<!-- TITLE: Reactjs -->
<!-- SUBTITLE: A quick summary of Reactjs -->

# RJSX mode and Tide
* Install rjsx-mode package it needs Emacs 24.4 or greater, It is for sintax higlighting and identation.
* Install tide package, you will need install [Nodejs](/javascript/nodejs).
* Install company package.
* Install use-package package.

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


## Setup tide-mode and rjsx-mode


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;                                                                                                                                                                               
;; Setup-tide-mode                                                                                                                                                           
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;                                                                                                                                                                               
(defun setup-tide-mode ()
  (interactive)
  (tide-setup)
  (flycheck-mode +1)
  (setq flycheck-check-syntax-automatically '(save mode-enabled))
  (eldoc-mode +1)
  (tide-hl-identifier-mode +1)
  ;; company is an optional dependency. You have to
  ;; install it separately via package-install
  ;; `M-x package-install [ret] company`
  (company-mode +1))

;; aligns annotation to the right hand side
(setq company-tooltip-align-annotations t)

;; formats the buffer before saving
(add-hook 'before-save-hook 'tide-format-before-save)

(add-hook 'typescript-mode-hook #'setup-tide-mode)
```


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;                                                                                                                                                                               
;; Replace tab for 2 spaces identation in rjsx-mode, and invoke setup-tide-mode                                                                                                                                                            
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;                                                                                                                                                                               

(add-hook 'rjsx-mode-hook
          (lambda ()
            (setq indent-tabs-mode nil) ;;Use space instead of tab                                                                                                                                             
            (setq js-indent-level 2) ;;space width is 2 (default is 4)                                                                                                                                         
            (setq js2-strict-missing-semi-warning nil) ;;disable the semicolon warning                                                                                                                         
            (when (string-equal "js" (file-name-extension buffer-file-name))
              (setup-tide-mode)) ;; call setup-tide-mode 
          ))
						
```

use-package

```lisp

(use-package tide
  :ensure t
  :after (typescript-mode company flycheck)
  :hook ((typescript-mode . tide-setup)
         (typescript-mode . tide-hl-identifier-mode)
         (before-save . tide-format-before-save)))
```


## jsconfig.json file

The file <a href="/uploads/reactjs/jsconfig.json" download>jsconfig.json</a> must exist in your project folder, this is a sample:


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




