# How to fix BIND's journal out of sync error
> by [The Dumb Terminal]
> (http://www.thedumbterminal.co.uk/posts/2013/02/how_to_fix_binds_journal_out_of_sync_error.html)

Assumning you have a DHCP server updating your DNS, which is pretty typical
(and how my network is configured), manually editing the zone files will cause
the following error:

```
zone example.com/IN: journal rollforward failed: journal out of sync with zone
zone example.com/IN: not loaded due to errors.
```

You can see this by querying the status of named:

```
systemctl status bind9.service
   - or -
named -g
```

To resolve this stop BIND, then remove the journal file for problem zone, these
exist in the same directory as the zone files but end in ".jnl". Once the file
has been deleted BIND can be restarted and all will be back to normal.

With dynamic zones, you need to `freeze` them first before editing and `thaw`
them after to avoid this problem in the first place. The commands for this are:

```
rndc freeze example.com
```
(edit example.com zonefile)
```
rndc reload example.com
rndc thaw sxample.com
```
