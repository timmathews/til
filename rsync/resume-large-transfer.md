# Resume A Large SCP Transfer
> https://yyab.wordpress.com/2006/12/18/resume-a-large-scp-transfer/

Use `rsync`. Which might have been a better choice to begin with.

```
$ rsync --partial --progress --rsh=ssh user@host:remote_file local_file
```

Instead of `--partial --progress`, you can also use the the `-P` flag which
combines the two.

`--partial` tells rsync to keep partial files.

`--progress` displays a progress bar.

`--rsh=ssh` tunnels the transfer over SSH. `-e` also works. If SSH is on a
non-standard port, `-e 'ssh -p 2222'` is the way to go.
