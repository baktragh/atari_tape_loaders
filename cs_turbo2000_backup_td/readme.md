# Backup T/D

## About

Backup T/D is a Turbo 2000 tape preservation toolkit for 8-bit Atari computers.

## Components
The toolkit consists of two components:

1. Backup T/D utility disk
2. Backup T/D extractor 

## Backup T/D Utility Disk

### Overview

The utility disk is a special, large bootable disk without a filesystem.
The disk provides the following functions:

1. List files present on the utility disk.
2. Backup tape. This function reads Turbo 2000 files from tape and stores them on the utility disk. This is repeated until the
   RESET key is pressed. A full tape side can be preserved automatically.
3. Record tape. This function records all previously backed up files back to tape.

### Notable Features

* The utility disk can backup and record Turbo 2000 files that are up to 65532 bytes long.

### System Requirements

* Atari XL/XE with 128 KB RAM. The extra 64 KB of RAM is required.
* Disk drive replacement/emulator that supports large disk images. Real disk drives will not work, because
  they do not support large disks.
* Data recorder with Turbo 2000 or compatible upgrade
* Data recorder and disk drive emulator/replacement connected simultaneously to the computer.

### Considerations

* The Backup tape function, when started, always overwrites all files on the disk. If the disk is not pristine,
  a warning message is displayed.
* Do not press RESET until a full tape side is backed up
* To exit the utility disk, you can press SHIFT+ESC. This will result in cold start.

## Backup T/D Extractor

The extractor can extract files from the previously populated utility disk. The extractor is a binary load file
that can run under Atari DOS 2 or similar disk operating systems.

The extractor provides the following functions:
1. List files present on the utility disk
2. Extract files from the utility disk and store them as binary load files or flat files.
3. Extract files from the utility disk and store them as tape images (.CAS). Some programs cannot be fully preserved when stored as binary load files or flat files.
4. Controls for setting up the extraction.

### System Requirements

* 8-bit Atari computer with 48 KB RAM
* Disk drive replacement/emulator that supports large disk images (for the utility disk)
* Device to store the extracted files. It can be any device available through CIO. 

### Considerations

* The extracted files are always overwritten without a warning.
* There are no rules for Turbo 2000 file names, while rules for disk file names are strict. The extractor normalizes the file names by replacing characters inappropriate for disk file names.
* The extractor provides a special support for the H: devices provided by emulators. The extracted files are named using long names. Configure the H: device for long name support.
* The Turbo 2000 file names can be up to 10 characters long, while disk file names are limited to 8 characters (except the H: devices, where the file names can be much longer).
* To prevent unwanted file overwrites caused by duplicate file names, use the "Sequential naming" option. The option adds a three-digit prefix to file names extracted to a H: device, or sets a numbered file name extension for other devices.

## How to Backup a Full Tape Side and then Extract the files

### Backup
1. Create a working copy of the BACKUP T/D Utility disk image
2. Insert the disk image to the emulated drive #1. Ensure the disk image is inserted as read-write.
3. Boot from the disk image
4. Connect the data recorder, insert tape
5. Select the "Backup tape" function
6. Press PLAY and then press START
7. Observe the messages, and then wait until the full tape side is backed up. Then press RESET to return to the main menu.
8. Select the "List files on disk" function to review what files have been backed up.
8. Eject the disk image from the emulated drive.

### Extraction Using Emulator
1. Configure the emulator, so that the virtual hard drive device H1: is available. Ensure the H1: device is in read/write mode and supports long file names.
2. Have the emulator launch the BACKUP T/D Extractor binary load file
3. Insert the previously used disk image to emulated drive #1
4. On the main menu, select the "List files on Backup T/D disk" to verify the contents of the disk image
5. Verify that H1 is selected as the target device.
6. On the main menu, select the "Extract files from disk" function to extract the files to the virtual hard drive.