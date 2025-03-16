# Операционные системы UNIX/Linux (Базовый)
Установка и обновления системы Linux. Основы администрирования.

## 1) Установка ОС
* Установили VirtualBox и создали новую виртуальною машину с операционной системой Ubuntu 20.04 Server LTS.
###### Рисунок 1 - Созданная в VBox виртуальная машина
![image](https://github.com/user-attachments/assets/bf4a7953-d0d0-4e56-8726-ff8edf06f4d1)
* На ВМ отсутствует графический интерфейс.
###### Рисунок 2 - Терминал виртуальной машины
![image](https://github.com/user-attachments/assets/d34072ce-6595-4474-8c01-7d0c0820a13a)
* Вводим команду ``cat /etc/issue``, чтобы проверить текущую версию ОС.
###### Рисунок 3 - Вывод команды ``cat /etc/issue``
![image](https://github.com/user-attachments/assets/cfb452d9-d8a3-4eb5-8638-60f23485cdc8)
* На скриншоте видно, что сейчас установлена версия ОС 20.04.6 LTS.

## 2) Создание пользователя
* Командой ``useradd alex`` создем нового пользователя ``alex``.
###### Рисунок 4 - Выполнение команды ``useradd alex``
![image](https://github.com/user-attachments/assets/f3b03ceb-02a2-4d55-aa90-3a480b7da999)
* Комнадой ``usermod -aG adm alex`` добавляем пользователя ``alex`` в группу adm.
  - Флаг -a - добавление пользователя в группу
  - Флаг -G - указание группы, куда добавлять
###### Рисунок 5 - Добавление пользователя в группу
![image](https://github.com/user-attachments/assets/35814048-bf9a-470e-93c3-0766ae9bae3e)
* Командой ``cat /etc/passwd | grep "alex"`` проверяем появилась ли инфорамция о новом пользователе в системе.
###### Рисунок 6 - Поиск информации о новом пользователе в файле ``/etc/passwd``
![image](https://github.com/user-attachments/assets/8b8beaf3-58b0-4464-ab13-81839620b713)
* Информация о пользователе отображается:
  - Имя пользователя: alex
  - Пароль: x, потому что в зашифрованном виде хранится
  - Идентификатор пользователя: 1002
  - Идетификатор группы: 1002
  - Путь до пользовательского каталога
  - Вход в командную оболочку

## 3) Настройка сети ОС
* Изменяем название машины на ``user-1`` утилитой ``hostamectl``.
###### Рисунок 7 - Изменение имени хоста на ``user-1``
![image](https://github.com/user-attachments/assets/ac1b64d9-0b0c-48aa-b682-5deb723e6edf)
* Используя утилиту ``timedatectl`` устанавливаем Московское время.
###### Рисунок 8 - Устанавка временной зоны ``Europe/Moscow``
![image](https://github.com/user-attachments/assets/bfb88f40-ce63-48ef-86a3-5d73e768e9c1)
###### Рисунок 9 - Вывод текущего времени командой ``date``
![image](https://github.com/user-attachments/assets/920c7b19-29db-4843-8035-1eac93e219e3)
* Команда ``ip a`` выводит список сетевых интерфейсов
###### Рисунок 10 - Список сетевых интерфейсов
![image](https://github.com/user-attachments/assets/5ade1583-d2cf-4ae5-b953-c19509b0f0ba)
* Loopback - логический интерфейс для взаимодействия устройства с самим собой.
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

## 4) OS Update
* Update the system packages to the latest version

![image](https://github.com/user-attachments/assets/e4a86514-b105-4c0b-a90f-bdd21fd011fc)

* After updating the system packages, if you enter the update command again, a message should appear saying there are no updates;

![image](https://github.com/user-attachments/assets/4327563c-5875-4211-9b1a-8d735b683a12)

* Теперь версия убунты

![image](https://github.com/user-attachments/assets/01a9ad4f-f933-43e3-86a5-c96be5d49f8a)

## 5) Using the sudo command
* Открываем файл etc/sudoers.tpm командой ``sudo visudo``

![image](https://github.com/user-attachments/assets/1157f0ff-1938-4559-9507-379552dca537

* Редактируем файл так, чтобы ``alex`` мог использовать команду ``sudo``

![image](https://github.com/user-attachments/assets/ff213c52-8193-4606-a2f8-ecd551cbd18e)

* In the report explain the true purpose of sudo command (don’t write about the fact that this word is "magic" one);
* Переходим в командную оболочку пользователя ``alex``

![image](https://github.com/user-attachments/assets/a2b4c075-d9da-44a7-b69b-8c20b96097d5)

* Change the OS hostname via the user created in Part 2 (using sudo);

![image](https://github.com/user-attachments/assets/011172e6-319e-482f-8b43-204f0e8b4690)

* Просматриваем изменения

![image](https://github.com/user-attachments/assets/1001b493-26de-461e-b9f0-c0ea8cb72b33)

## 6) Installing and configuring the time service
* Output the time of the time zone in which you are currently located.


![image](https://github.com/user-attachments/assets/ffafe882-2e3e-456a-b47c-6b797ba1e1ce)

* The output of the following command must contain NTPSynchronized=yes: 
timedatectl show

![image](https://github.com/user-attachments/assets/b05d19e4-93ba-42f9-b7a1-c0bff6c3d3f4)

## 7) Installing and using text editors
* JOE установлен

![image](https://github.com/user-attachments/assets/504e39b1-2e94-4a45-af21-111b6038f462)

* vim установлен

![image](https://github.com/user-attachments/assets/62e8f53d-ac3a-4fee-b1af-4ac68b6bc076)

* nano устанволен

![image](https://github.com/user-attachments/assets/4ad0e366-f7ae-46d6-b58d-80c5f13fd58b)

### Выйти с сохранением изменений
* файл test_vim.txt

![image](https://github.com/user-attachments/assets/20c36dff-b05b-4bac-8dec-3e8ede1066ac)

:wq
* файл test_nano.txt

![image](https://github.com/user-attachments/assets/03b2cd4f-8852-4c75-9b55-63f9e4de66fc)

Ctrl+X -> y -> Enter
* файл test_joe.txt

![image](https://github.com/user-attachments/assets/94113c08-d1a7-4c29-81a5-7e477b9cea5b)

Ctrl+K X -> Ctrl+K D -> y

### Выйти без сохранения изменений
* файл test_vim.txt
![image](https://github.com/user-attachments/assets/18cccb38-d816-4941-ab30-726115da9a02)

без сохранения :q!
* файл test_nano.txt
![image](https://github.com/user-attachments/assets/3fb121b2-3ab5-42d3-937d-35ca6514340e)

Ctrl+X -> n
* файл test_joe.txt

![image](https://github.com/user-attachments/assets/9a1c55f4-8040-430b-a758-740f0118017a)

Ctrl+C -> y

### Поиск слова и редактирование 
* файл test_vim.txt
- Поиск слова School

![image](https://github.com/user-attachments/assets/aed9ea7e-e35b-441b-a390-d9b3c8883b70)

- Замена School на sarirunc

![image](https://github.com/user-attachments/assets/aa056800-0c32-44ac-af5b-1f2d6bfcedc0)

* файл test_nano.txt
- Поиск слова School (Ctrl + W)

![image](https://github.com/user-attachments/assets/fd07876b-e815-4d41-a617-a2e35b66eac8)

- Замена School на sarirunc

![image](https://github.com/user-attachments/assets/463d0bba-ec81-4cf1-8d4f-2bf74ac646c9)
![image](https://github.com/user-attachments/assets/adedd06d-a2bd-4b07-8279-9839fda38c0d)
![image](https://github.com/user-attachments/assets/aa5c6ae3-855a-4e8e-969d-b5a21a0c03c7)

* файл test_joe.txt
Поиск и замена Ctrl+K F
- Поиск

![image](https://github.com/user-attachments/assets/5bda2f48-5832-48e2-ac31-7b6ccb1dfba7)

- Замена
## 8) Installing and basic setup of the SSHD service
* Install the SSHd service.

![image](https://github.com/user-attachments/assets/17efdffd-e71c-4dc9-be7f-b07b8ed96876)

* Add an auto-start of the service whenever the system boots.

![image](https://github.com/user-attachments/assets/52b8dc6f-b364-4f1a-b8f4-a9c5261088a3)

* Reset the SSHd service to port 2022.

![image](https://github.com/user-attachments/assets/3c67db6a-360a-468e-ae67-d3e278b64eb5)

* Show the presence of the sshd process using the ps command. To do this, you need to match the keys to the command.

Explain in the report the meaning of the command and each key in it.

![image](https://github.com/user-attachments/assets/22f35715-ca85-4034-8e49-9643d38688a1)

## 9) Installing and using the top, htop utilities
* Install and run the top and htop utilities.

![image](https://github.com/user-attachments/assets/ea901a6c-b8ae-4030-8539-83cfdd443f2a)

From the output of the top command determine and write in the report:

uptime
number of authorised users
average system load
total number of processes
cpu load
memory load
pid of the process with the highest memory usage
pid of the process taking the most CPU time

* sorted by PID, PERCENT_CPU, PERCENT_MEM, TIME

![image](https://github.com/user-attachments/assets/a4fbcda2-8d1e-42e5-8fcb-6e089d897226)
![image](https://github.com/user-attachments/assets/fdf80309-cb8e-4500-80e1-9770747b0a2f)
![image](https://github.com/user-attachments/assets/4298f41e-95c8-4281-83ce-f6e415975fc9)
![image](https://github.com/user-attachments/assets/5a28142a-5bd3-4074-b010-7c1da4d64037)

* filtered for sshd process

![image](https://github.com/user-attachments/assets/2c6c078a-4092-4b1d-bdd5-760d69434d18)

* with the syslog process found by searching

![image](https://github.com/user-attachments/assets/4c6ee401-3ff2-460e-bd9f-fdd2c14d04c7)

* with hostname, clock and uptime output added

![image](https://github.com/user-attachments/assets/30e39c0f-9893-44de-8cdb-97790e9535e0)

## 10) Using the fdisk utility
"Now let's figure out how to get information about your hard disk. Especially for you I've put together a couple of examples of how to use the fdisk utility."
== Task ==

Run the fdisk -l command.

![image](https://github.com/user-attachments/assets/8578f453-f763-4848-84ff-0919b46104ae)

In the report write the name of the hard disk, its capacity and number of sectors, and also the swap size.


## 11) Using the df utility
Run the df command.

![image](https://github.com/user-attachments/assets/4a5478ea-0aa2-4eb5-a105-0501e726f1f0)

In the report write for the root partition (/):

partition size
space used
space free
percentage used


Determine and write the measurement unit in the report.


Run the df -Th command.

![image](https://github.com/user-attachments/assets/6171a0cf-9309-4ce7-89ec-c23d3c3887bb)

In the report write for the root partition (/):

partition size
space used
space free
percentage used


Determine and write the file system type for the partition in the report.


## 12) Using the du utility
* Output the size of the /home, /var, /var/log folders (in bytes, in human readable format)

![image](https://github.com/user-attachments/assets/e211c827-8ccd-4d99-9b96-2c6a7c1c1e64)
![image](https://github.com/user-attachments/assets/fe0bdbfc-98fe-4a2f-ae4a-8e4f204cb517)
![image](https://github.com/user-attachments/assets/c41a79af-920a-4e40-811c-f2e8d6a22182)

* Output the size of all contents in /var/log (not the total, but each nested element using *)

![image](https://github.com/user-attachments/assets/24c4a711-22d6-46a9-872c-886e828f9cf5)

Add screenshots with the output of all used commands to the report.


## 13) Installing and using the ncdu utility

* Install the ncdu utility.

* Output the size of the /home, /var, /var/log folders.

![image](https://github.com/user-attachments/assets/e2e62a4f-79b1-403f-8161-744086fbf8e2)
![image](https://github.com/user-attachments/assets/5917275f-f11e-4775-8dcd-43015315528c)
![image](https://github.com/user-attachments/assets/0830d360-48c9-4bc7-8c76-7d8b26c045e5)

The size should be approximately the same as in Part 12;

## 14) Working with system logs

Open for viewing:

1. /var/log/dmesg

2. /var/log/syslog

3. /var/log/auth.log

Write the last successful login time, user name and login method in the report;

![image](https://github.com/user-attachments/assets/623e3877-7c98-49e0-bd1d-0e581879f58a)
![image](https://github.com/user-attachments/assets/0b9236ae-5ed1-497f-a7a2-d0b84b690118)

Restart SSHd service;
Add a screenshot of the service restart message to the report (search for it in the logs).
![image](https://github.com/user-attachments/assets/b8cd1c91-64cf-4752-9e86-aa2a9c79bcdf)


## 15) Using the CRON job scheduler

Using the job scheduler, run the uptime command in every 2 minutes.

![image](https://github.com/user-attachments/assets/9548a8b3-2313-43a4-9b77-bc394f69ecef)

Find lines in the system logs (at least two within a given time range) about the execution;

![image](https://github.com/user-attachments/assets/d1d3f767-a2c0-4bab-aead-1721b4540029)
![image](https://github.com/user-attachments/assets/4331be38-adcb-44a2-9267-847de95deb7e)

Display a list of current jobs for CRON;

![image](https://github.com/user-attachments/assets/616b250f-356f-45eb-b988-a547df608835)

Remove all tasks from the job scheduler.

![image](https://github.com/user-attachments/assets/7d467b06-6865-460c-b831-8d52accda070)

![image](https://github.com/user-attachments/assets/8d3c2272-2319-4fe7-a641-5e9df71f979b)

