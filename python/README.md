# *Python*
A list of useful scripts:  

* #### Upgrade all package:
  ```bash
  pip freeze --local | grep -v '^\-e' | cut -d = -f 1 | xargs -n1 pip install -U
  ```