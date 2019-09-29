# BBB Commands for Electronics Testing
This guide outlines simple scripts for basic electronics testing. This is so the Electronics team can run basic tests of their hardware without a representative from Software.

#### Connect to the BBB
To do the basic testing outlined in the guide, you will need to connect to the BBB. Follow the appropriate steps for Mac or Linux.
**When prompted for the password, enter `spacex`**
##### Linux 
For Linux users, run the following command script to install Git:
```
sudo apt-get install git
```
Clone the repo of scripts:
```
git clone https://github.com/Hyp-ed/electronics_testing.git
```
For Linux users, run the following script to install SSH and Git:
```
./install_ssh.sh
```
Connect to the BBB:
```
./ssh_linux.sh
```

##### Mac
For Mac users, run the following command script to install Git:
```
sudo apt-get install git
```
Clone the repo of scripts:
```
git clone https://github.com/Hyp-ed/electronics_testing.git
```
Connect to the BBB:
```
./ssh_mac.sh
```

Now, you are connect to the BBB.

#### CAN Dump
To monitor all CAN0 traffic, type the following command:
```
hyped@beaglebone:~# candump can0
```
This will print the ID of the CAN message in hex.

**For the following three actions, you will need to enter each command individually**
Feel free to change the GPIO pin number, as long as it follows the available pins outlined in the "Beaglebone Black Pin Kill Map" pdf.
#### GPIO Input
To test whether an electronic device is outputting the correct voltage (3.3V), we set GPIO pin 66 to read in the input signal. The BBB will process this input signal as a 1 if high or 0 if low.
```
hyped@beaglebone:~# sudo -i
root@beaglebone:~# cd sys/class/gpio
root@beaglebone:~# echo 66 > export
root@beaglebone:~# echo in > gpio66/direction
root@beaglebone:~# cat gpio66/value
```
#### GPIO Output: Low
Here, we set GPIO pin 66 to output a low signal.
```
hyped@beaglebone:~# sudo -i
root@beaglebone:~# cd sys/class/gpio
root@beaglebone:~# echo 66 > export
root@beaglebone:~# echo out > gpio66/direction
root@beaglebone:~# echo 0 > gpio66
```
#### GPIO Output: High
Here, we set GPIO pin 66 to output a high signal.
```
hyped@beaglebone:~# sudo -i
root@beaglebone:~# cd sys/class/gpio
root@beaglebone:~# echo 66 > export
root@beaglebone:~# echo out > gpio66/direction
root@beaglebone:~# echo 1 > gpio66
```
