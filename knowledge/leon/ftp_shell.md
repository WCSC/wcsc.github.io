# The FTP shell

#### Looks like this `ftp>_____`

## Useful Commands
Here some helpful commands for maneuvering inside shell
* pwd, ls, cd, rmdir, mkdir - work as expected
* lcd - changes directory for client
* bye - closes connection 
* get file1 - downloads file1 from server to client
* mget file1 file2 - get fro multiple files
* delete file1 - deletes file1 from server
* put file1 - puts file1 on the server from the client
* mput file1 file2 - puts multiple files


## LFTP Shell
#### Looks like this `lftp:~>_____`
The LFTP shell can used like a normal FTP Shell and as a SFTP shell.
* lftp:~> !ls ---- execute any shell command by adding a ! before it on the local host
* lftp:~> ls ---- execute any shell command on the remote host
* lftp:~> set ssl:verify-certificate no	---- This will allow you to use self-signed certs, like in the vsftpd guide
* lftp:~> connect localhost ---- Will Connect you to localhost, you can replace localhost with whatever
* lftp my_user@localhost:~> login my_user ---- Login as user after you connect
* lftp my_user@localhost:~> close ---- Closes the connection

[Back](../../)