# *Raspberry*  
A list of useful scripts:

* #### Routing all WiFi traffic from `wlan` to `eth`:
  ```
                         192.168.1.1
      +----------+       +---------+    eth0    +-------------+
      | Internet | ===== |  Modem  | ========== |  Raspberry  |
      +----------+       +---------+            +-------------+
                                                       |       
      # Raspberry:                                     |  wlan0
        - eth0:                                        |
               192.168.1.10/24                    +---------+               +--------------+
               gw 192.168.1.1                     | WiFi AC | ------------- | Workstations |
                                                  +---------+               +--------------+
        - wlan0:                                  192.168.2.1
               192.168.2.20/24
               gw 192.168.2.10
               dhcp 192.168.2.1
  ```  
  
  ```bash
  # /etc/network/interfaces
  
  ...
  
  auto eth0
  iface eth0 inet dhcp
  
  allow-hotplug wlan0
  iface wlan0 inet dhcp
      wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
      post-up /usr/local/sbin/wifi-forwarding
  ```
  
  ```bash
  # /etc/wpa_supplicant/wpa_supplicant.conf
  
  ...
  
  network={
        ssid="WIFISSID"
        key_mgmt=WPA-PSK
        psk="WIFIPASSWD"
  }
  ```  
  
  ```bash
  # /usr/local/sbin/wifi-forwarding
  
  #!/bin/sh
  
  iptables -F INPUT
  iptables -F OUTPUT
  iptables -F FORWARD

  iptables -t nat -P PREROUTING ACCEPT
  iptables -t nat -P POSTROUTING ACCEPT
  iptables -t nat -P OUTPUT ACCEPT

  iptables -A FORWARD -p ALL --in-interface wlan0 -j ACCEPT
  iptables -A FORWARD -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

  iptables -t nat -A POSTROUTING --out-interface eth0 -j MASQUERADE

  route del default
  route add default gw 192.168.1.1
  ```  
  
  ```bash
  # /etc/sysctl.conf
  
  ...
  
  # Uncomment the next line to enable packet forwarding for IPv4
  net.ipv4.ip_forward=1
  ```
  
  
