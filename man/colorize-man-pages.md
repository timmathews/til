# Colorize man pages
> by [Peter Hosey]
> (http://boredzo.org/blog/archives/2016-08-15/colorized-man-pages-understood-and-customized)
> and
> [@cocoalabs](https://gist.github.com/cocoalabs/2fb7dc2199b0d4bf160364b8e557eb66)

I'm currently using this configuration

```
man() {
  LESS_TERMCAP_mb=$'\e'"[1;31m" \
  LESS_TERMCAP_md=$'\e'"[1;36m" \
  LESS_TERMCAP_me=$'\e'"[0m" \
  LESS_TERMCAP_se=$'\e'"[0m" \
  LESS_TERMCAP_so=$'\e'"[1;44;33m" \
  LESS_TERMCAP_ue=$'\e'"[0m" \
  LESS_TERMCAP_us=$'\e'"[1;34m" \
  command man "$@"
}
```

It's very blue
