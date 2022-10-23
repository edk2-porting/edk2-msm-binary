# Patched Binaries

This file aims to provide further information about the different patches applied to stock firmware UEFI DXEs. These files are from [SurfaceDuoPkg](https://github.com/WOA-Project/SurfaceDuoPkg) repo.

## Reasoning behind each patch

- DisplayDxe: Panels get deinitialized partially on exit boot services by the stock firmware, it is thus needed to reinitialize them, but due to them being partially deinitialized, running some routines again will break the platform. An MMU Domain is already setup by the previous firmware and gets re-set again, causing a crash.

- UFSDxe: An MMU Domain is already setup by the previous firmware and gets re-set again, causing a crash.

- UsbConfigDxe: Important to get USB to work after exit boot services for KdNet or DeveloperMenu or FFULoader.

- ButtonsDxe: to help navigating menus more easily.

## UFSDxe & DisplayDxe

MMU related setup routine was patched to not recreate already existing MMU domains.

## DisplayDxe

Panel Reset function was patched to not run again.

Exit BootServices routine was patched to not deinitialize the panels.

## UsbConfigDxe

Exit BootServices routine was patched to not deinit USB after exit boot services.