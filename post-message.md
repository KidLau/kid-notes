# postMessage

HTML5 API postMessage doesn't work in some versions of IE cross-origin between two windows, use below way can make it works in IE10+. 

```js
// previous
const url = 'https://www.google.com'
const win = window.open(url, 'New Window Name')
```

```js
// now
const url = 'https://www.google.com'
const win = window.open('/', 'New Window Name')
win.location.href = url
```

For IE compatibility, use event listener like below

```js
const eventer = window.addEventListener ? 'addEventListener' : 'attachEvent'
const event = eventer === 'attachEvent' ? 'onmessage' : 'message'
window[eventer](event, e => {
  console.log(e.data)
}, false)
```