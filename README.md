# mssp4

## This repository is a collection of kernels and libs for the Microsoft Surface Pro 4. It's mainly for myself and this README will serve as a notes area for what is and is not working.

### adra_kernel
This is a pre-compiled kernel referenced in this reddit https://www.reddit.com/r/SurfaceLinux/comments/4vbzki/androidx86_with_the_new_ipts_driver/?sort=old. I believe it is based off of this github repository https://github.com/ipts-linux-org/ipts-linux. It is said to have touchscreen support, wifi fix and lid patches.

#### Working
* Touchscreen with fingers and pen (When paired)
   * Touchscreen needs setup with windows binaries. (see bellow)
* Keyboard cover with touchpad

#### Not Working
* Power, and Volume hard buttons
* Cannot resume once lid/keyboard is closed
* Touchpad doesn't work properly if keyboard cover is detached then reattached.
  * "Adds one finger" actions that normally require one finger (including moving cursor) now take 2 fingers. Actions that require 2 fingers now require 3 fingers.

#### Untested
* Wifi fix
* lid patches

### jimdigriz_kernel
This is a kernel I compiled myself. It was cloned from this github repository https://github.com/jimdigriz/ipts-linux.

#### Working
* Touchscreen only with pen (When paired)
  * Touchscreen needs setup with windows binaries. (see bellow)
* Keyboard cover with touchpad
* Power and Volume hard buttons

#### Not Working
* Touchscreen does not work with fingers
* Cannot resume once lid/keyboard is closed
* Touchpad doesn't work properly if keyboard cover is detached then reattached.
  * "Adds one finger" actions that normally require one finger (including moving cursor) now take 2 fingers. Actions that require 2 fingers now require 3 fingers.

#### windows_binaries
These binaries are essential to getting the touchscreen to work.
Copy all of them into /itouch.
Add symbolic links.

sudo ln -s iaPreciseTouchDescriptor.bin /itouch/integ_descriptor.bin

sudo ln -s SurfaceTouchServicingSFTConfigMSHW0078.bin /itouch/integ_sft_cfg_skl.bin

sudo ln -s SurfaceTouchServicingDescriptorMSHW0078.bin /itouch/vendor_descriptor.bin

sudo ln -s SurfaceTouchServicingKernelSKLMSHW0078.bin /itouch/vendor_kernel_skl.bin


### surface_pen
To get the pen working it's best use wacom drivers. Copy all files into /usr/share/X11/xorg.conf.d or /etc/X11/xorg.conf.d. /usr/share/X11/xorg.conf.d may get overwritten during an update. Reference https://m.reddit.com/r/SurfaceLinux/comments/422la9/sp3_help_getting_pen_input_to_work_properly/.

#### Working
* Pressure sensitivity
* Eraser
* Side button hold and tap for right click

#### Not Working
* Eraser button
