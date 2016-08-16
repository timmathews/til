# Print man pages as PDF

The `-t` flag for the man command will run a man page through troff/groff and create PostScript instead of printing to
the screen. By default groff uses Times as its output font. Blech.

To make pretty PostScript, change `/etc/manpath.config` to tell groff to use a different font. Font definitions are
stored in `/usr/share/groff/current/font/devps` for PS output. They have two letter names, but the first letter is the
important one (of course it is).

For instance, to use Palatino instead of Times, in `/etc/manpath.config`, about 2/3rds of the way down is the program
definitions section

```
#---------------------------------------------------------
# Program definitions.  These are commented out by default as the value
# of the definition is already the default.  To change: uncomment a
# definition and modify it.
#
#DEFINE   pager pager -s
#DEFINE   cat cat
#DEFINE   tr  tr '\255\267\264\327' '\055\157\047\170'
#DEFINE   grep  grep
DEFINE  troff   groff -mandoc -f P
#DEFINE   nroff   nroff -mandoc
#DEFINE   eqn   eqn
#DEFINE   neqn  neqn
#DEFINE   tbl   tbl
#DEFINE   col   col
#DEFINE   vgrind  vgrind
#DEFINE   refer   refer
#DEFINE   grap  grap
#DEFINE   pic   pic -S
#
#DEFINE   compressor  gzip -c7
#---------------------------------------------------------
```

Uncomment the troff line and add `-f P`. To use Avant Garde Gothic Book, `-f A`.

Then to make a PDF (requires ghostscript installed):

```
$ man -t <manpage> | ps2pdf - <manpage>.pdf
```
