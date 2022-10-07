# Swap
Acts as a sort of virtual RAM where the system can offload some data held in RAM temporarily so it doesn't crash when you run out of memory. 

##### Set partition to swap type
```sh
sudo cfdisk /dev/sda # > gpt > select parition > type > Linux swap > Write > yes 
```

##### Format the partition as swap
```sh
sudo mkswap /dev/sda1
```

##### Set the swap to enabled
```sh
sudo swapon /dev/sda1
```

##### Set the swap to disabled
```sh
sudo swapoff /dev/sda1
```

#### Resize a swap file
###### Disable swap for file
```sh
sudo swapoff /swapfile
```

##### Resize swap file
```sh
sudo dd if=/dev/zero of=/swap bs=1M count=3096 # bs * count = new size
```

##### Set file permissions to root read/write only
```sh
sudo chmod 600 /swapfile
```

##### Format file as swap
```sh
sudo mkswap /swapfile
```

##### Enable swap
```sh 
sudo swapon /swapfile
```

## List swap
```
swapon --show
```

## List disk partitions
```
lsblk
```

