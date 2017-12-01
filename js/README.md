# *JavaScript*
A list of useful scripts:

* #### Modulo operator:
  ```javascript
  const mod = (x, base) => {
    return ((x % base) + base) % base
  };

  13 % 12  // 1 (using the *remainder* operator)
  mod(13, 12)  // 1
  
  // So why you should use the *modulo* operator?
  -1 % 12  // -1
  mod(-1, 12)  // 11
  ```
  
* #### ~Pseudo~ Random number within a specific range:
  ```javascript
  const randomFromRange = (min, max) => {
    return Math.random() * (max - min) + min
  };
  
  randomFromRange(1, 10)  // 7.1392...
  randomFromRange(1, 10)  // 1.8713...
  randomFromRange(1, 10)  // 4.4522...
  
  // TODO: window.crypto.getRandomValues(new Uint8Array(1))
  ```

* #### HTML *escape* function:
  ```javascript
  const charEscape = {
        '"': '&quot;', '&': '&amp;', "'": '&#39;',
        '/': '&#47;', '<': '&lt;', '>': '&gt;'
    },
    
    escapeHtml = (text) => {
        if ( !text || !text.length ) { return "" }
        if ( !( text instanceof String ) ) { text = text.toString() }
        return text.replace(/["&'\/<>]/g, (c) => {
            return charEscape[c]
        })
    };
    
  escapeHtml(`"><script>`)  // &quot;&gt;&lt;script&gt;
  ```
  
* #### Utils for working with circle (hoping you'll never have to):
  ```javascript
  const degreesToRadians = (degrees) => {
          return degrees * ( Math.PI / 180 )
      },

      radiansToDegrees = (radians) => {
          return radians * ( 180 / Math.PI );
      },

      coordinatesToRadians = (x, y, cx, cy) => {
          // where: x & y = point coords
          //        cx & cy = center coords
          return Math.atan2(y - cy, x - cx)
      },

      isInsideCircle = (x, y, cx, cy, r) => {
          // where: x & y = point coords
          //        cx & cy = center coords
          //        r = radius
          return Math.sqrt(Math.pow(x - cx, 2) + Math.pow(y - cy, 2)) < r
      };
  ```
