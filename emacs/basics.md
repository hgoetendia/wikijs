<!-- TITLE: Emacs/Basics -->

# Install
Default emacs package in Centos 7.5 is Emacs 24.3.1

```sh
sudo yum install -y emacs
```

If you prefer other versions you can install it from sources:

Example: Emacs 26.1

```sh
sudo yum -y install libXpm-devel libjpeg-turbo-devel openjpeg-devel openjpeg2-devel turbojpeg-devel giflib-devel libtiff-devel gnutls-devel libxml2-devel GConf2-devel dbus-devel wxGTK-devel gtk3-devel wget gcc ncurses-devel.x86_64
wget http://git.savannah.gnu.org/cgit/emacs.git/snapshot/emacs-26.1.tar.gz
tar zxvf emacs-26.1.tar.gz
cd emacs-26.1
./autogen.sh
./configure --without-makeinfo # incase makeinfo is not available on your system: Example Centos 7 else `./configure` would do
sudo make install
```

Check version


```sh
emacs --version
GNU Emacs 26.1
```




To start emacs
```sh
emacs
```

# .emacs file

Create startup configuration file `.emacs`


```lisp
emacs .emacs
```



![Filedotemacs](/uploads/emacs/filedotemacs.png "Filedotemacs")

# Inhibit initial splash screen


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;Inhibir splash screen;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq inhibit-splash-screen t)
```


# Repos

 Repo `gnu` and `melpa` to install emacs addons.
 

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;Paquetes para instalar;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(package-initialize)
(setq package-archives '(("gnu" . "https://elpa.gnu.org/packages/")
                         ("melpa" . "https://melpa.org/packages/")))

```

To show package list: `M-x package-list-packages`

![Packages](/uploads/emacs/packages.png "Packages")

## Install package

Example:

`M-x package-install`

`Install package: yasnippet`


# Backup folder
Set the backup folder to avoid them.


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;Para que todos los archivos backup residan en un solo sitio;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq backup-directory-alist `(("." . "~/")))

```

# Default directory

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;Directorio por defecto;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq default-directory "~/")

```

# Resize windows

With keys:

* F7 Enlarge window horizontally
* F8 Shrink window horizontally
* F9 Enlarge window vertically
* F10 Shrink window vertically

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;Resize de ventanas con las teclas F;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;; Use control-arrow keys for window resizing
(global-set-key [f7] 'enlarge-window-horizontally)
(global-set-key [f8] 'shrink-window-horizontally)
(global-set-key [f9] 'enlarge-window)
(global-set-key [f10] 'shrink-window)

```


# Switching between windows

Custom switching using:

