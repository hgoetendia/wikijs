<!-- TITLE: Reactjs -->
<!-- SUBTITLE: A quick summary of Reactjs -->

# RJSX mode
Install rjsx-mode, it needs Emacs 24.4 or greater.

It is for sintax higlighting and identation.


# Load .js files in rjsx-mode

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; Cargar archivos .js en rjsx-mode
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(add-to-list 'auto-mode-alist '("\\.js$" . rjsx-mode))
```

# Identation 2 spaces


```lisp
(add-hook 'rjsx-mode-hook
          (lambda ()
            (setq indent-tabs-mode nil) ;;Use space instead of tab
            (setq js-indent-level 2) ;;space width is 2 (default is 4)
            (setq js2-strict-missing-semi-warning nil))) ;;disable the semicolon warning
```


