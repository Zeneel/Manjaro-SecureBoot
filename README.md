# Manjaro SecureBoot / the easier way
Setup secure boot for Manjaro (Arch) using 'sbctl' to enable dual boot with Windows 11 bitlocker encrypted OS

## Steps
1. In UEFI BIOS disable secureboot and clear out the enrolled keys 

- https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Putting_firmware_in_%22Setup_Mode%22


2. Create and Enroll secureboot keys using 'sbctl'

- https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Creating_and_enrolling_keys


3. Sign the EFI boot loader and kernel images

- https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Signing

    - Then verify, e.g.:

        sudo sbctl verify

        >Verifying file database and EFI images in /boot/efi...

        >✓ /boot/efi/EFI/Boot/bootx64.efi is signed

        >✓ /boot/efi/EFI/Manjaro/grubx64.efi is signed

        >✓ /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi is signed

        >✓ /boot/efi/EFI/Microsoft/Boot/bootmgr.efi is signed

        >✓ /boot/efi/EFI/Microsoft/Boot/memtest.efi is signed

        >✓ /boot/vmlinuz-6.1-x86_64 is signed

        >✓ /boot/vmlinuz-6.5-x86_64 is signed



4. Install Pacman hook to automatically update linux kernel, systemd or the boot loader when required

- https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Automatic_signing_with_the_pacman_hook

    - e.g.

        sudo sbctl verify

        >✓ /usr/lib/systemd/boot/efi/systemd-bootx64.efi.signed is signed

5. Reboot into UEFI BIOS and enable secureboot
6. DONE
