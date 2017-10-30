# Fix network error
[Manjaro Forum](https://forum.manjaro.org/t/vmware-needs-ethernet0/27271/9)

```
sudo systemctl start vmware-networks
sudo systemctl enable vmware-networks
```

```
sudo /usr/bin/modprobe vmnet
sudo vmware-networks --start
```
