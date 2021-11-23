# Record

This extension lets you use Mousetrap to record keyboard sequences and play them back.

This is a node module (works in node/electron or with something like browserify). For original plugin see [this repo](https://github.com/ccampbell/mousetrap/tree/master/plugins/record)

## Installation

```bash
npm install mousetrap-record --save
```

Note that you also need the core `mousetrap` module (`npm install mousetrap --save`).

## Usage

```javascript
var Mousetrap = require('mousetrap-record')(require('mousetrap'));
```

```html
<button onclick="recordSequence()">Record</button>

<script>
    function recordSequence() {
        Mousetrap.record(function(sequence) {
            // sequence is an array like ['ctrl+k', 'c']
            console.log('You pressed: ' + sequence.join(' '));
        });
    }
</script>
```

If necessary, it's possible to change the default record timeout of 1000ms:

```js
// at initialize
var Mousetrap = require('mousetrap-record')(require('mousetrap'), { timeout: 250 });

// or at record call
Mousetrap.record(function(sequence) {
    console.log('You pressed: ' + sequence.join(' '));
}, 3000);
```

You can also disable default browser behaviour while recording:

```js
// at initialize
var Mousetrap = require('mousetrap-record')(require('mousetrap'), { timeout: 250, preventDefault: true, noRepeat: true });

// or at record call
Mousetrap.record(
    function(sequence) {
        console.log('You pressed: ' + sequence.join(' '));
    },
    3000,
    null,
    true,
    function(sequence) {
        console.log('You pressed (in progress): ' + sequence.join(' '));
    },
);
```
