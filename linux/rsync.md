<!-- TITLE: Rsync -->
<!-- SUBTITLE: A quick summary of Rsync -->

# Copy incremental files of folder

```text
-z, --compress
              With this option, rsync compresses the file data as it is sent to the destination machine, which reduces the amount of
              data being transmitted -- something that is useful over a slow connection.
-a, --archive
              This  is equivalent to -rlptgoD. It is a quick way of saying you want recursion and want to preserve almost everything (with -H being a notable omission).  The only exception to the above equivalence is when --files-from is specified, in which case -r
              is not implied.

              Note that -a does not preserve hardlinks, because finding multiply-linked files is expensive.  You must separately specify -H.
-r, --recursive
              This tells rsync to copy directories recursively.  See also --dirs (-d).

              Beginning with rsync 3.0.0, the recursive algorithm used is now an incremental scan that uses much less memory than before and begins the transfer after the scanning of the first few directories have been completed.  This incremental scan only affects
              our recursion algorithm, and does not change a non-recursive transfer.  It is also only possible when both ends of the transfer are at least version 3.0.0.

              Some  options  require  rsync to know the full file list, so these options disable the incremental recursion mode.  These include: --delete-before, --delete-after, --prune-empty-dirs, and --delay-updates.  Because of this, the default delete mode when
              you specify --delete is now --delete-during when both ends of the connection are at least 3.0.0 (use --del or --delete-during to request this improved deletion mode explicitly).  See also the --delete-delay option that is a better  choice  than  using
              --delete-after.

              Incremental recursion can be disabled using the --no-inc-recursive option or its shorter --no-i-r alias.
							
-h, --human-readable        output numbers in a human-readable format

-v, --verbose               increase verbosity


```

Command


```sh
rsync -zarvh /home/myuser/folderoriginal/ root@192.168.1.10:/home/otheruser/folderdestino/
```


