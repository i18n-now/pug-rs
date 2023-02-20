# pug-rs

![crates.io](https://img.shields.io/crates/v/pug?style=for-the-badge)

A port of [pug](https://pugjs.org) to Rust.

This is a maintained fork of the [original code by
github.com/aep](https://github.com/aep/pug-rs).

## CLI usage

```
$ cargo install pug
$ pug < thing.pug > thing.html
```


## Using with webpack

pug_loader.js:
```javascript
const spawnSync = require('child_process').spawnSync;
module.exports = function(source) {
  var proc = spawnSync("pug", {
    input: source
  });
  if (proc.status != 0) {
    throw proc.error;
  }
  return proc.stdout.toString();
}
```

webpack.config.js
```javascript
  module: {
    rules: [
      {
        test: /\.pug$/,
        use: [require.resolve('./pug_loader.js')]
      },

```

