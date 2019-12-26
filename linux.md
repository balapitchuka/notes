### Referecences
https://github.com/PacktPublishing/Learn-Linux-Shell-Scripting-Fundamentals-of-Bash-4.4

### The Linux Filesystem
1. Everything is a file
2. A **filesystem** is, in essence, the way data is stored and retrieved on a physical medium (which can be a hard disk, 
   solid state drive, or even RAM).
3. It is a software implementation that manages where and how the bits are written and found again, and may include
   various advanced features which enhance reliability, performance, and functionality

### ToDo
4. The concept of a filesystem is abstract: there are many filesystem implementations, which are confusingly often referred to as filesystems. We find it easiest to grasp by ordering the filesystems in families, just as with Linux distributions: there are Linux filesystems, Windows filesystems, macOS filesystems, and many others. The Windows filesystem family spans from the earliest filesystem of FAT up until the newest ReFS, with the most widely used currently being NTFS.

5. the most important filesystems in the Linux family are the following implementations:

ext4
XFS
Btrfs

6.The most commonly used Linux filesystem implementation is currently ext4. It is the fourth iteration in the extended file system (ext) series of Linux filesystems. It was released in 2008 and is considered very stable, but it is not state-of-the-art; reliability is the most important consideration.

7. XFS is most famously used in Red Hat distributions (Red Hat Enterprise Linux, CentOS, and Fedora). It contains some features that are more advanced than ext4, such as parallel I/O, larger file size support, and better handling of large files.

8. Finally, there is Btrfs. This filesystem implementation was initially designed at Oracle and is considered stable as of 2014. Btrfs has many advanced features that could make it preferable to ext4 and XFS; the principal developer of ext4 even stated that ext4 should eventually be replaced by Btrfs. The most interesting feature of Btrfs is that it uses the copy-on-write (COW) principle: files that are copied aren't actually written out to the physical medium fully, but only a new pointer to the same data is created. Only when either the copy or the original gets modified is new data written.

9. Another interesting thing to note is that, while ext4 is native to Linux, with the help of drivers it can be used under, for example, Windows as well. You would not use ext4 as the filesystem for the primary drive under Windows, but you could mount a Linux-formatted ext4 filesystem under Windows and interact with the contents. The other way around, mounting a Windows filesystem under Linux, is also supported for most implementations. And while we used ext4 as the example here, the same goes for XFS and Btrfs.

### Everything is a file
> On a Linux system, everything is a file; if something is not a file, it is a process.

### Arrays
```linux
reader@ubuntu:~$ array=("This" "is" "an" "array")
reader@ubuntu:~$ echo ${array[0]}
This
reader@ubuntu:~$ echo ${array[1]}
is
reader@ubuntu:~$ echo ${array[2]}
an
reader@ubuntu:~$ echo ${array[3]}
array
```
