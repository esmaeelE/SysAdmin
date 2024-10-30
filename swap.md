# Swap
```
/etc/fstab
mount -a 
swapoff -a
swapon -a
```

Use file as swap
```
sudo fallocate -l 1G /swap.img
sudo chmod 0600 swap.img
sudo swapon swap.img
```

