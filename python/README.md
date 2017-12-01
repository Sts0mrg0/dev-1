# *Python*
A list of useful scripts:  

* #### Upgrade all package:
  ```bash
  pip freeze --local | grep -v '^\-e' | cut -d = -f 1 | xargs -n1 pip install -U
  ```
* #### Check if a class method is static (Python3):
  ```python
  class MyClass:
    def __init__(self):
      return
      
    @staticmethod
    def my_static_method(x):
      return x
      
  isinstance(MyClass.__dict__["my_static_method"], staticmethod)  # True
  ```
