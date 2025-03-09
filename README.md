# 8-03-hw
# Установка Zabbix

## Установка репозитория Zabbix
wget https://repo.zabbix.com/zabbix/7.2/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.2+debian12_all.deb  
dpkg -i zabbix-release_latest_7.2+debian12_all.deb  
apt update  

## Установка Zabbix сервера, web-интерфейса и агента
apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent  

## Установка PostgreSQL
sudo apt install -y postgresql-common  
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh  
sudo apt install curl ca-certificates  
sudo install -d /usr/share/postgresql-common/pgdg  
sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc  
sudo sh -c 'echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'  
sudo apt update  
sudo apt -y install postgresql  

## Содание базы данных
sudo -u postgres createuser --pwprompt zabbix  
sudo -u postgres createdb -O zabbix zabbix  
  
zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix  

## Настройка базы данных для Zabbix сервера
vim /etc/zabbix/zabbix_server.conf  
DBPassword=password  

## Запуск процессов Zabbix сервера и агента
systemctl restart zabbix-server zabbix-agent apache2  
systemctl enable zabbix-server zabbix-agent apache2  

## Скриншот для Задания 1
![image](https://github.com/user-attachments/assets/a8ce9e7e-de46-4e19-afd9-82e9cd14a25a)

## GIT команды
git status  
git add --all  
git commit -m "Update README.md"  
git push  

## Установка репозитория Zabbix
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb  
dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb  
apt update  

## Установка Zabbix агента на Ubuntu
apt install zabbix-agent  

## Запуска процесса Zabbix агента
systemctl restart zabbix-agent  
systemctl enable zabbix-agent  

## Скриншот для Задания 2
![image](https://github.com/user-attachments/assets/76af8350-8cbf-4cf4-b34f-967e0e1ca37c)  
![image](https://github.com/user-attachments/assets/b9c8df3d-3354-44ae-8277-872b8ff1747b)  



