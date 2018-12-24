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

![Emacs](/uploads/emacs/emacs.png "Emacs")

# Repos

 Repo gnu and melpa to install emacs addons.
 

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;Paquetes para instalar;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(package-initialize)
(setq package-archives '(("gnu" . "https://elpa.gnu.org/packages/")
                         ("melpa" . "https://melpa.org/packages/")))

```

# Backup folder
Set the backup folder to avoid that files anywhere.


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;Para que todos los archivos backup residan en un solo sitio;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq backup-directory-alist `(("." . "~/")))

```


