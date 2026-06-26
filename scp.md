# scp - Secure Copy

[Back to README](README.md)

scp (SecureCopy) enables you to move files from / to a remote instance.

**Sub-headings:**

* [sending files](#sending-files)
* [retrieving files](#retrieving-files)

## sending files

| command | action |
| ----- | ----- |
| `scp [PATH/FILENAME] [USER@SERVER:/home/user/FILENAME]` | simplest format to send a file using scp (without Auth Key). E.g. `scp linux_file.txt ubuntu@52.64.26.152:home/ubuntu/files/dest_filename.txt` |
| `scp -r [DIRECTORYPATH] [USER@SERVER:]` | use `-r [DIRECTORYPATH]` to move an entire folder of files. `-r` is 'recursive'. Just supplying ':' means it will drop to the home directory |
| `scp -i [AUTHKEYPATH/FILENAME] [PATH/FILENAME] [USER@SERVER:/home/user/FILENAME]` | send a file using scp with Auth Key. E.g. `scp -i ~/.ssh/ha_aws_k.pem linux_distros.txt ubuntu@ec2-52-64-26-152.ap-southeast-2.compute.amazonaws.com:/home/ubuntu` |

## retrieving files

| command | action |
| ----- | ----- |
| `scp [USER@SERVER:/home/USER/FILENAME] [/home/USER/FILENAME]` | simplest form assuming no auth key |
| `scp -i [~/.ssh/id_rsa.pub] [USER@SERVER:/home/USER/FILENAME] [/home/USER/FILENAME]` | retrieve a file from a server with auth key. E.g. `scp -i /home/hca/.ssh/ha_aws_k.pem ubuntu@ec2-52-64-26-152.ap-southeast-2.compute.amazonaws.com:/home/ubuntu/hca_test .` (note that . defines current directory) |
