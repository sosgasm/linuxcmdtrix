# Error during installation of Grapheneos on a Pixel4a
The error was: FAILED remote 'changing slot with snapshot applied may cancel the update.'

#### Prerequisites
##### Just follow the installation guide on grapheneos.org. I tried both installation options, the webinstaller and the commandline way, using Fastboot.<br>

### Knowledge
```
Read about:
Fastboot installation and commands
Grapheneos installation (graphenos.org)
```

---

### Fix

```
Figure out the snapshot state:

s0s@ubuntu:~$ fastboot getvar snapshot-update-status
snapshot-update-status: merging
Finished. Total time: 0.037s

I tried to complete the merge operation:
s0s@ubuntu:~$ fastboot snapshot-update merge
Snapshot merge                                     FAILED (remote: 'snapshot-update [cancel]')
fastboot: error: Command failed

So merging was not working. Finally I decided to cancel the snapshot update:

s0s@ubuntu:~$ fastboot snapshot-update cancel
Snapshot cancel                                    (bootloader) update cancelled
OKAY [  0.121s]
Finished. Total time: 0.121s
s0s@ubuntu:~$ fastboot getvar snapshot-update-status
snapshot-update-status: none
Finished. Total time: 0.025s

```

### Your welcome

```
My source for all fastboot snapshot commands:
https://source.android.com/docs/core/ota/virtual_ab/implement#fastboot-tooling-changes
```

