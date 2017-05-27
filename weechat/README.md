#Setup reminders

##[passwords]
/secure passphrase <pass>
/secure set bncpass <pass>

##[servers - general]

 $ openssl s_client -connect my.bouncer.net:6000 </dev/null 2>/dev/null | openssl x509 -in /dev/stdin -noout -fingerprint -sha256  | sed s/://g | cut -c 20-

/server add [name] katiezone.biz/6000 -ssl -username=k8e/[network] -password=${sec.data.bncpass} -autoconnect
/set irc.server.[name].ssl_fingerprint 0D47B9FA7EDDF7C79DC3C8226CDCE8391939BC533FBDFB682C8553A77D3B942B


##[servers]

/server add undernet katiezone.biz/6000 -ssl -username=k8e/undernet -password=${sec.data.bncpass} -autoconnect
/set irc.server.undernet.ssl_fingerprint 0D47B9FA7EDDF7C79DC3C8226CDCE8391939BC533FBDFB682C8553A77D3B942B

/server add freenode katiezone.biz/6000 -ssl -username=k8e/freenode -password=${sec.data.bncpass} -autoconnect
/set irc.server.freenode.ssl_fingerprint 0D47B9FA7EDDF7C79DC3C8226CDCE8391939BC533FBDFB682C8553A77D3B942B

/server add stl-tech katiezone.biz/6000 -ssl -username=k8e/stl-tech -password=${sec.data.bncpass} -autoconnect
/set irc.server.stl-tech.ssl_fingerprint 0D47B9FA7EDDF7C79DC3C8226CDCE8391939BC533FBDFB682C8553A77D3B942B

/server add lucsc katiezone.biz/6000 -ssl -username=k8e/lucsc-slack -password=${sec.data.bncpass} -autoconnect
/set irc.server.lucsc.ssl_fingerprint 0D47B9FA7EDDF7C79DC3C8226CDCE8391939BC533FBDFB682C8553A77D3B942B

/server add DecentralizedWeb katiezone.biz/6000 -ssl -username=k8e/DecentralizedWeb -password=${sec.data.bncpass} -autoconnect
/set irc.server.DecentralizedWeb.ssl_fingerprint 0D47B9FA7EDDF7C79DC3C8226CDCE8391939BC533FBDFB682C8553A77D3B942B


##[scripts]

/script install autosort.py iset.pl grep.py 

/autosort rules add irc.server.*.&* = 0
/autosort rules add irc.server.*.#* = 1
/autosort rules add irc.server.*.\*status = 2


##[buffers]

/set irc.look.server_buffer independent

/set buflist.format.buffer "${if:${type}==server?${color:black,cyan}${format_number}${color:white}:${color:white}${format_number}${indent}${color_hotlist}}${if:${type}!=0&&${type}!=exec?${if:${cutscr:8,+,${name}}!=${name}?${cutscr:8,${color:${weechat.color.chat_prefix_more}}+,${name}}:${cutscr:8, ,${name}                             }}:${name}}${format_hotlist}${if:${buffer.full_name}==perl.iset? ${color:cyan}${buffer.local_variables.iset_filter}} ${color:cyan}${buffer.local_variables.buflist}"
/set buflist.format.buffer_current "${if:${type}==server?${color:*white,cyan}:${color:*white}}${hide:>,${buffer[last_gui_buffer].number}} ${indent}${color_hotlist}${name}${if:${buffer.full_name}==perl.iset? ${color:cyan}${buffer.local_variables.iset_filter}} ${color:cyan}${buffer.local_variables.buflist}"
/set buflist.format.hotlist_highlight "${color:magenta}"
/set buflist.format.hotlist_message "${color:yellow}"
/set buflist.format.hotlist_private "${color:green}"
/set buflist.format.number "${number}${if:${number_displayed}?.: }"


##[Title bar]

/bar add activetitle window top 1 0 buffer_title
/set weechat.bar.activetitle.priority 500
/set weechat.bar.activetitle.conditions "${active}"
/set weechat.bar.activetitle.color_fg white
/set weechat.bar.activetitle.color_bg 31
/set weechat.bar.activetitle.separator on

/set weechat.bar.title.conditions "${inactive}"
/set weechat.bar.title.color_fg black
/set weechat.bar.title.color_bg 31


##[status bar]

/bar add rootinput root bottom 1 0 [mode_indicator]+[buffer_name]+[input_prompt]+(away),[input_search],[input_paste], > input_text,[vi_buffer]"
/set weechat.bar.rootinput.color_bg black
/set weechat.bar.rootinput.priority 1000
/bar del input
/bar set rootinput name input


##[key bindings]

/key bind ctrl-J "/window page_up"
/key bind ctrl-K "/window page_down"


##[other]

/set weechat.look.bar_more_down "▼"
/set weechat.look.bar_more_left "◀"
/set weechat.look.bar_more_right "▶"
/set weechat.look.bar_more_up "▲"
/set weechat.look.item_buffer_filter "•"
/set weechat.look.separator_horizontal "="
/set weechat.color.separator cyan

