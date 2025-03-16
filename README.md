## Installation of the OS
* Used VirtualBox to install Ubuntu 20.04 Server LTS without GUI.
* Checked Ubuntu version by running the command ``cat /etc/issue``.
* You can see the result in the Screenshot below.

![image](https://github.com/user-attachments/assets/cfb452d9-d8a3-4eb5-8638-60f23485cdc8)

## Creating a user
* Created user``alex`` - a user other than the one created during installation. The result is below.

![image](https://github.com/user-attachments/assets/f3b03ceb-02a2-4d55-aa90-3a480b7da999)

* Added ``alex`` to adm group. You can see the command in the Screenshot below.

![image](https://github.com/user-attachments/assets/35814048-bf9a-470e-93c3-0766ae9bae3e)

* Checked the user existance by running the command ``cat /etc/passwd``. The ``alex`` is in the output.

![image](https://github.com/user-attachments/assets/8b8beaf3-58b0-4464-ab13-81839620b713)

## Setting up the OS network
* Set the machine name as user-1

![image](https://github.com/user-attachments/assets/ac1b64d9-0b0c-48aa-b682-5deb723e6edf)

* Set the time zone corresponding to my current location.

![image](https://github.com/user-attachments/assets/bfb88f40-ce63-48ef-86a3-5d73e768e9c1)

* Got current time.

![image](https://github.com/user-attachments/assets/920c7b19-29db-4843-8035-1eac93e219e3)

* Got the names of the network interfaces using ``ip a``.

![image](https://github.com/user-attachments/assets/5ade1583-d2cf-4ae5-b953-c19509b0f0ba)

Loopback интерфейс нужен для взаимодействия устройства с самим собой.

* Got the ip address of the PC from the DHCP server.

![image](https://github.com/user-attachments/assets/d2038a27-0580-4ec7-8b9a-e44c8444442c)

Decode DHCP in the report.

* Defined the external ip address of the gateway (ip).

![image](https://github.com/user-attachments/assets/8a7290d3-5310-442d-9ede-b1daab466a2a)

* Defined the internal IP address of the gateway (gw).

![image](https://github.com/user-attachments/assets/f5e71f06-11ef-434e-b072-fbca6cbcbd92)

* Set static ip, gw, dns settings (use public DNS servers, e.g. 1.1.1.1 or 8.8.8.8).

![image](https://github.com/user-attachments/assets/be231c56-4da5-4b29-9ef3-f6b0d6ac0c75)

* Reboot the virtual machine. Make sure that the static network settings (ip, gw, dns) correspond to those set in the previous point.

![image](https://github.com/user-attachments/assets/bb7da6a8-5fd7-4dee-8822-7d5c6f2a6736)

![image](https://github.com/user-attachments/assets/433c5da8-2cd0-403a-bae3-22dac6cc561d)

* Describe in the report what you have done to complete all seven points (you can do it in text or with screenshots);
* Successfully ping 1.1.1.1 and ya.ru remote hosts and add a screenshot of the output command to the report. There should be "0% packet loss" phrase in command output

![image](https://github.com/user-attachments/assets/7ae8e567-e200-4821-bb93-690adeb42dd1)
![image](https://github.com/user-attachments/assets/65408ba6-68ea-423c-8e4b-c1c876ecd117)

## OS Update
* Update the system packages to the latest version

![image](https://github.com/user-attachments/assets/e4a86514-b105-4c0b-a90f-bdd21fd011fc)

* After updating the system packages, if you enter the update command again, a message should appear saying there are no updates;

![image](https://github.com/user-attachments/assets/4327563c-5875-4211-9b1a-8d735b683a12)

* Теперь версия убунты

![image](https://github.com/user-attachments/assets/01a9ad4f-f933-43e3-86a5-c96be5d49f8a)

## Using the sudo command
* Открываем файл etc/sudoers.tpm командой ``sudo visudo``


![image](https://github.com/user-attachments/assets/1157f0ff-1938-4559-9507-379552dca537

* Редактируем файл так, чтобы ``alex`` мог использовать команду ``sudo``

![image](https://github.com/user-attachments/assets/ff213c52-8193-4606-a2f8-ecd551cbd18e)

* In the report explain the true purpose of sudo command (don’t write about the fact that this word is "magic" one);
* Переходим в командную оболочку пользователя ``alex``

![image](https://github.com/user-attachments/assets/a2b4c075-d9da-44a7-b69b-8c20b96097d5)

* Change the OS hostname via the user created in Part 2 (using sudo);


Add screenshot with changed hostname to the report.

## Installing and configuring the time service
Set up the automatic time synchronisation service.

Output the time of the time zone in which you are currently located.
The output of the following command must contain NTPSynchronized=yes: 
timedatectl show

Add screenshots of the correct time and command output to the report.

## Installing and using text editors
Install VIM text editor (+ any two others if you like NANO, MCEDIT, JOE etc.)

Using each of the three selected editors, create a test_X.txt file, where X is the name of the editor in which the file is created. Write your nickname in it, close the file and save the changes.

Add screenshots to the report:

Of each editor with the contents of the file before closing;


Write down in the report what you have done to exit with the changes saved.


Using each of the three selected editors, open the file for editing, edit the file by replacing the nickname with the "21 School 21" string, close the file without saving the changes.

Add screenshots to the report:

Of each editor with the contents of the file after editing;


Write down in the report what you have done to exit without saving the changes.


Using each of the three selected editors, edit the file again (similar to the previous point) and then master the functions of searching through the contents of a file (a word) and replacing a word with any other one.

Add screenshots to the report:

Of each editor with word search results;
Of each editor with commands entered to replace a word with another.

## Installing and basic setup of the SSHD service
Install the SSHd service.

Add an auto-start of the service whenever the system boots.

Reset the SSHd service to port 2022.

Show the presence of the sshd process using the ps command. To do this, you need to match the keys to the command.

Explain in the report the meaning of the command and each key in it.


Reboot the system.

Describe in the report what you have done to complete all five points (you can do this in text or with screenshots);
The output of the netstat -tan command should contain 
tcp 0 0.0.0.0:2022 0.0.0.0:* LISTEN 
(if there is no netstat command, it needs to be installed);
Add a screenshot of the command output to the report;
Explain the meaning of the -tan keys, the value of each output column, the value 0.0.0.0. in the report.


## Installing and using the top, htop utilities
Install and run the top and htop utilities.

From the output of the top command determine and write in the report:

uptime
number of authorised users
average system load
total number of processes
cpu load
memory load
pid of the process with the highest memory usage
pid of the process taking the most CPU time


Add a screenshot of the htop command output to the report:

sorted by PID, PERCENT_CPU, PERCENT_MEM, TIME
filtered for sshd process
with the syslog process found by searching
with hostname, clock and uptime output added




## Using the fdisk utility
"Now let's figure out how to get information about your hard disk. Especially for you I've put together a couple of examples of how to use the fdisk utility."
== Task ==

Run the fdisk -l command.

In the report write the name of the hard disk, its capacity and number of sectors, and also the swap size.


## Using the df utility
"We got the information about the hard disk, but often it is much more interesting to get information about the disk space, which can be obtained with the df utility."
== Task ==

Run the df command.

In the report write for the root partition (/):

partition size
space used
space free
percentage used


Determine and write the measurement unit in the report.


Run the df -Th command.

In the report write for the root partition (/):

partition size
space used
space free
percentage used


Determine and write the file system type for the partition in the report.


## Using the du utility

Run the du command.

Output the size of the /home, /var, /var/log folders (in bytes, in human readable format)

Output the size of all contents in /var/log (not the total, but each nested element using *)

Add screenshots with the output of all used commands to the report.


## Installing and using the ncdu utility

Install the ncdu utility.

Output the size of the /home, /var, /var/log folders.


The size should be approximately the same as in Part 12;


Add screenshots of the used commands to the report.



## Working with system logs

Open for viewing:

1. /var/log/dmesg

2. /var/log/syslog

3. /var/log/auth.log

Write the last successful login time, user name and login method in the report;
Restart SSHd service;
Add a screenshot of the service restart message to the report (search for it in the logs).


## Using the CRON job scheduler
"Phew, we finally got to the last part of my long narrative. I will now show you the program, which, among other things, noticeably simplifies the periodic invocation of other programs."
== Task ==

Using the job scheduler, run the uptime command in every 2 minutes.

Find lines in the system logs (at least two within a given time range) about the execution;
Display a list of current jobs for CRON;
Add screenshots of the execution lines and the list of current tasks to the report.


Remove all tasks from the job scheduler.

Add a screenshot of the list of current tasks for CRON to the report.
