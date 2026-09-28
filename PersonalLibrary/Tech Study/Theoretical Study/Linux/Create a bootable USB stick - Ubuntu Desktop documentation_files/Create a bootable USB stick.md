[web link](https://documentation.ubuntu.com/desktop/en/latest/how-to/create-a-bootable-usb-stick/)

# Create a bootable USB stick

> You can convert your USB stick (USB flash drive) into Ubuntu installation media. This is different from copying a file to the USB stick. Instead, use a specialized application to rewrite your USB stick with Ubuntu. Select an application depending on the system that you're currently using.
> 
> With a bootable Ubuntu USB stick, you can:
> 
> - Install or upgrade Ubuntu
> - Test out the Ubuntu Desktop experience without touching your PC configuration
> - Boot into Ubuntu on a borrowed machine
> - Use tools from the USB stick to repair or fix a broken configuration
> 
> You need:
> 
> - An 8GB USB stick or larger.

> [!alert] **Warning**
> Back up your files on the USB stick. This process will overwrite and destroy all data stored there

> - An Ubuntu image file. See [Download Ubuntu Desktop](https://ubuntu.com/download/desktop).
> 
> Take note of where your browser saves the downloaded file. This is normally a directory called *Downloads*. Don't download the ISO image directly to the USB stick.
> 
> Proceed only when the download has successfully finished.

### On Windows

> On Microsoft Windows, you have to install a third-party application for writing images to USB sticks.

##### Using Rufus

> You can create a bootable USB stick using [Rufus](https://rufus.ie/), a FOS USB stick writing tool.
> 
> 1. Download and install the latest version of Rufus from the [rufus.ie](https://rufus.ie/) website.
>    If you're using Windows 7, install version 3.22 of Rufus. On Windows XP or Vista, install version 2.18.
> 2. Launch Rufus. If prompted, allow online updates.

> [!question] **Note**
> Rufus presents many options in its interface. It's safe to leave most of them with their default values.

> 3. Insert your USB stick. It appears in the Device field.
>    if Device shows the wrong USB device, select the correct one from the drop-down menu.
> ![[Pasted image 20260317121841.png]]
> 4. Click *select* next to *Boot selection*. Choose the Ubuntu image file that you've downloaded and confirm by clicking *Open*
>    
>    If the button reads *DOWNLOAD* instead, click the dropdown and change it to *SELECT* first.
>    ![[Pasted image 20260317122335.png]]

> 5. If you've already tried Rufus and the USB stick failed to boot on your system, change *Partitioning scheme* to *GPT* and check that *Target system* is set to *UEFI (non CSM)*. This works on modern systems that disable legacy compatibility.
> 6. Click *START* to write the image to USB.
> 7. Rufus tells you that the Ubuntu image is an *ISOHybrid image.* This means that the same image file can be used as the source for both a USB stick and a DVD.
>    
>    Confirm the *Write in ISO Image mode* option.
>    ![[Pasted image 20260317122604.png]]

> 8. If Rufus asks to download additional files to complete writing the image, select *Yes* to continue.
> 9. Rufus warns you that all data on the USB device is about to be destroyed. Double-check that you've selected the correct device and confirm by clicking *OK*.
>    ![[Pasted image 20260317123944.png]]

> 10. Rufus is now writing the image to USB. This usually takes around 10 minutes.
>  ![[Pasted image 20260317124011.png]]

> 11. When Rufus has finished writing to the USB device, the status bar says *READY*.
>  Click *CLOSE* to complete the write process.
>  ![[Pasted image 20260317124049.png]]
