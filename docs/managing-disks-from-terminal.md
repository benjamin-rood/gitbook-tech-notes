## Managing disks from terminal

### Find usb devices

```
lsof -v | grep {some identifier of the disk, e.g. 'StoreJet' - drive or manufacturer type}
```

### Eject disk

```
eject /dev/sdX
```

### Power off device

```
udisksctl power-off -b /dev/sdX
```



