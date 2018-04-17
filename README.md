# Slack Night Mode
A Stylish style for easy Slack theming. [CC0](http://creativecommons.org/publicdomain/zero/1.0/).

## Usage

This theme requires that you use the Stylish extension for your browser (available for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/stylish/), [Chrome](https://chrome.google.com/webstore/detail/stylish/fjnbnpbmkenffdnngjfgmeleoegfcffe), and [Safari](http://sobolev.us/stylish/)).

Unfortunately, if you're using the desktop version of Slack, you will not** be able to use this theme (as explained on [my blog post](http://blog.lacour.me/making-slack-night-mode#toc_1)).

** However you can still use this theme using this little hack: https://github.com/laCour/slack-night-mode/issues/73#issuecomment-242707078

#### Instructions for macOS
- Open `/Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js`
- Add this snippet to the bottom of that file
- Replace `/absolute/path/to` with path to your `black.css`
- You will have to re-add this everytime Slack update itself.
```js
document.addEventListener('DOMContentLoaded', function() {
  var fs = require('fs'),
  filePath = '/absolute/path/to/black.css';

  fs.readFile(filePath, {encoding: 'utf-8'}, function(err, data) {
    if (err) {
        console.log(err);
        return
    }
      var css = document.createElement('style');
      css.type = "text/css";
      if (css.styleSheet){
        css.styleSheet.cssText = data;
      } else {
        css.appendChild(document.createTextNode(data));
      }
      document.getElementsByTagName('head')[0].appendChild(css);
  })
});
```

## Themes

### Supported

#### Black ([source](scss/main.scss) - [build](css/black.css) - [install](https://userstyles.org/styles/117475/slack-night-mode-black))

The primary supported theme. This is an excellent theme if you use a program like f.lux or redshift.

![Black Screenshot](https://userstyles.org/style_screenshots/117475_after.png)

#### Aubergine ([source](scss/themes/_aubergine.scss) - [build](css/variants/aubergine.css) - [install](https://userstyles.org/styles/101971/slack-night-mode))

This is based on Slack's aubergine/maroon style. It's the original theme.

![Aubergine Screenshot](https://userstyles.org/style_screenshots/101971_after.png)

### Variants

* **Arc ([source](scss/themes/_arc-dark.scss) - [build](css/variants/arc-dark.css))** _by [@Lemmmy](https://github.com/Lemmmy)_
* **Midnight Blue ([source](scss/themes/_midnight-blue.scss) - [build](css/variants/midnight-blue.css))** _by [@matt-h](https://github.com/matt-h)_
* **Tomorrow Dark (base16) ([repository](https://github.com/danarnold/slack-night-mode))** _by [@danarnold](https://github.com/danarnold)_

### Extensions

Variants can have extensions which add additional changes.

#### Monospaced ([source](scss/themes/_monospaced.scss))

Replaces the messaging font stack with a monospace font stack.
