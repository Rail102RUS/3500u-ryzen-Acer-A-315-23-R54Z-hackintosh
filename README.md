# Acer-Aspire_3_A315-23-R54Z-ryzen3500u-hackintosh



An OpenCore config for Acer-Aspire A315-23-R54Z 2023 (Ryzen Edition)

OpenCore version: 0.9.9

macOS: 11.6.6

## SPECS:
- LAPTOP: Acer-Aspire A315-23-R54Z
- CPU: AMD Ryzen 5 3500U
- Display: AMD Radeon Vega 8 (Working on VRAM 2GB)
- Network: Intel wireless 8265 / 8275
- Hard-disk: Samsung M.2 SSD 970Evo Plus 1TB
- RAM: 24GB (8GB soldered + 16GB in slot)
- ALC255

Please change MLB/ROM/Serial Number/UUID.

### What is working

- Graphic Acceleration (using NootedRed.kext)

* CPU Monitoring (using AMD Power Gadget app)

* Network

* Bluetooth

* Battery Status

* Audio (AppleALC layout-id=69)

### What is not working

* Hibernation
* Front Camera (connected to XHC, which is disabled)
* USB (still in the works)

## Installation instructions:

* https://4pda.to/forum/index.php?showtopic=84979&view=findpost&p=117964707

Download Mac OS Big Sur 11.6.6 (20G624)
* https://4pda.to/forum/index.php?showtopic=997068&view=findpost&p=114948379

Recovery from the image of the pre-installed system, with regard only to what I posted - svk (c6h6 on applelife).
I am not responsible for the other (and there is another):
First of all, what is it for? This was originally invented when it was impossible to install "from scratch" (as well as upgrade) macos systems such as Bigsure and newer, on hardware without nvram hardware support (this is not necessarily only legacy bios, it is also possible on uefi). Now there are ways to circumvent this restriction, whoever needs it will find it. Well, also, restoring from an image is just faster (if you don't blunt and do everything right) than reinstalling the system.

My images are a preset axis, before the user account is created. Root partition encryption (snapshot) is disabled in my images. You can restore both without a snapshot (then you can do "sudo mount -uw /" in the system, with all the consequences) and with a snapshot. The recovery must take place either from the system or in a recovery environment, in an axis not lower than the Catalina. Earlier axes have other versions of apfs, and will not work correctly with Bigs images.

To restore with a snapshot, you first need to find out the name of the snapshot:
We mount the image into the system, either stupidly by double-clicking, or in the terminal "sudo hdiutil attach the path of the image". Next, run the "diskutil list".
We look at where we have the system volume in the image, not the name of the volume-data, but just the name of the volume. We execute "diskutil apfs listSnapshots diskXsY", where diskXsY is the address of the domain name. We get the name of the snapshot.
Next, run "sudo asr restore --source path_image --target disk name or volume name --toSnapshot snapshot name --erase"

It is also possible that before loading a new axis, you will have to reset nvram if it either works for you or emulates it.
And also - there will be no delta updates on the axis without a snapshot. If you want everything to be regular, unfold it with a snapshot. And if you plan to use OCLP (for a factory, for example, ancient graphics), then too - deploy only with a snapshot.

Useful things actually, these preset axes...

### Credits

* https://github.com/GaisaiYuno/magicbook2019-ryzen3500u-hackintosh

* Apple for macOS

* https://github.com/pondsmile/EFI-Lenovo-Ideapad-C340-Hackintosh

* https://github.com/NootInc/NootedRed




