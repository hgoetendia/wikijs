<!-- TITLE: Emacs -->


* [Basics](/emacs/basics)

# Emacs for C/C++
## TAB = 4 spaces.

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;Tabulacion 4 caracteres C;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(setq-default indent-tabs-mode nil)
(setq-default tab-width 4)
(setq c-basic-offset 4)
(setq c-default-style "bsd"
      c-basic-offset 4)

```

## Compile with F5


```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;Compilacion;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;compilar con f5
(global-set-key [f5] 'compile)
```

## Jump to the next compilation error

Using F6

```lisp
;Siguiente error de compilacion
(global-set-key [f6] 'next-error)
```

## Tunning compilation window


```lisp
(defun my-compilation-hook ()
  (when (not (get-buffer-window "*compilation*"))
    (save-selected-window
      (save-excursion
        (let* ((w (split-window-vertically))
               (h (window-height w)))
          (select-window w)
          (switch-to-buffer "*compilation*")
          (shrink-window (- h 10)))))))
(add-hook 'compilation-mode-hook 'my-compilation-hook)

;; auto scroll to the end 
(setq compilation-scroll-output 1)
(setq column-number-mode t)
```





