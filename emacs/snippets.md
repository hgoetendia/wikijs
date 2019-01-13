<!-- TITLE: Snippets -->

# Yasnippet

Autocomplete structures with custom data

In emacs command line:

`M-x package-install`
`Install package: yasnippet`

In bash:

`mkdir -p~/.emacs.d/plugins/snippets`

Add this to `~/.emacs` configfile

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;Yasnippet;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(add-to-list 'load-path
              "~/.emacs.d/plugins/snippets")
(require 'yasnippet)
(yas-global-mode 1)
```
