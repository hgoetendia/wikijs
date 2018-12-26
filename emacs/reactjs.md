<!-- TITLE: Reactjs -->
<!-- SUBTITLE: A quick summary of Reactjs -->

# RJSX mode and Tide
* Install rjsx-mode package it needs Emacs 24.4 or greater, It is for sintax higlighting and identation.
* Install tide package, you will need install [Nodejs](/javascript/nodejs).
* Install company package.

## Load .js files in rjsx-mode


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; Cargar archivos .js en rjsx-mode
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(add-to-list 'auto-mode-alist '("\\.js$" . rjsx-mode))
```

## Load .tsx files in rjsx-mode

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; Cargar archivos .tsx en rjsx-mode
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(add-to-list 'auto-mode-alist '("\\.tsx\\'" . rjsx-mode))
```


## Identation and setup-tide-mode

Replace tab for 2 spaces identation in `rjsx-mode`


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;                                                                                                                                                                               
;; Replace tab for 2 spaces identation in rjsx-mode                                                                                                                                                            
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;                                                                                                                                                                               

(add-hook 'rjsx-mode-hook
          (lambda ()
            (setq indent-tabs-mode nil) ;;Use space instead of tab                                                                                                                                             
            (setq js-indent-level 2) ;;space width is 2 (default is 4)                                                                                                                                         
            (setq js2-strict-missing-semi-warning nil) ;;disable the semicolon warning                                                                                                                         
            (when (string-equal "js" (file-name-extension buffer-file-name))
              (setup-tide-mode)) ;; Setup tide before js
          ))
						
```

## jsconfig.json files

The file jsconfig.json must exist in your project folder, this is a sample:


```json
{
  "compilerOptions": {
    "target": "es2017",
    "allowSyntheticDefaultImports": true,
    "noEmit": true,
    "checkJs": true,
    "jsx": "react",
    "lib": [ "dom", "es2017" ]
  }
}
```




