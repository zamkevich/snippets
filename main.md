## Resize observer
Old style RO hack 

```
resizeObserver(node, function(){
  console.log(this.offsetWidth + ' x ' + this.offsetHeight)
});


function resizeObserver(node, handler){
  let frame = document.createElement('iframe');
    frame.style.cssText = `
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
      border: 0;
      opacity: 0;
      pointer-events: none;
      z-index: -1;`;
    node.parentNode.appendChild(frame)
    frame.contentWindow.onresize = () => { handler.call(node.parentNode) };
}
```
