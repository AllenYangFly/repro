```javascript
function mySetInterval(fn, millisec){
  function interval(){
    setTimeout(interval, millisec);
    fn();
  }

  setTimeout(interval, millisec)
}
```