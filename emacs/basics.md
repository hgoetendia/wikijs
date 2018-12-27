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


