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

**Commandns to download and compil the RTL-SDR v4-compatibele version:**

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





