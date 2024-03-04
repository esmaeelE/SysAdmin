# Archive

tar command is tape archiver.
we can combine many files under the name of a new set.

Also tar can be used with compress tools like zip and bzip to reduce output file size.

## Untar, not preserve original directory structure

### show contents without extract

```
$ tar -tf lpic1_eng_new.tar.gz                                                                                                 
learn/                                                                                                                                            
learn/LPIC 1 - 81 - 110.3 (1⧸3) - Securing data with encryption; Key Pairs (Public & Private) and SSH [ElbC0EtZc4c].mp4                           
learn/LPIC 1 - 83 - 110.3 (3⧸3) - Securing data with encryption; Using gpg to Encrypt⧸Decrypt & Sign data [BX6BB8bqy24].mp4                       
learn/LPIC 1 - 008 - 101.2 - Part 2⧸2 - Boot Process; logs (dmesg, logs, journalctl) & init (systemd&SysV) [Sn20NKM0hbw].mp4                      
learn/Why vi ⧸ vim is important and how to use it to edit files [7S5RaX1OsTE].mp4                                         
```

#### We have a directory structure here in original tar file.

Runing below command with gnu tar, remove original directory strucrure and extract all contents in the root of **lpic1_eng_new**

```
mkdir lpic1_eng_new
tar -xvf lpic1_eng_new.tar.gz   --strip-components=1 -C lpic1_eng_new/
```

