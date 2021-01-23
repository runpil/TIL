## Swap Memory
- Swap Memory는 주 Memory가 부족할 때 하드디스크와 같은 공간을 Memory로 사용하기 위한 가상 Memory

## Check Swap Memory
```bash
# Swap 부분 used가 Swap 사용량을 나타냄
$ free -m
              total        used        free      shared  buff/cache   available
Mem:          64086       35204         745        2457       28136       25517
Swap:         65535        1903       63632
```

## Swap Memory Disable
```bash
# swapoff - reboot 하면 원상복구 되는 설정
$ sudo swapoff -a

# fstab - 영구 설정 (swap 단어를 포함한 라인 #으로 주석처리)
$ sudo vi /etc/fstab
# /dev/mapper/VolGroupData-lv_data    /data     xfs nodev,noatime,inode64,allocsize=16m  0 0
```