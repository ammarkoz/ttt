

## Backup commands

```bash
Backup
 => mkdir /root/hct/
 => cp /etc/*.conf /root/hct/
 => tar -cvpf name.tar /root/hct/*

Restore
 => tar -xvpf /root/name.tar

Options:
-c (create bkup)
-x (restore)
-f (file)
-v(verbos mode)-name of files that take as bkup/list of files 
-p(preseve per/permission)
-z (zip)
to create backup:
tar -c(other option) filenamebkup.tar source
to make bkup in spesific folder
ex:
#mkdir imdata
==>copy same files from etc into this folder
#cp /etc/*.conf /root/imdata/
==>to check
#ls /root/imdata/ 
==> to copy for loop
#cp /dev/loop* /root/imdata/ 
==> to check the backup
#ls /root/imdata/ 
to make bk up:
#tar -cpvf mybackup.tar /root/imdata/*
==> red color mybkup.tar (mean 1 bkup is created)
#ls
if i want to see the list of file as bkup +no list for process
#tar -cpf 2mybkup.tar /root/imdata/*
if i don't want to take permission:
#tar -cf 3mybkup.tar /root/imdata/*
if i do ls -l: i will see many backup files الحجم .مع
#ls -l 
if i want to comprese the file of backup:
#tar -cpvzf mybkup.tar.gz /root/imdata/*
if i want to see size of compere the size:
#ls -l
remove data folder:
#rm -rf impData/
to check:
#ls /root/impData
-to retrive/restore the data from the bkup:
#cd ..
#tar -xpvf /root/mybkup.tar
to check the data that is restored:
#cd /root/
#ls -l /root/impData/
to make files:
#cat > abc.txt
jskdnakjsdnj
^d
show abc.txt
#ls -l 
make new bkup file with standard format:it will specify date and time (descripte date and time)u have 
bkup until 1pm
#tar -cf confbkup_10032021_01pm.tar /root/imdata/*
#ls -l
```

## DHCP

```bash
apt install isc-dhcp-server
nano /etc/dhcp/dhcpd.conf => photos below

systemctl restart isc-dhcp-server-service
ifconfig enp0s3 192.168.30.101/24
subnet 192.168.30.0 netmask 255.255.255.0(
range 192.168.30.100 192.168.30.150;
option routers 192.168.30.1;
)
change network in both machine to internal 
```

## Samba

```bash
sudo apt-get update
#install sambe  
1 => sudo apt-get install samba

#check the status of the Samba services
2 => systemctl status smbd nmbd

#add new user
3 => useradd testsamba
4 => passwd testsamba

#make new directory to be share with windows
5 => mkdir /home/testsamba
6 => mkdir /home/testsamba/mydir

#add the file to samba config
7 => nano /etc/samba/smb.conf
All down under profiles and printers
[mydir]

#allow samba through firewall
8 => sudo ufw allow samba
chown 777 /home/testsamba/mydir
```



## LVM

```bash
LVM => Logical Volume Management
- Deploying logical storage rather than physical storage.

- Using Logical Volume Management (LVM) to manage storage:
A physical disk is divided into one or more physical volumes (PVs). 

These PVs can then be combined to create Logical Volume Groups (VGs).

----------------------------------------------------------------------
1) Add a new hard disk of 50 GB in your system. The hard disk name must be the same as your name.

2) Create an extended partition of 50 GB.
Fdisk 
=> fdisk /dev/sdb
=> n > e > Enter in space

3)Create four (4) logical partitions of 10 GB each.
=> fdisk /dev/sdb
=> n > 

4) Create physical partition on second, third and fourth partitions.
#To show all partition
=> fdisk /dev/sdb > p 

#Create physical partition
in same menu => Pvcreate /dev/sdb5 /dev/sdb6 /dev/sdb7 /dev/sdb8
=> w > to save

5) Verify either physical volumes are created or not.
in same menu => pvdisplay

6) Combine second and third partitions into a group named “YourFirstName”.
 => vgcreate “ammar” /dev/sdd6  /dev/sdd7

7) Verify either volumes group is created or not.
vgdisplay |more OR vgdisplay ammar

8) Drive logical volume named "YourLastName" of 15GB from a group.
 => lvcreate –n “alawaidi”   --size +15G /dev/ammar

9) Verify either logical volume is created or not.
 => lvdisplay

10)Format logical volume with Linux default file system.
 => Mkfs.ext4 /dev/ammar/alawaidi 

11) Make newly created logical volume usable for the uses.
#command displays the disk space usage for all mounted file systems in human-readable format.
 => df -h
 => Mkdir newdisk 
 => Mount /dev/ammar/alawaidi  /root/newdisk/
 => df-h

12) Add 3 GB more in the newly created logical volume.
 => Lvextend  –L +3G /dev/ammar/Alawaidi 
#Update the partition table without formatting.
 => Resize2fs /dev/ammar/alawaidi

14 )Add new physical volume (fourth partition) to the group.
 => Pvcreate /dev/sdd8 
 => vgextend “ammar”  /dev/sdd8

15) Verify either new volume is added to the volume group or not.
vgdisplay

16) Remove 2 GB from the logical volume.
=> Lvreduce -L -2G /dev/ammar/alawaidi
=> Resize2fs /dev/ammar/alawaidi

```

## IP

