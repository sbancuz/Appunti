---
tags:
  - OS
---
Unified Extensible Firmware Interface is a significant evolution from the traditional BIOS that had been the underpinning of PC firmware for decades. It acts as an interface between the systems firmware and the OS. 

One notable improvement is a more versatile and modular environment where the users can extend its capabilities through additional drivers. This is the first thing that gets loaded in RAM from an nvRAM.

For startup, UEFI relies on files that are stored in a dedicated FAT32 partition known as the EFI System Partition. This is where the actual bootloader resides.

The GUID Partition Table (GPT) is a modern disk partitioning system that has emerged as the replacement for the older Master Boot Record (MBR) system. Here are some important points to understand about GPT:
1) GPT Layout
	GPT is located at the beginning of the disk, typically occupying sectors 1 through 33, with sector 0 reserved for a protective MBR. The protective MBR ensures limited backward compatibility by occupying the space which would otherwise be used by a legacy MBR. This way, older systems that do not recognize GPT will not mistakenly interpret the disk as unpartitioned.
2) UEFI and File Systems
	UEFI firmware, which often goes hand in hand with GPT, understands various file systems including Microsoft FAT, which is typically used on EFI System Partitions (ESP) for storing bootloader files. Apple’s version of UEFI also supports HFS+, allowing it to work with disks formatted for macOS.
3) Partition Entries
	Within the GPT, each partition entry holds significant information:
	- The first 16 bytes specify the partition type’s globally unique identifier (GUID), which indicates the type of partition (e.g. Linux filesystem, Windows data partition).
	- The second 16 bytes are a GUID that is unique to that particular partition.

![[GPT.png]]