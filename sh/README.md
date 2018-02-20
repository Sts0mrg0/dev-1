[//]: # "#!/bin/sh"

# *Bash*
A list of useful scripts:  

* #### Pipe `cat` output to Clipboard (Linux):
  ```bash
  cat <FILE NAME> | xsel -ib
  ```

* #### SSH through Proxy:
  ```bash
  # ~/.ssh/config
  
  Host *
	    ProxyCommand  ncat --proxy-type {http|socks4|socks5} --proxy <PROXY IP>:<PROXY PORT> %h %p
  ```

* #### Convert FLAC audio files to MP3 with `ffmpeg`:
  ```bash
  ffmpeg -i <AUDIO FILE>.flac -sample_rate 44100 -ab 320k -q:a 0 <AUDIO FILE>.mp3
  ```
  
* #### Prompt new terminal in the same directory [`zsh`]:
  ```bash
  # ~/.zshrc
  
  precmd() {
    if [[ $PWD = $HOME ]]; then
        [[ -f "${HOME}/.last_pwd" ]] && cd "$(< ${HOME}/.last_pwd)"
    fi
  }
  
  chpwd() { eval "$PROMPT_COMMAND" }
  
  PROMPT_COMMAND='pwd > "${HOME}/.last_pwd"'
  ```
  
  
