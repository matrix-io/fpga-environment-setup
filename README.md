# FPGA Programming Environment Setup
How to set up the Xilinx compiler for FPGA code to flash the SPARTAN-6 FPGAs on MATRIX devices.

### For Linux

Click [here](https://www.xilinx.com/registration/sign-in.html?oamProtectedResource=wh%3Dwww.xilinx.com%20wu%3D%2Fmember%2Fforms%2Fdownload%2Fxef.html%3Ffilename%3DXilinx_ISE_DS_Lin_14.7_1015_1.tar%20wo%3D1%20rh%3Dhttps%3A%2F%2Fwww.xilinx.com%20ru%3D%252Fmember%252Fforms%252Fdownload%252Fxef.html%20rq%3Dfilename%253DXilinx_ISE_DS_Lin_14.7_1015_1.tar) to go to the Xilinx website and download the full ISE WebPack installer for Linux.

The above link will prompt you to either log in to your Xilinx account or you will have to create one.

![](/images/sign_in_sign_up.png)

Once you log in, Xilinx will take you to a page where you will have to fill out more information.

If you are a student/professor, you can enter your institution name for the "Company Name" field or just put "ATTN: your name" in the company field.

After filling out all the required fields, click Next.

You will then be prompted to open or save the Xilinx ISE tar file. Make sure to save the file to your desired location on your computer.

Open up a terminal, navigate to the terminal with the .tar file and enter the following command to extract the contents. It's better not to change the file location once you extract the file so make sure you extract it at a file path you want your Xilinx ISE to be.
```bash
sudo tar -xvf Xilinx_ISE_DS_Lin_14.7_1015_1.tar 
```
Input the following commands to navigate into the extracted directory and run the setup executable.

Keep in mind you will need 22GB free space in root for this application.

```bash
cd Xilinx_ISE_DS_Lin_14.7_1015_1
sudo ./xsetup
```
The ISE 14.7 installer UI will open up. Follow the steps in the video below to install ISE with the correct settings.

********INSERT VIDEO********

In your terminal type the following to open the ~/.bashrc file.
```bash
sudo nano ~/.bashrc
```
Scroll to the end of the file and add the following line.
```bash
source /opt/Xilinx/14.7/ISE_DS/settings64.sh 
```
Press Ctrl+X, then Y to save and exit the nano editor.

Close your terminal and open a new one.

When you reopen your terminal, it will look something like this.

![](/images/after_settings64_sourcing.png)

Run the command ise in your terminal to run the application.
```bash
ise
```
An error will pop saying "a license was not found". 

To install the license file, go back to the Xilinx website using [this](https://www.xilinx.com/member/forms/license-form.html) link. 

Once again, you will be prompted to log in. Once you do, it will take you to the page to fill out additional information which should be pre-filled. (**Verify this works on Mozilla**) Click Next.

Select *ISE WebPACK* check box (you will see it says "No Charge") and click on "Generate Node-locked License".

Once the license is generated, you will automatically be routed to the "Manage Licenses" tab. Click on the download button on the bottom left corner of the window. Make sure to download the license or move it into the filepath of your choosing before continuing on.

![](/images/download_license.png)

Go to your ISE Project Navigator, go to Help > Manage License > Load License and select the appropriate license file.

********INSERT VIDEO********

Congratulations, you have set up your Xilinx FPGA compiler on Linux!

[Scroll down](#modify-compile-&-upload-verilog-files) to learn how to mofidy the MATRIX device Verilog files, compile them and flash them to your MATRIX device FPGA.

### For Windows

Click [here](https://www.xilinx.com/registration/sign-in.html?oamProtectedResource=wh%3Dwww.xilinx.com%20wu%3D%2Fmember%2Fforms%2Fdownload%2Fxef.html%3Ffilename%3DXilinx_ISE_S6_Win10_14.7_ISE_VMs_0206_1.zip%20wo%3D1%20rh%3Dhttps%3A%2F%2Fwww.xilinx.com%20ru%3D%252Fmember%252Fforms%252Fdownload%252Fxef.html%20rq%3Dfilename%253DXilinx_ISE_S6_Win10_14.7_ISE_VMs_0206_1.zip) to go to the Xilinx website and download the full ISE WebPack installer for Windows.

The above link will prompt you to either log in to your Xilinx account or you will have to create one.

![](/images/sign_in_sign_up.png)

Once you log in, Xilinx will take you to a page where you will have to fill out more information.

If you are a student/professor, you can enter your institution name for the "Company Name" field or just put "ATTN: your name" in the company field.

After filling out all the required fields, click Next.

You will then be prompted to open or save the Xilinx ISE tar file. Make sure to save the file to your desired location on your computer.

Once downloaded, extract the contents of the file. Enter the extracted folder and run **xsetup.exe** to start the installation process.

The installer is set to download VirtualBox and the Xilinx ISE Virtual Machine on your Windows computer and will prompt you to uninstall VirtualBox for a full re-download through the installer. This is the more straightforward method.

If you already have VirtualBox and are not willing to uninstall it for the Xilinx ISE VM, you can continue with the installation as long as your VirtualBox installation is the same or more recent version than what Xilinx supports.

Follow the directions to continue with the installation. The window below is the most important step.

First, enter the installation directory, this is where your VM will be located.

I would recommend creating the desktop shortcut. It starts the VM and runs the ISE.

The Xilinx ISE VM shares files with your host computer and prompts you to specify the shared file. This is how you will edit files on your host machine and compile them using the Xilinx ISE VM.

![](/images/Xilinx_Windows_Install_1.PNG)

The contents of your shared folder will show up in the Xilinx ISE VM as a drive called ISE_Projects as shown below.

![](/images/Xilinx_Windows_After_Install.PNG)

Congratulations, you have set up your Xilinx FPGA compiler on Windows!

[Scroll down](#modify-compile-&-upload-verilog-files) to learn how to mofidy the MATRIX device Verilog files, compile them and flash them to your MATRIX device FPGA.

### For Mac

This is not officially supported by Xilinx but the Windows method can be slightly modified to work with Mac.

First download and install the OS X version of [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

Click [here](https://www.xilinx.com/registration/sign-in.html?oamProtectedResource=wh%3Dwww.xilinx.com%20wu%3D%2Fmember%2Fforms%2Fdownload%2Fxef.html%3Ffilename%3DXilinx_ISE_S6_Win10_14.7_ISE_VMs_0206_1.zip%20wo%3D1%20rh%3Dhttps%3A%2F%2Fwww.xilinx.com%20ru%3D%252Fmember%252Fforms%252Fdownload%252Fxef.html%20rq%3Dfilename%253DXilinx_ISE_S6_Win10_14.7_ISE_VMs_0206_1.zip) to go to the Xilinx website and download the full ISE WebPack installer for Windows (yes Windows, we will mod slightly to make it work with Mac).

The above link will prompt you to either log in to your Xilinx account or you will have to create one.

![](/images/sign_in_sign_up.png)

Once you log in, Xilinx will take you to a page where you will have to fill out more information.

If you are a student/professor, you can enter your institution name for the "Company Name" field or just put "ATTN: your name" in the company field.

After filling out all the required fields, click Next.

You will then be prompted to open or save the Xilinx ISE tar file. Make sure to save the file to your desired location on your computer.

Once downloaded, extract the contents of the file.

Then, open VirtualBox and follow the directions below.

### Modify, Compile & Upload Verilog Files

#### MATRIX Creator

To modify the MATRIX Creator FPGA code, type the following commands in your computer's terminal (For Windows use Windows Power Shell, Git Bash or Putty, and make sure to clone the repo into the shared file path with the Xilinx ISE VM).
```bash
git clone https://github.com/matrix-io/matrix-creator-fpga.git
```
If git is not installed on your computer, type the following commands to install it.
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```
You can then navigate to matrix-creator-fpga > creator-core and edit the Verilog files as desired.

To compile the modified FPGA code, open your terminal, navigate to the matrix-creator-fpga > creator-core directory and run the command
```bash
make
```
This should create a system.bit file. 

> Be advised that this file will not have mic DSP since that IP has not been made public yet.

To flash the system.bit file onto your FPGA, follow the instructions in the documentation [here](https://matrix-io.github.io/matrix-documentation/matrix-creator/resources/fpga/).

#### MATRIX Voice

To modify MATRIX Voice FPGA code, type the following commands in your computer's terminal.
```bash
git clone https://github.com/matrix-io/matrix-voice-fpga.git
```
If git is not installed on your computer, type the following commands to install it.
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git 
```
You can then navigate to matrix-voice-fpga > voice-core and edit the Verilog files as desired.

To compile the modified FPGA code, open your terminal, navigate to the matrix-voice-fpga > voice-core directory and run the command
```bash
make
```
This should create a system.bit file. 

> Be advised that this file will not have mic DSP since that IP has not been made public yet.

To flash the system.bit file onto your FPGA, follow the instructions in the documentation [here](https://matrix-io.github.io/matrix-documentation/matrix-voice/resources/fpga/).

Scroll down for [General Comments](#general-comments).

#### General Comments
You can use a text editor of your choice to edit the Verilog files. I prefer to use [Visual Studio Code](https://code.visualstudio.com/) in which you can install extensions to color code your files.

To upload the system.bit file:
1) You can use [Cyberduck](https://cyberduck.io/) (available on Windows and Mac) to SFTP into your Raspberry Pi, and upload the system.bit file.

2) For Linux, you can mount your Raspberry Pi as a network drive using SFTP.

> Remember that you will have to upload the system.bit file to the /home/pi directory and then move it to the appropriate location to be flashed via the terminal using the sudo command.
