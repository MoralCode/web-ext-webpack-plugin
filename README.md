# web-ext-plugin

A webpack plugin for running web-ext

## Basic usage

```bash
$ npm install --save-dev web-ext-plugin

# Or for yarn
$ yarn add -D web-ext-plugin
```

**webpack.config.js**

```js
const WebExtPlugin = require('web-ext-plugin');

module.exports = {
  plugins: [new WebExtPlugin({ sourceDir: 'extension-dist' })],
};
```

## Options

- `artifactsDir` (optional) - The folder where artifacts are built stored.
  Defaults to `<sourceDir>/web-ext-artifacts`.
  You typically won't need to alter this.

- `browserConsole` (optional) - A boolean indicating if the browser console
  should be shown on load.
  
  Defaults to false.

- `firefox` (optional) - A path to a specific version of Firefox to run.
  The value is an absolute path to the Firefox executable or an alias string.

- `firefoxProfile` (optional) - A specific Firefox profile to use.
  This may be either a profile name or the path to a profile directory.
  If this is not set a new profile is generated each time.
  
- `keepProfileChanges` (optional) - A boolean value indicating if the profile
  specified by `firefoxProfile`.

  Defaults to false.

  See the notes for the [`--keep-profile-changes` flag](https://extensionworkshop.com/documentation/develop/web-ext-command-reference/#web-ext-run) from the `web-ext run` documentation.
  Specifically, this should not be used together with a profile you later use for browsing.
  It is, however, useful if you want to force the profile in a specific location to be written to (e.g. for testing out-of-disk space situations).

- `profileCreateIfMissing` (optional) - A boolean value indicating if the
  profile specified by `firefoxProfile` should be created if it does not
  exist.

  Note that if this is specified, `firefoxProfile` is treated as meaning a directory path (not a profile name).

  Defaults to false.
  
- `sourceDir` (optional) - The folder where webpack is building your extension
  to.
  Typically this will be where you have configured `output.path` to point to.
  Relative paths will be resolved relative to the `webpack.config.js` file.
  
  Defaults to the same folder as the `webpack.config.js` file.  

- `startUrl` (optional) - A URL to load on startup.

- `target` (optional) - One of `firefox-desktop`, `firefox-android`, or `chromium`.

  Defaults to `firefox-desktop`.

  See the documentation for the `--target` option of [`web-ext run`](https://extensionworkshop.com/documentation/develop/web-ext-command-reference/#web-ext-run).