* ESC left arrow
* ESC right arrow
* ESC up arrow
* ESC down arrow


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;Navegacion por ventanas con el cursor y escape;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(global-set-key (kbd "ESC <left>") 'windmove-left)          ; move to left window
(global-set-key (kbd "ESC <right>") 'windmove-right)        ; move to right window
(global-set-key (kbd "ESC <up>") 'windmove-up)              ; move to upper window
(global-set-key (kbd "ESC <down>") 'windmove-down)          ; move to lower window
```

# Match parentesis


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;Para ver los parentesis que corresponden;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(show-paren-mode t)
```

# Return to the previously edit position
When you visit a file, point goes to the last place where it was when you previously visited the same file.

For GNU Emacs 24.5 and older versions

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; A la hora de cargar te devuelva a la misma posicion donde estabas;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(require 'saveplace)
(setq-default save-place t)
```

For GNU Emacs 25.1 and newer versions
```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; A la hora de cargar te devuelva a la misma posicion donde estabas;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(save-place-mode 1) 
```


# Show column number

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;Para ver en que columna estas;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq column-number-mode t)
```


# Neotree (file manager)
F12 to toggle neotree window

![Installneotree](/uploads/emacs/installneotree.png "Installneotree")

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;NEOTREE directorios a la izquierda;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(require 'neotree)
  (global-set-key [f12] 'neotree-toggle)

```


![Neotree 2](/uploads/emacs/neotree-2.png "Neotree 2")


# Fix MacOSX meta key issue


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;Cambiamos la tecla meta alt a q no tenga funcion esto para MACOS;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq mac-option-modifier nil)

```

# Look and feel

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;Look And Feel ( Coloreado );;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(default ((t (:inherit nil :stipple nil :background "gray0" :foreground "green"
			 :inverse-video nil :box nil :strike-through nil
			 :overline nil :underline nil :slant normal
			 weight normal :width normal :family "monospace"))))
 '(background "black")
 '(font-lock-builtin-face ((((class color) (background dark))
			    (:foreground "Turquoise"))))
 '(font-lock-comment-face ((t (:foreground "red"))))
 '(font-lock-constant-face ((((class color) (background dark))
			     (:bold t :foreground "DarkOrchid"))))
 '(font-lock-doc-string-face ((t (:foreground "yellow"))))
 '(font-lock-function-name-face ((t (:foreground "green1"))))
 '(font-lock-keyword-face ((t (:foreground "DeepSkyBlue"))))
 '(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))))
 '(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
 '(font-lock-string-face ((t (:foreground "gold2")))))
```

## Mark selected text


```lisp
;;;;;;;;Para que aparezca coloreado cuando seleccionas un texto
(transient-mark-mode t)

```

## Comments in blue

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;Comentario en azul;
(set-face-foreground 'font-lock-comment-face "Red" )
(set-variable font-lock-comment-face 'font-lock-comment-face)
```


## Window margin
```lisp
;;;;;;;;;;;;;;;;;;;;;;;;Left/Right window margin;;;;;;;;;;;
 (setq-default left-margin-width 1 right-margin-width 1) ; Define new widths.
 (set-window-buffer nil (current-buffer)) ;; Use them now.
```


## Line numbers 


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;Line numbers in code        ;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;(global-linum-mode 1)
(add-hook 'prog-mode-hook 'linum-mode)
;(setq linum-format "%4d \u2502 ") ;With vertical bar
(setq linum-format "%d ")
```

## Winner Mode                                                                                                                                                                      

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;; Winner mode : Undo window operations;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(winner-mode 1)
```



## Extras

When press key 'End' and shows get an error `<select> is undefined`

```lisp
;; PuTTY fix. Ugly. Bad. But it works. (Good)
;; Even when TERM=xterm-256color on bash and
;; ~/.tmux.conf says:
;;   set-window-option -g xterm-keys on
;;   set -g default-terminal "xterm-256color"
;; still, pressing <end> key results in error:
;;   <select> is undefined
;; This hack fixes the end key. Home key already
;; worked on Linux/tmux (don't know about putty)
;;
(define-key global-map "\M-[1~" 'beginning-of-line)
(define-key global-map [select] 'end-of-line)

```


# All together


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;Inhibir splash screen;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq inhibit-splash-screen t)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;Para que todos los archivos backup residan en un solo sitio;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq backup-directory-alist `(("." . "~/.emacs.d/backup")))

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;Paquetes para instalar;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(package-initialize)
(setq package-archives '(("gnu" . "https://elpa.gnu.org/packages/")
                         ("melpa" . "https://melpa.org/packages/")))


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;Resize de ventanas con las teclas F;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;; Use control-arrow keys for window resizing
(global-set-key [f7] 'enlarge-window-horizontally)
(global-set-key [f8] 'shrink-window-horizontally)
(global-set-key [f9] 'enlarge-window)
(global-set-key [f10] 'shrink-window)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;Navegacion por ventanas con el cursor y escape;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(global-set-key (kbd "ESC <left>") 'windmove-left)        ; move to left window
(global-set-key (kbd "ESC <right>") 'windmove-right)      ; move to right window
(global-set-key (kbd "ESC <up>") 'windmove-up)            ; move to upper window
(global-set-key (kbd "ESC <down>") 'windmove-down)        ; move to lower window

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;; A la hora de cargar te devuelva a la misma posicion donde estabas;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(require 'saveplace)
(save-place-mode 1) 


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;Para ver los parentesis que corresponden;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(show-paren-mode t)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;Para ver en que columna estas;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq column-number-mode t)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;NEOTREE F12 y directorios a la izquierda;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(require 'neotree)
  (global-set-key [f12] 'neotree-toggle)
	
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;Cambiamos la tecla meta alt a q no tenga funcion esto para MACOS;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq mac-option-modifier nil)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;Look And Feel ( Coloreado );;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(default ((t (:inherit nil :stipple nil :background "gray0" :foreground "green"
			 :inverse-video nil :box nil :strike-through nil
			 :overline nil :underline nil :slant normal
			 weight normal :width normal :family "monospace"))))
 '(background "black")
 '(font-lock-builtin-face ((((class color) (background dark))
			    (:foreground "Turquoise"))))
 '(font-lock-comment-face ((t (:foreground "red"))))
 '(font-lock-constant-face ((((class color) (background dark))
			     (:bold t :foreground "DarkOrchid"))))
 '(font-lock-doc-string-face ((t (:foreground "yellow"))))
 '(font-lock-function-name-face ((t (:foreground "green1"))))
 '(font-lock-keyword-face ((t (:foreground "DeepSkyBlue"))))
 '(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))))
 '(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
 '(font-lock-string-face ((t (:foreground "gold2")))))

;;;;;;;;Para que aparezca coloreado cuando seleccionas un texto
(transient-mark-mode t)
;;;;;;;;;;;;;;;;;;;;;;;;Comentario en azul;
(set-face-foreground 'font-lock-comment-face "Red" )
(set-variable font-lock-comment-face 'font-lock-comment-face)

;;;;;;;;;;;;;;;;;;;;;;;;Left/Right window margin;;;;;;;;;;;
 (setq-default left-margin-width 1 right-margin-width 1) ; Define new widths.
 (set-window-buffer nil (current-buffer)) ;; Use them now.

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;Line numbers in code        ;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;(global-linum-mode 1)
(add-hook 'prog-mode-hook 'linum-mode)
;(setq linum-format "%4d \u2502 ") ;With vertical bar
(setq linum-format "%d ")

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;; Winner mode : Undo window operations;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(winner-mode 1)


;; PuTTY fix. Ugly. Bad. But it works. (Good)
;; Even when TERM=xterm-256color on bash and
;; ~/.tmux.conf says:
;;   set-window-option -g xterm-keys on
;;   set -g default-terminal "xterm-256color"
;; still, pressing <end> key results in error:
;;   <select> is undefined
;; This hack fixes the end key. Home key already
;; worked on Linux/tmux (don't know about putty)
;;
(define-key global-map "\M-[1~" 'beginning-of-line)
(define-key global-map [select] 'end-of-line)

```




