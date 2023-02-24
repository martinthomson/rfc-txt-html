# Make an HTML RFC look just like a text RFC

IETF RFCs are now being rendered into HTML.  This is good.  HTML is great.

For years, we have relied on "htmlized" versions of RFCs that are text files
with links added.  This works by running a bunch of regular expressions over the
text to recognize links.  This is crazy.  We already have those links in the
HTML source.

The HTMLizing code is starting to fall behind.  It won't render new RFCs with
links in the table of contents because it doesn't recognize a table of contents
without page numbers.

The core realization here is that a stylesheet is all it needs to render the
HTML file in a way that is nearly identical to the text file.  This repository
does just that.

## Demo

Try a side-by-side comparison of [RFC
9000](https://martinthomson.github.io/rfc-txt-html/diff.html).

## Usage

Use this with [xml2rfc](https://pypi.org/project/xml2rfc/) with the `--css`
flag:

```
xml2rfc --css=../path/to/txt.css --html draft-foo.xml
```

## Variances from Text Format

This isn't perfect, but it's close.  Known differences:

* The stylesheet is incomplete (not great).

* Table borders are rendered with lines, not ASCII art (arguably better).

* Pilcrows are rendered (useful).

* Sentences do not end with double-spacing (probably neutral), so paragraph
  breaks aren't 100% identical.

* Centred items are properly centred, not quantized (whatever).

* Ordered lists with ten or more items don't render identically (maybe consider
  using fewer items in your lists).

* All headings are bold, even non-numbered ones (¯\\_(ツ)_/¯).

* Anchors for section numbers aren't highlighted as links (no problem).

* The document publication date isn't in the same place in the document header
  (annoying, but not fatal).

* Line heights aren't absolutely precise (due to browser variations).

* Some links are rendered differently (annotations in the HTML could be more
  consistent).

* All links are links (clear win).

* Superscripts and subscripts are rendered as superscripts and subscripts
  (harder to fix than it seems).

## User Style

This is available as a user style.  It is incompatible with [this user
style](https://github.com/martinthomson/rfc-css).

To install this, you need a userstyle extension for your browser:

🎨 Stylus for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/), [Chrome](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne) or [Opera](https://addons.opera.com/en-gb/extensions/details/stylus/).<br>
🎨 xStyle for [Firefox](https://addons.mozilla.org/firefox/addon/xstyle/) or [Chrome](https://chrome.google.com/webstore/detail/xstyle/hncgkmhphmncjohllpoleelnibpmccpj).<br>
🎨 [Stylish](https://userstyles.org).

📦 [Install the usercss](https://martinthomson.github.io/rfc-txt-html/txt.user.css).
