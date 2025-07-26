# Installing RTL-TCP on your Rasperry Pi
Here you can find the commands used in the BloxyLabs videos about intalling RTL-TCP server on a Raspberry Pi.
<br>
<br>
Check also our YouTube channel for instructions and other related information [YouTube](https://www.youtube.com/@bloxylabs "YouTube").
<br>
If you had fun with the projects, please consider giving us a Super Thanks on YouTube or buying us a [cup of coffee](https://www.buymeacoffee.com/bloxylabs "cupofcoffee").

**Commands to update and upgrade the OS:**

```
sudo apt update
```
```
sudo apt upgrade -y
```


**Command to install the required libraries:**

```
sudo apt install -y git cmake build-essential libusb-1.0-0-dev
```

**Commands to download and compile the RTL-SDR v4-compatibele version:**

```
git clone https://github.com/rtlsdrblog/rtl-sdr-blog.git
```
```
cd rtl-sdr-blog
```
```
mkdir build && cd build
```
```
cmake .. -DDETACH_KERNEL_DRIVER=ON
```
```
make
```
```
sudo make install
```
```
sudo ldconfig
```
**Command to block the default driver so it can't claim our RTL-SDR:**

```
sudo bash -c 'echo "blacklist dvb_usb_rtl28xxu" > /etc/modprobe.d/rtl-sdr-blacklist.conf'
```
Reboot your Pi
```
sudo reboot now
```

**Commands to download and execute the rules to get the permissions to use your RTL-SDR:**

```
wget -O /tmp/rtl-sdr.rules https://raw.githubusercontent.com/keenerd/rtl-sdr/master/rtl-sdr.rules
```
```
sudo mv /tmp/rtl-sdr.rules /etc/udev/rules.d/
```
```
sudo udevadm control --reload-rules
```
```
sudo mv /tmp/rtl-sdr.rules /etc/udev/rules.d/
```
```
sudo udevadm trigger
```
Reboot your PI
```
sudo reboot now
```

**Commands to autostart RTL-TCP server:**

```
sudo nano /etc/systemd/system/rtl_tcp.service
```
Now add the following text to the file

```
[Unit]
Description=RTL-SDR TCP server
After=network.target

[Service]
ExecStart=/usr/local/bin/rtl_tcp -a 0.0.0.0
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
Save the file by using ctrl-x. Next enter the following commands:

```
sudo systemctl daemon-reexec
```
```
sudo systemctl enable rtl_tcp
```
```
sudo systemctl start rtl_tcp
```
You are ready to use your RTL-SDR remotely, just reboot your PI and RTL-TCP will autostart
```
sudo reboot now
```

