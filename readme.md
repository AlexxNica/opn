# opn

> A better [node-open](https://github.com/pwnall/node-open). Opens stuff like websites, files, executables. Cross-platform.


#### Why?

- Actively maintained
- Supports app arguments
- Safer as it uses `spawn` instead of `exec`
- Fixes most of the open `node-open` issues
- Comes with a CLI for use in your scripts
- Includes the latest [`xdg-open` script](http://portland.freedesktop.org/download/) for Linux


## Install

```
$ npm install --save opn
```


## Usage

```js
var opn = require('opn');

opn('unicorn.png');
// opens the image in the default image viewer

opn('http://sindresorhus.com');
// opens the url in the default browser

opn('http://sindresorhus.com', 'firefox');
// specify the app to open in

opn('http://sindresorhus.com', ['google chrome', '--incognito']);
// specify app arguments
```


## API

Uses the command `open` on OS X, `start` on Windows and `xdg-open` on other platforms.

### opn(target, [app], [callback])

#### target

*Required*
Type: `string`

The thing you want to open. Can be a URL, file, or executable.

Opens in the default app for the file type. Eg. URLs opens in your default browser.

#### app

Type: `string`, `array`

Specify the app to open the `target` with, or an array with the app and app arguments.

The app name is platform dependent. Don't hard code it in reusable modules. Eg. Chrome is `google chrome` on OS X, `google-chrome` on Linux and `chrome` on Windows.

#### callback(error)

Type: `function`

Called when the opened app exits.

On Windows you have to explicitly specify an app for it to be able to wait.


## CLI

```
$ npm install --global opn
```

```
$ opn --help

  Usage
    $ opn <file|url> [app] [app arguments]

  Example
    $ opn http://sindresorhus.com
    $ opn http://sindresorhus.com firefox
    $ opn http://sindresorhus.com 'google chrome' --incognito
    $ opn unicorn.png
```


## License

MIT © [Sindre Sorhus](http://sindresorhus.com)
