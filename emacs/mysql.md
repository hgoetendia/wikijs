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
                  (sql-user "myotheruser")
                  (sql-password "userpassword")
                  (sql-database "mydatabase1")
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

Open a window and set `sql-mode` then `M-x mydatabaseconn` to load SQLi

# SQLi

Send selected query region to sql engine  `C-c C-r` 

![Sqli](/uploads/emacs/sqli.png "Sqli")

