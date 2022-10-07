###### cryptsetup
Encrypt a volume with either plain or LUKS encryption. 

```sh
sudo cryptsetup --verify-passphrase open --type plain /dev/vde mysecuredisk
```

Encrypts the volume at `/dev/vde` with `plain` encryption as `mysecuredisk`

`--verify-passphrase` makes cryptsetup ask for the passphrase twice to make sure we don't set it incorrectly. 

`open` is the action we want cryptsetup to perform. We're telling it to open this device for reading encrypted data on it and writing encrypted data to it.

`--type plain` is an option we're adding to the `open` action. It modifies the action to use the plain encryption scheme.

`/dev/vde` is the device where data will be encrypted on and decrypted from.

`mysecuredisk` is a name we can freely choose for our mapped device. This device will be located at `/dev/mapper/mysecuredisk`

```sh
sudo mkfs.xfs /dev/mapper/mysecuredisk
```

Create a file system on the encrypted block device

```sh
sudo mount /dev/mapper/mysecuredisk /mnt
```

Mount the disk like any normal disk.

The device at /dev/mapper/mysecuredisk acts as a normal disk would however, behind the scenes what is actually happening is Linux is encrypting any data being written to /dev/mapper/mysecuredisk and then writing it to /dev/vde and similarly any data being read from the disk, Linux is decrypting first from /dev/vde and then sends it to the application. 

```sh
sudo umount /mnt
```

```sh
sudo cryptsetup close mysecuredisk
```

First, if you want to close a connection, you need to unmount the device and then you can close the disk. 

##### LUKS
Linux Unified Key Setup

```sh
sudo cryptsetup luksFormat /dev/vde
```

This will format the device to be used with LUKS encryption. 

```sh
sudo cryptsetup luksChangeKey /dev/vde
```

Change the encryption key for the device.

```sh
sudo cryptsetup open /dev/vde mysecuredisk
```

At this point everything is the same as with the plain encryption scheme we used before for writing, mounting, and closing the connection.