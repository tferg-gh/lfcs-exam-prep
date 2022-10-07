**rsync**: Remote Synchronization. The remote server must have an SSH daemon running on it. #rsync #ssh
``` sh
rsync [options] [source] [target]
rsync -a /Pictures tom@192.168.0.108:/home/tom/Pictures/ # -a for archive
```
Only updates changes after first sync. 

**dd**: Disk Imaging. #sudo #dd
``` sh
sudo dd if=/dev/vda of=diskimage.raw bs=1M status=progress # if = input file of = output file bs = block size
```