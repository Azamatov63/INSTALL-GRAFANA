![image](https://github.com/user-attachments/assets/bc33b7a9-f6ab-4671-b447-661f27da96ae)

# INSTALL-GRAFANA

1. Установил пакет <b>wget</b>, используя команду `sudo yum install wget`, с этим пакетом можно загружать файлы с интернета

![image](https://github.com/user-attachments/assets/0003a506-9140-4f18-840e-da3f31d534bc)

2. И установил пакет <b>curl</b> командой `sudo yum install curl`, для того чтобы отправлять HTTP/HTTPS запросы

![image](https://github.com/user-attachments/assets/6d02fe6c-28dc-42a4-ab03-3422b54755ed)

3. Копирую репозиторий докера, для того чтобы его потом установить, используя <b>wget</b> используя тег <b>-P</b> для чтения командой `sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/49702220-2091-4d13-9b05-8a1c47eb7113)

4. Устанавливаем докер из копированного репозитория `sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/9d328c5f-59bc-44d7-b803-cb1647a64837)
![image](https://github.com/user-attachments/assets/016bfe10-4c09-4deb-b02c-4372631a8e99)

5. Запускаем докер используя команду `sudo systemctl enable docker --now` эта команда добавляет doker в список служб, которые запустятся при запуске ОС

![image](https://github.com/user-attachments/assets/1fbf4817-c4b8-4247-97c7-303aaf446559)

6. Получаем последнюю версию Docker Compose, используя команду `COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/50a49f8d-a5be-4a0a-af9a-db69a01bb0b5)

7. Скачиваем и устанавливаем последнюю версию Docker Compose с помощью команды `sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose`

![image](https://github.com/user-attachments/assets/cb9665bd-511c-499d-ae83-8acabd4867c8)

8. Устанавливаем права на выполнение `sudo chmod +x /usr/bin/docker-compose` 

![image](https://github.com/user-attachments/assets/372b8fd6-7c12-4b21-8cdf-2a515fc1f06e)

9. Проверяем установленную версию docker c помощью команды `docker --version`

![image](https://github.com/user-attachments/assets/008fcc42-9639-4701-898d-edfcb1251e5a)

10. Клонируем репозиторий с github, где содержится Grafana с помощью команды `git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/20edabf3-6167-4cdf-a25b-821bc2a37512)

11. Переходим в директорию в Grafana с помощью команды `cd grafana_stack_for_docker`

![image](https://github.com/user-attachments/assets/aed2cc17-c4d8-4d6e-b79c-30905cde8719)

12. Создаем директорию с помощью команды `sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

![image](https://github.com/user-attachments/assets/81edb2f5-503c-4266-a3c3-d757f1f288bf)

13. И создаем еще одну директорию `sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

![image](https://github.com/user-attachments/assets/f15e5689-080b-41e9-9190-c877ee7dec5c)

14. Изменяем владельца и группу для указанных директорий и всех их содержимых файлов с помощью `sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}`

![image](https://github.com/user-attachments/assets/9ab016f9-60f9-4004-acd9-54c0c1373c3e)

15. 

![image](https://github.com/user-attachments/assets/36be6f18-9b8c-496f-bc72-dd072bfdcf1c)

![image](https://github.com/user-attachments/assets/5198901b-9f7b-4d78-a745-aa3863252ecf)

![image](https://github.com/user-attachments/assets/41d1cd56-91f4-473e-bb83-83bef2391e51)

![image](https://github.com/user-attachments/assets/1ba0b64b-f93b-40ba-93f4-f68be388dc47)
![image](https://github.com/user-attachments/assets/3581849f-766c-4d9e-8544-62b9e02ba52c)
