<!-- TITLE: Snippets -->

# Yasnippet

Autocomplete structures with custom data

## Installation

In emacs command line:

`M-x package-install`
`Install package: yasnippet`

In bash:

`mkdir -p ~/.emacs.d/snippets`

Add this to `~/.emacs` configfile

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;Yasnippet;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(add-to-list 'load-path
              "~/.emacs.d/snippets")
(require 'yasnippet)
(yas-global-mode 1)
```

## Creating snippets

`M-x yas-new-snippet` or `C-c & C-n`


This will load a file with this structure to fill

```text
# -*- mode: snippet -*-
# name: 
# key: 
# --
```

Example


```text
# -*- mode: rjsx-mode -*-
# name: console.log
# key: conlo
# --
console.log("$0");
```

Save the file in a directory according to mode

For example in `.emacs.d/snippets/rjsx-mode/consolelog.txt`

When you need to use them in the right mode start typing conlog then press TAB key for complete:

`conlo<TAB>`