```bash

IP address add 192.168.1/24 dev enp0s3
IP addr show
route

#Assign an IP address and subnet mask to the network interface
 => ifconfig enp0s3 *.*.*.* netmask *.*.*.*

#Bring the network interface up or down:
 => ifconfig enp0s3 up/down

#Add a route for a specific network:
 => route add -net 172.16.0.0 netmask 255.255.255.0 gw gwname

#Add a default gateway:
 => route add default gw gwname

#Change ip 
 => ifconfig enp0s3 192.168.7.10/24

Note: The network name "default" is a shorthand for 0.0.0.0, which represents the default route.

#ping 172.16.0.50
#ctrl +c > cancel
disable/enaple
#ifconfig enp0s3 down
#ifconfig enp0s3 up
show all i/f
#ifconfig -a
Gateway
for default n/w:
#route add 0.0.0.0 gw 10.0.2.1(IP)
#route add default gw 10.0.2.1(IP)
Add specific n/w:
#route add -net 10.0.2.0 netmask 255.255.255.0 gw 
10.0.2.1
Delete /remove specific n/w:
#route del -net 10.0.2.0 netmask 255.255.255.0 gw 
10.0.2.1
routing table
#route -n
get all info about command 
#man route
#man ifconfig
to change ip manually: trun off dhcp:
cat /etc/netplan/50-cloud-init.yam1
vi /etc/netplan/50-cloud-init.yam1
i
make it false
iwq
-----------------------

```

## DNS

```bash
DNS
#Install DNS serve:
1 => Apt-get install bind9

#Check service (running/active)
2 => Systemctl status bind9

#To stop running service
  => Systemctl stop bind9

#Ran the service 
  => Systemctl start bind9

#Check the file 
3 => cat /etc/bind/

#Edit the file 
4 => nano named.conf.options

5 =>
Go to 
//forwarders {
//8.8.8.8; //};

6 => Delete all // and change 8.8.8.8 to 0.0.0.0 

#Restart DNS server
7 => systemctl restart bind9

#Check the query time(sec) from google /getting response from DNS cache 
8 => dig google.com
```

## HTTP Apache

```bash

#Install Apache serve: (first update, upgrade)
1 => Apt-get install apache2
#To list app
2 => ufw app list

#Check the status of firewall
3 => ufw status
#Enable firewall
4 => ufw enable

#Allow Apache packet
5 => ufw allow ‘Apache’
 => ufw status

#Start Apache 
6 => systemctl start apache2

#Stop Apache 
 => systemctl stop apache2

#Restart Apache (if you made change in on place ,first it will stop the service then start it will load again and it will take long time ,it is not good idea)
 => Systemctl restart apache2

#Reload Apache (only restart the place where we change only )
 => Systemctl reload apache2

#Check if Apache start 
 => Systemctl status apache2 

#change IP address and set it for apache server
7 => ifconfig enp0s3 192.168.7.10/24

#The web page is stored in
8 => ls /var/www/html/

#Create newvi page 
9 => nano var/www/html/mypage.html

# in windows 
IP address: 192.168.7.100
Subnet mask: 255.255.255.0
Default gateway: 192.168.7.1
Preferred DNS server: 192.168.7.10 => server ip

```


NFS

```bash
#install nfs kernal
1 => apt-get install nfs-kernel-server

#making directory to be share later
2 => mkdir /mnt/server_share

#change the ownership to nobody:nogroup,
3 => chown nobody:nogroup /mnt/server_share

#To change the permissions to 777 | 4:r , 2:w , x:1 
4 => chmod 777 /mnt/server_share

#file is used by the NFS server to define the directories that are exported and the options associated with them.
5 => nano /etc/exports

#add this line to /etc/exports
6 => /mnt/server_share 192.168.7.10/24(rw,sync)

#change IP address of the machine 
7 => ifconfig enp0s3 192.168.7.10/24

#enable firewall
8 => ufw enable

#exportfs -a, it scans the /etc/exports file and exports all the directories listed in it.
9 => exportfs -a

#restart the NFS (Network File System) server service
10 => systemctl restart nfs-server
====> systemctl restart nfs-kernel-server 

#add a rule to the UFW firewall configuration that allows incoming NFS traffic from the specified subnet
11 => ufw allow from 192.168.7.0/24 to any port nfs
ufw status

------------------------------
in client

#install the NFS (Network File System) client package
1 => apt install nfs-common

#directory to mount NFS shares from the server
2 => mkdir /mnt/client_share

#change IP address of the machine 
3 => ifconfig enp0s3 192.168.7.20/24

#mount the NFS share from the server at 192.168.7.10 and the directory /mnt/server_share onto the local directory /mnt/client_share.
4 => mount 192.168.7.10:/mnt/server_share /mnt/client_share

#For testing 
cd /mnt/client_share
echo "Hi" > clientfile.txt

#in server
ls -l /mnt/server_share
```

### Firewall

```bash
# Clear existing rules and chains
iptables -F
iptables -X

# Allow SSH from a specific IP address
iptables -A INPUT -p tcp -s <trusted_IP_address> --dport 22 -j ACCEPT

# Allow HTTP and HTTPS traffic
iptables -A INPUT -p tcp --dport 80 -j ACCEPT 
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Allow outgoing connections for DNS
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

# Allow outgoing HTTP and HTTPS connections
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# Block incoming connections on port 25 (SMTP)
iptables -A INPUT -p tcp --dport 25 -j DROP

# Block incoming connections on port 135 (RPC)
iptables -A INPUT -p tcp --dport 135 -j DROP

#block the IP address 192.168.1.100 from accessing your server.
iptables -A INPUT -s 192.168.1.100 -j DROP | ACCEPT

#save the rules
sudo service iptables save
iptables-save > root/myfw
cat /root/myfw

#To list the firewall rule
iptables -L INPUT
iptables -L --line-numbers |more

#To delete the rule with rule number 1
iptables -D INPUT 1
```
