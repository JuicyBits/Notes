**DOMContentLoaded**
- The `DOMContentLoaded` event is fired when the initial HTML document ha been completely loaded and parsed without waiting for stylesheets, images, and subframes to finish loading
```
document.addEventListener('DOMContentLoaded', function(e){
  console.log('DOM fully loaded and parsed');
})
```
