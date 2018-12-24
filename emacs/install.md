<!-- TITLE: Install -->
<!-- SUBTITLE: A quick summary of Install -->

# Install

```sh
sudo yum install -y emacs
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
# Backup folder
Set the backup folder to avoid them.


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;Para que todos los archivos backup residan en un solo sitio;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq backup-directory-alist `(("." . "~/")))

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



