# Операционные системы UNIX/Linux (Базовый)
Установка и обновления системы Linux. Основы администрирования.

## 1) Установка ОС
1. Устанавили VirtualBox и создали новую виртуальною машину с операционной системой **Ubuntu 20.04 Server LTS**.
###### Рисунок 1 - Созданная в VBox виртуальная машина
https://github.com/user-attachments/assets/bf4a7953-d0d0-4e56-8726-ff8edf06f4d1

2. На ВМ отсутствует графический интерфейс.
###### Рисунок 2 - Терминал виртуальной машины
![image](https://github.com/user-attachments/assets/d34072ce-6595-4474-8c01-7d0c0820a13a)

3. Ввели команду ``cat /etc/issue``, чтобы проверить текущую версию ОС.
###### Рисунок 3 - Вывод команды ``cat /etc/issue``
![image](https://github.com/user-attachments/assets/cfb452d9-d8a3-4eb5-8638-60f23485cdc8)

4. На скриншоте видно, что сейчас установлена ОС версии 20.04.6 LTS.

## 2) Создание пользователя
1. Командой ``useradd alex`` создали нового пользователя ``alex``.
###### Рисунок 4 - Выполнение команды ``useradd alex``
![image](https://github.com/user-attachments/assets/f3b03ceb-02a2-4d55-aa90-3a480b7da999)

2. Комнадой ``usermod -aG adm alex`` добавили пользователя ``alex`` в группу ``adm``.
  - Флаг -a - добавление пользователя в группу
  - Флаг -G - указание группы, куда добавлять
###### Рисунок 5 - Добавление пользователя в группу
![image](https://github.com/user-attachments/assets/35814048-bf9a-470e-93c3-0766ae9bae3e)

3. Командой ``cat /etc/passwd | grep "alex"`` проверили появилась ли инфорамция о новой учетной записи.
###### Рисунок 6 - Поиск информации о новой учетной записи в файле ``/etc/passwd``
![image](https://github.com/user-attachments/assets/8b8beaf3-58b0-4464-ab13-81839620b713)

4. Новый пользователь создан

## 3) Настройка сети ОС
1. Изменили название машины на ``user-1`` утилитой ``hostamectl``.
###### Рисунок 7 - Изменение имени хоста на ``user-1``
![image](https://github.com/user-attachments/assets/ac1b64d9-0b0c-48aa-b682-5deb723e6edf)

2. Используя утилиту ``timedatectl`` устанавили Московское время.
###### Рисунок 8 - Устанавка временной зоны ``Europe/Moscow``
![image](https://github.com/user-attachments/assets/bfb88f40-ce63-48ef-86a3-5d73e768e9c1)

3. Проверили, что в системе установлено верное время.
###### Рисунок 9 - Вывод текущего времени командой ``date``
![image](https://github.com/user-attachments/assets/920c7b19-29db-4843-8035-1eac93e219e3)

4. Вывели список всех сетевых интерфейсов командой ``ip a``.
###### Рисунок 10 - Список сетевых интерфейсов
![image](https://github.com/user-attachments/assets/5ade1583-d2cf-4ae5-b953-c19509b0f0ba)

5. Первым в списке отображается Loopback-интерфейс. Это сетевой интерфейс, который позволяет операционной системе устанавливать связи между процессами на одном ПК.
6. В системных логах посмотрели ip-адрес, который ВМ получает от DHCP-сервера Vbox. В нашем случае это 10.0.2.15.
###### Рисунок 11 - Записи syslog о dhcp
![image](https://github.com/user-attachments/assets/d2038a27-0580-4ec7-8b9a-e44c8444442c)

7. DHCP(Dynamic Host Configuration Protocol) - сетевой протокол, позволяющий автоматически назначать устройствам в сети конфигурацию(в том числе и ip-адреса).
###### Рисунок 12 - Просмотр внешнего ip-адреса
![image](https://github.com/user-attachments/assets/8a7290d3-5310-442d-9ede-b1daab466a2a)
###### Рисунок 13 - Просмотр шлюза по умолчанию
![image](https://github.com/user-attachments/assets/f5e71f06-11ef-434e-b072-fbca6cbcbd92)

8. Чтобы задать статические настройки, изменили сетевой адаптер ВМ с NAT на bridged. Bridged-адаптер дает ВМ возможность получать ip-адрес из локальной сети.
9. Затем с помощью утилиты ``netplan`` поменяли сетевые настройки
* Шлюз по умолчанию - внутренний адрес роутера: 192.168.0.1
* Адрес машины - статический адрес из локальной сети роутера: 192.168.0.3
* DNS сервера общедоступные: 8.8.8.8, 1.1.1.1
###### Рисунок 14 - Конфигурация netplan
![photo_2025-03-16_11-45-45](https://github.com/user-attachments/assets/39e6014a-377c-4ed6-a31e-820c8f1d3dba)

10. Отправили ``ping`` до адреса 1.1.1.1 и ya.ru
###### Рисунок 15 - ping 1.1.1.1
![image](https://github.com/user-attachments/assets/7ae8e567-e200-4821-bb93-690adeb42dd1)
###### Рисунок 16 - ping ya.ru
![image](https://github.com/user-attachments/assets/65408ba6-68ea-423c-8e4b-c1c876ecd117)

11. Пинги проходят.

## 4) Обновление ОС
1. Обновили ОС
###### Рисунок 17 - Команда для обновления ОС
![image](https://github.com/user-attachments/assets/e4a86514-b105-4c0b-a90f-bdd21fd011fc)

2. Ввели команду еще раз и проверили, что новых версий больше нет.
###### Рисунок 18 - Та же команда после обновления
![image](https://github.com/user-attachments/assets/4327563c-5875-4211-9b1a-8d735b683a12)

3. Еще раз просмотрели версию ОС, видно, что она изменилась.
###### Рисунок 19 - Настоящая версия ОС
![image](https://github.com/user-attachments/assets/01a9ad4f-f933-43e3-86a5-c96be5d49f8a)

## 5) Использование команды sudo
1. sudo - утилита, которая временно повышает привелегии пользователя до root для выполнения команды.
2. Выдача пользователю прав использования ``sudo`` осуществляется добавлением пользователя в файл ``sudoers``.
###### Рисунок 20 - Открытие файла etc/sudoers.tpm
![image](https://github.com/user-attachments/assets/1157f0ff-1938-4559-9507-379552dca537
###### Рисунок 21 - Добавление alex в sudoers
![image](https://github.com/user-attachments/assets/ff213c52-8193-4606-a2f8-ecd551cbd18e)

3. Теперь пользователь ``alex`` может выполнять команды от root.
###### Рисунок 22 - Переход в командную оболочку пользователя ``alex``
![image](https://github.com/user-attachments/assets/a2b4c075-d9da-44a7-b69b-8c20b96097d5)
###### Рисунок 23 - Изменение hostname
![image](https://github.com/user-attachments/assets/011172e6-319e-482f-8b43-204f0e8b4690)
###### Рисунок 24 - Новое имя хоста
![image](https://github.com/user-attachments/assets/1001b493-26de-461e-b9f0-c0ea8cb72b33)

## 6) Установка и настройка службы времени
###### Рисунок 25 - Время настоящего часового пояса
![image](https://github.com/user-attachments/assets/ffafe882-2e3e-456a-b47c-6b797ba1e1ce)
###### Рисунок 26 - Вывод команды ``timedtectl show``
![image](https://github.com/user-attachments/assets/b05d19e4-93ba-42f9-b7a1-c0bff6c3d3f4)

* Вывод содержит ``NTPSynchronized=yes``

## 7) Установка и использование текстовых редакторов
###### Рисунок 27 - JOE установлен
![image](https://github.com/user-attachments/assets/504e39b1-2e94-4a45-af21-111b6038f462)
###### Рисунок 28 - vim установлен
![image](https://github.com/user-attachments/assets/62e8f53d-ac3a-4fee-b1af-4ac68b6bc076)
###### Рисунок 29 - nano устанволен
![image](https://github.com/user-attachments/assets/4ad0e366-f7ae-46d6-b58d-80c5f13fd58b)

### Выйти с сохранением изменений
###### Рисунок 30 - файл test_vim.txt
![image](https://github.com/user-attachments/assets/20c36dff-b05b-4bac-8dec-3e8ede1066ac)
* **Выход из файла с сохранением: :wq**
###### Рисунок 31 - файл test_nano.txt
![image](https://github.com/user-attachments/assets/03b2cd4f-8852-4c75-9b55-63f9e4de66fc)
* **Выход из файла с сохранением: Ctrl+X -> y -> Enter**
###### Рисунок 32 - файл test_joe.txt
![image](https://github.com/user-attachments/assets/94113c08-d1a7-4c29-81a5-7e477b9cea5b)
* **Выход из файла с сохранением: Ctrl+K X -> Ctrl+K D -> y**

### Выйти без сохранения изменений
###### Рисунок 33 - файл test_vim.txt
![image](https://github.com/user-attachments/assets/18cccb38-d816-4941-ab30-726115da9a02)
* **Выход из файла без сохранения: :q!**
###### Рисунок 34 - файл test_nano.txt
![image](https://github.com/user-attachments/assets/3fb121b2-3ab5-42d3-937d-35ca6514340e)
* **Выход из файла без сохранения: Ctrl+X -> n**
###### Рисунок 35 - файл test_joe.txt
![image](https://github.com/user-attachments/assets/9a1c55f4-8040-430b-a758-740f0118017a)
* **Выход из файла без сохранения: Ctrl+C -> y**

### Поиск слова и редактирование 
1. Поиск слова в vim: /<слово>
###### Рисунок 36 - Поиск слова School в test_vim.txt
![image](https://github.com/user-attachments/assets/aed9ea7e-e35b-441b-a390-d9b3c8883b70)

2. Замена слова в vim: :s/<слово>/<замена>
###### Рисунок 37 - Замена School на sarirunc в test_vim.txt
![image](https://github.com/user-attachments/assets/aa056800-0c32-44ac-af5b-1f2d6bfcedc0)

3. Поиск слова в nano: (Ctrl + W)
###### Рисунок 38 - Поиск слова School в test_nano.txt
![image](https://github.com/user-attachments/assets/fd07876b-e815-4d41-a617-a2e35b66eac8)

4. Замена слова в nano: (Ctrl + W) -> (Ctrl + R)
###### Рисунок 39 - Замена School на sarirunc в test_nano.txt
![image](https://github.com/user-attachments/assets/463d0bba-ec81-4cf1-8d4f-2bf74ac646c9)
![image](https://github.com/user-attachments/assets/adedd06d-a2bd-4b07-8279-9839fda38c0d)
![image](https://github.com/user-attachments/assets/aa5c6ae3-855a-4e8e-969d-b5a21a0c03c7)

5. Поиск и замена слова в joe Ctrl+K F
###### Рисунок 40 - Поиск слова School в test_joe.txt
![image](https://github.com/user-attachments/assets/5bda2f48-5832-48e2-ac31-7b6ccb1dfba7)
###### Рисунок 41 - Замена School на sarirunc в test_joe.txt
![image](https://github.com/user-attachments/assets/b3e43232-47af-41e6-9197-98a277208e70)
![image](https://github.com/user-attachments/assets/d8d63552-351d-4150-a4e8-e82066a943a5)

## 8) Установка и базовая настройка сервиса SSHD
1. Установили ssh-server.
###### Рисунок 42 - Установка ssh
![image](https://github.com/user-attachments/assets/17efdffd-e71c-4dc9-be7f-b07b8ed96876)

2. дОбавили его в автостарт.
###### Рисунок 43 - Добавление ssh в автостарт
![image](https://github.com/user-attachments/assets/52b8dc6f-b364-4f1a-b8f4-a9c5261088a3)

3. Изменили порт на 2022 в файле конфигурации ssh.
###### Рисунок 44 - Редактирование файла конфигурации sshd_config
![image](https://github.com/user-attachments/assets/3c67db6a-360a-468e-ae67-d3e278b64eb5)

4. Перезагрузили сервис, проверили, что порт изменился.
###### Рисунок 45 - Видно, что порт изменился
![image](https://github.com/user-attachments/assets/5e74b4f5-a3f9-4a40-b8f4-deab60abf541)

5. Нашли sshd в запущенных процессах.
###### Рисунок 47 - Выполнение команды ``ps -aux | grep "ssh"``
![image](https://github.com/user-attachments/assets/a26dd04c-4256-4b3d-8977-d538b7368e44)

* ps - выводит процессы
* -a - показывает процессы для всех пользователей
* -u - отобращает пользователя/владельца процесса
* -x - также показывает процессы, не привязанные к терминалу
6. Выполнили команду ``netstat``
###### Рисунок 48 - Вывод команды ``netstat -tan``
![image](https://github.com/user-attachments/assets/e4fadd7e-64d4-45fe-a9ac-52fa710a7054)
* Команда ``netstat`` отображает информацию о сетевой конфигурации и активности системы Linux, включая сетевые соединения, таблицы маршрутизации, статистику интерфейса и членство в многоадресной рассылке.
* -t - Отображает TCP-соединения
* -a - Показывает все прослушивающие порты и активные соединения
* -n - Показывает числовые адреса вместо разрешения хостов и портов
* Столбцы:
  - Протокол
  - Количество принятых пакетов в очереди
  - Количество отправленных пакетов в очереди
  - Локальный адрес, 0.0.0.0 означает что подключаться можно к любому адресу, но только по 2022 порту
  - Удаленный адресс, 0.0.0.0:* означает, что принимать подключения можно с любого адреса, с любого порта
  - Статус порта

## 9) Установка и использование утилит top, htop
1. Запустили утилиту ``top``.
###### Рисунок 49 - Запуск утилиты ``top``
![image](https://github.com/user-attachments/assets/8a9ca924-992d-4112-b2f8-c718bdc6032e)

Утилита показывает следующую информацию:
- uptime: 12 min
- количество авторизованных пользователей: 1
- среднюя загрузка системы: 0.91, 0.54, 0.21 
- общее количество процессов: 97
- загрузку cpu:
  •  us (user): 0.0% - время, затраченное процессами пользователя.
  •  sy (system): 0.0% - время, затраченное ядром.
  •  ni (nice): 0.0% - время, затраченное процессами с измененным приоритетом.
  •  id (idle): 100.0% - время простоя CPU.
  •  wa (wait): 0.0% - время ожидания ввода/вывода.
  •  hi (hardware interrupts): 0.0% - время обработки аппаратных прерываний.
  •  si (software interrupts): 0.0% - время обработки программных прерываний.
  •  st (steal time): 0.0% - время, украденное у виртуальной машины другим гипервизором.
- загрузку памяти:
  •  total: 2906.2 MiB - общий объем памяти.
  •  free: 2404.8 MiB - объем свободной памяти.
  •  used: 361.4 MiB - объем используемой памяти.
  •  buff/cache: 296.9 MiB - объем памяти, используемой для буферов и кэша.
- pid процесса занимающего больше всего памяти: 1 (PID=1, занимает 0.4% памяти)
- pid процесса, занимающего больше всего процессорного времени: 8 (PID=8, занимает 0.3% CPU)

2. Зарустили утилиту ``htop``
###### Рисунок 49 - Сортировка ``htop`` по PID
![image](https://github.com/user-attachments/assets/a4fbcda2-8d1e-42e5-8fcb-6e089d897226)
###### Рисунок 50 - Сортировка ``htop`` по PERCENT_CPU
![image](https://github.com/user-attachments/assets/fdf80309-cb8e-4500-80e1-9770747b0a2f)
###### Рисунок 51 - Сортировка  ``htop``по PERCENT_MEM
![image](https://github.com/user-attachments/assets/4298f41e-95c8-4281-83ce-f6e415975fc9)
###### Рисунок 52 - Сортировка ``htop`` по TIME
![image](https://github.com/user-attachments/assets/5a28142a-5bd3-4074-b010-7c1da4d64037)
###### Рисунок 53 - ``htop`` отфильтрованный по sshd
![image](https://github.com/user-attachments/assets/2c6c078a-4092-4b1d-bdd5-760d69434d18)
###### Рисунок 54 - ``htop`` с процессом syslog, найденным, используя поиск
![image](https://github.com/user-attachments/assets/4c6ee401-3ff2-460e-bd9f-fdd2c14d04c7)
###### Рисунок 55 - ``htop`` с добавленным выводом hostname, clock и uptime
![image](https://github.com/user-attachments/assets/30e39c0f-9893-44de-8cdb-97790e9535e0)

## 10) Использование утилиты fdisk
###### Рисунок 56 - Запуск комнады ``fdisk -l``
![image](https://github.com/user-attachments/assets/19b98ba4-6efb-434e-94c4-453f46bfd9d9)

* Жесткий диск называется /dev/sda
* Его размер составляет 50 GiB\
* Он содержит 104857600 секторов
* Размер swap составляет 24 GiB

## 11) Использование утилиты df
###### Рисунок 57 - Запуск комнады ``df``
![image](https://github.com/user-attachments/assets/571f5f85-c227-4a1f-ae98-30c4d01fbe02)

* Для корневого раздела:
  - Размер корневого раздела составляет 24590672 1K-block
  - Размер занятого пространства — 6757684 1K-blocks
  - Размер свободного пространства — 16558520 1K-blocks
  - Процент использования — 29%.
* Единицей измерения в выводе является 1K-blocks (1 килобайт).
###### Рисунок 58 - Запуск комнады ``df -Th``
![image](https://github.com/user-attachments/assets/3e77ac84-f9e5-4804-8bf6-d97018580b71)

* Для корневого раздела (/):
  - Размер раздела: 24Гб
  - Размер занятого пространства: 6,5 Гб
  - Размер свободного пространства: 16 Гб
  - Процент использования: 29%
* Тип файловой системы для раздела: ext4

## 12) Использование утилиты du
###### Рисунок 59 - Размер папки /home (в байтах, в человекочитаемом виде)
![image](https://github.com/user-attachments/assets/e211c827-8ccd-4d99-9b96-2c6a7c1c1e64)
###### Рисунок 60 - Размер папки /var (в байтах, в человекочитаемом виде)
![image](https://github.com/user-attachments/assets/fe0bdbfc-98fe-4a2f-ae4a-8e4f204cb517)
###### Рисунок 61 - Размер папки /var/log (в байтах, в человекочитаемом виде)
![image](https://github.com/user-attachments/assets/c41a79af-920a-4e40-811c-f2e8d6a22182)
###### Рисунок 62 - Размер каждого элемента вложенного в /var/log
![image](https://github.com/user-attachments/assets/24c4a711-22d6-46a9-872c-886e828f9cf5)

## 13) Установка и использование утилиты ncdu
###### Рисунок 63 - Размер папки /home
![image](https://github.com/user-attachments/assets/e2e62a4f-79b1-403f-8161-744086fbf8e2)
###### Рисунок 64 - Размер папки /var
![image](https://github.com/user-attachments/assets/5917275f-f11e-4775-8dcd-43015315528c)
###### Рисунок 65 - Размер папки /var/log
![image](https://github.com/user-attachments/assets/0830d360-48c9-4bc7-8c76-7d8b26c045e5)

## 14) Работа с системными журналами
1. Нашли последнее время авторизации пользователя.
###### Рисунок 66 - Записи об авторизации из auth.log
![image](https://github.com/user-attachments/assets/623e3877-7c98-49e0-bd1d-0e581879f58a)

  * Время последней успешной авторизации: 2025-03-16T18:04:24
  * Имя пользователя: sarirunc
  * Метод входа в систему: с помощью логина
2. Перезапустили SSHd
###### Рисунок 67 - Сообщения о перезапуске службы
![image](https://github.com/user-attachments/assets/b8cd1c91-64cf-4752-9e86-aa2a9c79bcdf)

## 15) Использование планировщика заданий CRON
1. Добавили новую зачу в планировщик.
###### Рисунок 67 - Добавление новой задачи в файл ``crontab``
![image](https://github.com/user-attachments/assets/9548a8b3-2313-43a4-9b77-bc394f69ecef)

2. Проверили выполнение этой задачи.
###### Рисунок 68-69 - Две записи в журнале о выполнении команды ``uptime``
![image](https://github.com/user-attachments/assets/d1d3f767-a2c0-4bab-aead-1721b4540029)
![image](https://github.com/user-attachments/assets/4331be38-adcb-44a2-9267-847de95deb7e)

3. Вывели список задач.
###### Рисунок 70 - Cписок текущих заданий для CRON
![image](https://github.com/user-attachments/assets/616b250f-356f-45eb-b988-a547df608835)

4. Удалили задачи.
###### Рисунок 71 - Удаление задач
![image](https://github.com/user-attachments/assets/7d467b06-6865-460c-b831-8d52accda070)

5. Еще раз проверили список
###### Рисунок 72 - Теперь в списке нет задач
![image](https://github.com/user-attachments/assets/8d3c2272-2319-4fe7-a641-5e9df71f979b)

