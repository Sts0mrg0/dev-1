[//]: # "#!/bin/sh"

# *Bash*
A list of useful scripts:  

* #### Convert FLAC audio files to MP3 with `ffmpeg`:
  ```bash
  ffmpeg -i <AUDIO FILE>.flac -sample_rate 44100 -ab 320k -q:a 0 <AUDIO FILE>.mp3
  ```
  
