# Домашние задания по модулю «Мониторинг»

В этом репозитории расположены ваши домашние задания к каждой лекции. 

Обязательны к выполнению задачи без звездочек. Их нужно выполнить, чтобы получить зачёт.

Задачи со звёздочкой (*) — дополнительные задачи или задачи повышенной сложности. Их выполнять не обязательно, но они помогут вам глубже понять тему.

Любые вопросы по решению задач задавайте в чате учебной группы. Ссылку вы найдёте в письме на вашей электронной почте.


1. [Обзор систем ИТ-мониторинга](hw-01.md)

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img1.png)

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img2.png)


2. [Система мониторинга Zabbix](hw-02.md)

### Задание 1 

Установите Zabbix Server с веб-интерфейсом.
#### Процесс выполнения:

1. Установливаем репозиторий Zabbix
wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb
dpkg -i zabbix-release_6.4-1+ubuntu22.04_all.deb
apt update 

2. Установливаем Zabbix сервер, веб-интерфейс
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts

3. Создаём базу данных 
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix 

4. На хосте Zabbix сервера импортируруем начальную схему и данные. 
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix 

5. Запускаем процессы Zabbix сервера
systemctl restart zabbix-server 
systemctl enable zabbix-server

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img3.png)


### Задание 2 

Установите Zabbix Agent на два хоста.

#### Процесс выполнения:

1. Установливаем репозиторий Zabbix

wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb
dpkg -i zabbix-release_6.4-1+ubuntu22.04_all.deb
apt update 

2. Установливаем Zabbix агент 

apt install zabbix-agent

3. Запускаем процесс Zabbix агента 

systemctl restart zabbix-agent
systemctl enable zabbix-agent

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img4.png)


3. [Система мониторинга Zabbix. Часть 2](hw-03.md)

### Задание 1
 
Создайте свой шаблон, в котором будут элементы данных, мониторящие загрузку CPU и RAM хоста.

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img5.png)


### Задание 2

Добавьте в Zabbix два хоста и задайте им имена <фамилия и инициалы-1> и <фамилия и инициалы-2>. Например: ivanovii-1 и ivanovii-2.

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img6.png)

### Задание 3

Привяжите созданный шаблон к двум хостам. Также привяжите к обоим хостам шаблон Linux by Zabbix Agent.

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img7.png)

### Задание 4 

Создайте свой кастомный дашборд.

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img8.png)


4. [Система мониторинга Prometheus](hw-04.md)
### Задание 1
Установите Prometheus.

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img9.png)


### Задание 2
Установите Node Exporter.

#### Результат:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img10.png)

### Задание 3
Подключите Node Exporter к серверу Prometheus.

#### Результат:

конфигурация:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img11.png)

Targets:

![alt text](https://github.com/Redcorprus/8.1-IT-Monitoring/blob/main/img/img12.png)


5. [Система мониторинга Prometheus. Часть 2](hw-05.md)
