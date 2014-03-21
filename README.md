![](https://f.cloud.github.com/assets/671378/2454103/24d89962-aee6-11e3-9dcf-ee2d81ec0373.jpg)

Reads in code, writes out HTML with CSS classes based on the tokens in the code.

[![Build Status](https://travis-ci.org/atom/highlights.png)](https://travis-ci.org/atom/highlights)

See it in action [here](http://atom.github.io/highlights/examples).

### Installing

```sh
npm install highlights
```

### Using

To convert a source file to tokenized HTML run the following:

```sh
highlights file.coffee -o file.html
```

Now you have a `file.html` file that has a big `<pre>` tag with a `<div>` for
each line with `<span>` elements for each token.

Then you can compile an existing Atom theme into a stylesheet with the
following:

```sh
git clone https://github.com/atom/atom-dark-syntax
cd atom-dark-syntax
npm install -g less
lessc --include-path=stylesheets index.less atom-dark-syntax.css
```

Now you have an `atom-dark-syntax.css` stylesheet that be combined with
the `file.html` file to generate some nice looking code.

Check out the [examples](http://atom.github.io/highlights/examples) to see
it in action.

Check out [atom.io](https://atom.io/packages) to find more themes.

Run `highlights -h` for full details about the supported options.

#### Using in code

```coffee
Highlights = require 'highlights'
highlighter = new Highlights()
html = highlighter.highlightSync
  fileContents: 'var hello = "world";'
  scopeName: 'source.js'

console.log html
```

Outputs:

```html
<pre class="editor editor-colors"><div class="line"><span class="source js"><span class="storage modifier js"><span>var</span></span><span>&nbsp;hello&nbsp;</span><span class="keyword operator js"><span>=</span></span><span>&nbsp;</span><span class="string quoted double js"><span class="punctuation definition string begin js"><span>&quot;</span></span><span>world</span><span class="punctuation definition string end js"><span>&quot;</span></span></span><span class="punctuation terminator statement js"><span>;</span></span></span></div></pre>
```

### Developing

* Clone this repository `git clone https://github.com/atom/highlights`
* Run `npm install` to install the dependencies, compile the CoffeeScript, and
  build the grammars.
* Run `npm test` to run the specs

:green_heart: Pull requests are greatly appreciated and welcomed.
