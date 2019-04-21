## Using Docker Volume

- Create a directory in your 'user' home directory called 'docker'. 
 - Within that directory, create another directory called 'mydata'. 
 - Within mydata, create a file called 'zekeData.txt' containing any text message you want.

        [user@zekelabs ~]$ mkdir docker
        [user@zekelabs ~]$ cd docker
        [user@zekelabs ~]$ mkdir mydata
        [user@zekelabs ~]$ cd mydata
        [user@zekelabs mydata]$ ll
        total 0
        [user@zekelabs mydata]$ echo "This is data originally kept in a file at Docker host" >> zekeData.txt
        [user@zekelabs mydata]$ ll
        total 4
        -rw-rw-r-- 1 user user 18 Dec 15 15:21 zekeData.txt
        [user@zekelabs mydata]$ cd ..
        [user@zekelabs docker]$ ll
        total 0
        drwxrwxr-x 2 user user 23 Dec 15 15:21 mydata


2. Create a docker container name 'local_vol' from the 'centos:6' image. 
- The container should be created in interactive mode, 
- attached to the current terminal and running the bash shell.

- Finally create the container with a volume (or directory) called 'containerDirectory' 
- so that the system will automatically create the directory/mount when the container starts.

      [user@zekelabs docker]$ docker run -it --name="local_vol" -v /containerDirectory centos:6 /bin/bash

      [root@191131068f8c /]#


3. List the filesystems within the container, specifically looking for the volume/directory that was added to the container during creation.

       [root@191131068f8c /]# df -h
       Filesystem            Size  Used Avail Use% Mounted on
       rootfs                9.8G  254M  9.0G   3% /
       /dev/mapper/docker-8:2-203558447-191131068f8ceffe6fb38198a61b9806f27e4d22de3c8b0d2aec4c0c4fe7f88d
                             9.8G  254M  9.0G   3% /
       tmpfs                 2.0G     0  2.0G   0% /dev
       shm                    64M     0   64M   0% /dev/shm
       /dev/sda2              36G  4.3G   32G  12% /containerDirectory
       tmpfs                 2.0G     0  2.0G   0% /run/secrets
       /dev/sda2              36G  4.3G   32G  12% /etc/resolv.conf
       /dev/sda2              36G  4.3G   32G  12% /etc/hostname
       /dev/sda2              36G  4.3G   32G  12% /etc/hosts
       tmpfs                 2.0G     0  2.0G   0% /proc/kcore
       tmpfs                 2.0G     0  2.0G   0% /proc/timer_stats
       [root@191131068f8c /]# ls -al /containerDirectory/
       total 4
       drwxr-xr-x  2 root root    6 Dec 15 20:46 .
       drwxr-xr-x 23 root root 4096 Dec 15 20:46 ..
       [root@191131068f8c /]#

 

4. Exit the container. This time, lets create another container called 'remote_vol'
 - with the same container configuration except when creating the volume in the container, 
 - link the volume name 'mydata' to the underlying host directory structure created in Step #1.

        [user@zekelabs docker]$ docker run -it --name="remote_vol" -v /home/user/docker/mydata:/mydata centos:6 /bin/bash
        [root@fnasfavdvadjv /]#
 

5. Once the container is started, list the disk mounts and verify the remote (host) volume is mounted. 
            
       [root@fnasfavdvadjv /]# df -h

       Filesystem            Size  Used Avail Use% Mounted on

       rootfs                9.8G  254M  9.0G   3% /

       /dev/mapper/docker-8:2-203558447-fnasfavdvadjva74f4e0e65efd02191685570ef89995d57716a2ff09c3078d7f8

                             9.8G  254M  9.0G   3% /

       tmpfs                 2.0G     0  2.0G   0% /dev

       shm                    64M     0   64M   0% /dev/shm

       ...

       tmpfs                 2.0G     0  2.0G   0% /proc/timer_stats

6. Change to that directory and verify that the text file created in Step #1 appears with the content created.

        [root@fnasfavdvadjv /]# ls -al /mydata/

        total 8

        drwxrwxr-x  2 1000 1000   23 Dec 15 20:21 .

        drwxr-xr-x 23 root root 4096 Dec 15 20:51 ..

        -rw-rw-r--  1 1000 1000   18 Dec 15 20:21 zekeData.txt

        [root@fnasfavdvadjv /]# cat /mydata/zekeData.txt 

        This is data originally kept in a file at Docker host

        [root@fnasfavdvadjv /]#
