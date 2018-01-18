[//]: # "#!/bin/sh"

# *Bash*
A list of useful scripts:  

* #### Pipe `cat` output to Clipboard (Linux):
  ```bash
  cat <FILE NAME> | xsel -ib
  ```

* #### Download all files from HTTP directory list:
  ```bash
  wget -r -np [-R index.html] [--no-check-certificate] <HOST>
  ```

* #### Convert FLAC audio files to MP3 with `ffmpeg`:
  ```bash
  ffmpeg -i <AUDIO FILE>.flac -sample_rate 44100 -ab 320k -q:a 0 <AUDIO FILE>.mp3
  ```
