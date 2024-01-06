#~/.screenrc
```
  autodetach on                         # default: on
  startup_message off                   # default: on
  crlf off                              # default: off
  multiuser on
  defscrollback 100000                   # default: 100
  silencewait 15                        # default: 30
  bufferfile            $HOME/.screen_exchange
  shell -$SHELL
  pow_detach_msg "Screen session of \$LOGNAME \$:cr:\$:nl:ended."
termcapinfo  * '' 'hs:ts=\E_:fs=\E\\:ds=\E_\E\\'
termcapinfo xterm* ti@:te@
defnonblock on
  termcap  xterm hs@:cs=\E[%i%d;%dr:im=\E[4h:ei=\E[4l
  terminfo xterm hs@:cs=\E[%i%p1%d;%p2%dr:im=\E[4h:ei=\E[4l
  termcapinfo  xterm Z0=\E[?3h:Z1=\E[?3l:is=\E[r\E[m\E[2J\E[H\E[?7h\E[?1;4;6l
  termcapinfo xterm* OL=100
  termcapinfo xterm 'VR=\E[?5h:VN=\E[?5l'
  termcapinfo xterm 'k1=\E[11~:k2=\E[12~:k3=\E[13~:k4=\E[14~'
  termcapinfo xterm 'kh=\EOH:kI=\E[2~:kD=\E[3~:kH=\EOF:kP=\E[5~:kN=\E[6~'
  termcapinfo xterm 'hs:ts=\E]2;:fs=\007:ds=\E]2;screen\007'
  termcapinfo xterm 'vi=\E[?25l:ve=\E[34h\E[?25h:vs=\E[34l'
  termcapinfo xterm 'XC=K%,%\E(B,[\304,\\\\\326,]\334,{\344,|\366,}\374,~\337'
  termcapinfo xterm* be
  termcapinfo xterm* ti@:te@
  termcapinfo xterm|xterms|xs ti@:te=\E[2J
  termcapinfo wy75-42 xo:hs@
  termcapinfo wy* CS=\E[?1h:CE=\E[?1l:vi=\E[?25l:ve=\E[?25h:VR=\E[?5h:VN=\E[?5l:cb=\E[1K:CD=\E[1J
  termcapinfo  hp700 'Z0=\E[?3h:Z1=\E[?3l:hs:ts=\E[62"p\E[0$~\E[2$~\E[1$}:fs=\E[0}\E[61"p:ds=\E[62"p\E[1$~\E[61"p:ic@'
  termcap  vt100* ms:AL=\E[%dL:DL=\E[%dM:UP=\E[%dA:DO=\E[%dB:LE=\E[%dD:RI=\E[%dC
  terminfo vt100* ms:AL=\E[%p1%dL:DL=\E[%p1%dM:UP=\E[%p1%dA:DO=\E[%p1%dB:LE=\E[%p1%dD:RI=\E[%p1%dC
  termcapinfo linux C8
" screen
  bind 'K' kill
  bind 'I' login on
  bind 'O' login off
  bind '}' history
  register [ "\033:se noai\015a"
  register ] "\033:se ai\015a"
  bind ^] paste [.]
  bind = resize =
  bind + resize +3
  bind - resize -3
hardstatus alwayslastline
hardstatus string '%{WB}%H %{W}| %{Y}%l %{W}| %?%{w}%-w%?%{+b g}[%{W}%{r}%n%{W} %t%?{%u}%?%{-b g}]%{W}%?%+w%?%=%{G}| %{Y}%d-%m-%Y %c:%s '
  bind k
  bind ^k
  bind .
  bind ^\
  bind \\
  bind ^h
  bind h
  bindkey "" next
  bindkey " prev
  bindkey ""

screen -t dnsmasq
screen -t dnsmasq
screen -t dnsmasq
screen -t dnsmasq
screen -t host-01 ssh host-01
screen -t host-02 ssh host-02
screen -t host-03 ssh host-03

```

