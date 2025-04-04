# File systems

File systems are standards for organizing data on a hard drive, SSD, or storage device.
File system is applied when you format a drive or partition.

## Description

File systems divide a storage space on a drive into virtual compartments known as
clusters and maintain an index of where individual files are located and available free
space

## FAT12, FAT16 & FAT32

FAT stands for File Allocation Table.

FAT was the first Dot and Windows file system.

It has three major variants:

* FAT12
* FAT16
* FAT32

Each can divide a drive into an increasing number of clusters and has maximum file and
volume sizes.

|       | Max file size                                  | Max volume size                                         |
|-------|------------------------------------------------|---------------------------------------------------------|
| FAT12 | 32MB (8KB clusters) or 16MB (4KB clusters)     | 32MB (8KB clusters) or 16MB (4KB clusters)              |
| FAT16 | 2GB / 4GB (depending on cluster & sector size) | to 16GB (depending on cluster & sector size)            |
| FAT32 | 4GB                                            | 32GB (Windows format) 2TB (other OS) 16TB (theoretical) |

FAT32 remains popular due to wide OS compatibility. It still widely used to format
removable media such as USB flash drives, memory cards and other external storage
devices.

## NTFS

NTFS - New Technology File System. Today's most popular Windows file system.

It was introduced in 1993 to overcome the limitations of FAT32.

File size limit 16EB (1 exabyte = 1 000 000 TB). It means that in practice there is no
file size constraint.

NTFS is journaling file system. This means that it maintains a record of changes. So it
can recover following the system crash or power failure.

NTFS supports file permissions and encryption. For example allowing a file to be flagged
as read-only.

All modern Windows system are installed on NTFS formatted drive.

Only real downside of NTFS is a lack of compatibility with non Windows operating
systems. For example by default NTFS volumes are read-only in macOS and in older Linux
distros and may be not readable at all on other devices such as standalone media
players.

## exFAT

exFAT - Extended file allocation table.

Was introduced by Microsoft in 2006 as a file system optimized for high-capacity USB
flash drives and memory cards.

Maximum file size: 16EB.

exFAT is the best choice for formatting memory cards for recording video. It is a
default file system for SDXC cards.

Has broader non-Windows OS support than NTFS including read and write support on macOS
and recent versions of Android. Many Linux systems require extra drivers to be install
to access exFAT devices.

## ext2, ext3 & ext4

ext - Extended File System. Was launched for Linux in 1992.

ext2 was released in 1993 and was the default file system in many Linux distros.

In 2001 ext2 was upgraded to ext3. ext3 supports journaling to protect against
corruption in the event of crushes or power failures.

In 2008 ext4 was released and became the Linux default file system.

Maximum file size: 16TB

Maximum volume size: 1EB

ext has no native Windows or macOS support.

## HFS, HFS+ & APFS

HFS - Hierarchical file system for macOS. Was introduced by Apple in 1985. It is also
known as macOS standard.

Maximum file size: 2GB.

Maximum volume size: 2TB.

In 1998 HFS was upgraded to a new version called HFS+ or HFS extended otherwise known as
macOS extended. This file system added journaling.

Maximum file and volume size up to 8EB (macOS 10.4 or above).

In 2017 APFS (Apple file system) was introduced. It is optimized for SSD and other solid
state media.

These file system have no native non-Apple OS support.

## ZFS

ZFS - Zed File System.

It was released in 2006 by Sun Microsystems. Since 2013 has been developed by the
OpenZFS Project.

ZFS differs from other file systems because it integrates a volume manager to control
the storage hardware attached to a computer. By integrating physical drive management
with file system functionality ZFS provides increased protection against data loss or
corruption.

ZFS is available for Linux, FreeBSD and TrueOS.

## Advice for choosing file system

For your system drive you should or must choose the file system for your operating
system. NTFS for Windows, ext4 for Linux distro and HFS+ or APFS on Mac.

For USB drives and memory cards below 32 gigabytes in capacity use FAT32 in order to
maximize compatibility across platforms.

exFAT is the best choice for 32Gb+ in capacity USB drives or memory cards, or for 4Gb+
files.

For other drives such as external drives use NTFS for sharing files between Windows,
exFAT for sharing files PC and Mac or FAT32 (but remember about file size and volume
size limitations).
