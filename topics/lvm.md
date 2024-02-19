# LVM

## How to increase disk space with lvm

1. Add a new disk like ```/dev/sdb``` or create a partiotion on an unallocated space. like ```/dev/sda3```

2. Add it to existing volume group or create new one

```sudo vgextend debian-vg /dev/sdb or /dev/sda3```

3. Use added entity inside volume group to make it usable

```sudo lvextend -r -l +100%FREE /dev/mapper/debian--vg-var```


# Check is it OK
```$ sudo vgdisplay```

