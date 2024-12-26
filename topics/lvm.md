# LVM

* Complete version moved to [LVM in Ubuntu ir wiki](https://wiki.ubuntu-ir.org/wiki/LVM)

## How to increase disk space with lvm

1. Add a new disk like ```/dev/sdb``` or create a partiotion on an unallocated space. like ```/dev/sda3```

2. Add it to existing volume group or create new one

```sudo vgextend debian-vg /dev/sdb or /dev/sda3```

3. Use added entity inside volume group to make it usable

```sudo lvextend -r -l +100%FREE /dev/mapper/debian--vg-var```


# Check is it OK
```$ sudo vgdisplay```

## Task

```
lsblk -f 

# Add new storage

# check it
fdisk -l

# partiton it to create sdb1
fdisk /dev/sdb 

lsblk -f 
pvdisplay 

# create new phyical volume on sdb1
pvcreate /dev/sdb1 

pvdisplay 

# extend existing volume group with new created physical volume sdb1
vgextend centos /dev/sdb1

vgdisplay 
lvdisplay 

# extend existing logical volume with newly added size
lvextend -r -l +100%FREE /dev/centos/home

lsblk -f 
reboot 


lsblk -f 
df -hl

```
