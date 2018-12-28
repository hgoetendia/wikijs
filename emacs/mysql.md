<!-- TITLE: Emacs / Mysql -->
<!-- SUBTITLE: A quick summary of Mysql -->

# sql-mysql
Execute `M-x sql-mysql` for interactive mode.


# Automating database connection

```lisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;MYSQL;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(add-hook 'sql-interactive-mode-hook
          (lambda ()
            (toggle-truncate-lines t)))  ; for a good query output

(setq sql-mysql-options '("-C" "-f" "-t" "-n" "-A")) ; for windows and for -A flag

(setq sql-connection-alist
      '((mydatabaseconn (sql-product 'mysql)
                  (sql-port 3306)
                  (sql-server "myserver.com")
                  (sql-user "foouser")
                  (sql-password "mysecretpass")
		              (sql-database "mydatabase")
                 )
			(myotherdatabaseconn (sql-product 'mysql)
                  (sql-port 18086)
                  (sql-server "localhost")
                  (sql-user "admtiaxa")
                  (sql-password "tiaxa")
                )
        ))

(defun mydatabaseconn ()
  (interactive)
  (my-sql-connect 'mysql 'mydatabaseconn))
	
(defun myotherdatabaseconn ()
  (interactive)
  (my-sql-connect 'mysql 'myotherdatabaseconn))

(defun my-sql-connect (product connection)
  ;; remember to set the sql-product, otherwise, it will fail for the first time
  ;; you call the function
  (setq sql-product product)
  (sql-connect connection))
```

Then

`M-x mydatabaseconn`

# SQLi

Send selected query region to sql engine  `C-c C-r` 

