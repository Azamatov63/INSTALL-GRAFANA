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

15. Создаем файл конфигурации с помощью команды `touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

![image](https://github.com/user-attachments/assets/36be6f18-9b8c-496f-bc72-dd072bfdcf1c)

16. Копируем все файлы из директории config в /mnt/common_volume/swarm/grafana/config/ c помощью команды `cp config/* /mnt/common_volume/swarm/grafana/config/`

![image](https://github.com/user-attachments/assets/5198901b-9f7b-4d78-a745-aa3863252ecf)

17. Переименовываем файл grafana.yaml в docker-compose.yaml с помощью `mv grafana.yaml docker-compose.yaml`

![image](https://github.com/user-attachments/assets/41d1cd56-91f4-473e-bb83-83bef2391e51)

18. Запускаем Docker Compose в фоновом режиме с помощью `sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/1ba0b64b-f93b-40ba-93f4-f68be388dc47)
![image](https://github.com/user-attachments/assets/3581849f-766c-4d9e-8544-62b9e02ba52c)

19. Открываем браузер и переходим по адресу: <b>localhost:3000</b>

<b>Логин:</b> admin

<b>Пароль:</b> admin

![image](https://github.com/user-attachments/assets/c9ee9cf7-9632-4600-b659-1fb2b7bf5ce9)

20. Открывается страница <b>Home</b>

![image](https://github.com/user-attachments/assets/69997362-c011-4f06-a3c7-7cff3a0f395b)

21. Останавливаем grafana командой `sudo docker compose stop`

![image](https://github.com/user-attachments/assets/c3191edb-3c8a-42ae-b807-25fd3d703564)

22. Чтобы полность остановить вводим команду `sudo docker compose down`

![image](https://github.com/user-attachments/assets/e292fd39-ac73-4be1-b890-2960930da02a)

23. Заходим в конфигурационный файл докера с помощью команды `vi docker-compose.yaml`

![image](https://github.com/user-attachments/assets/c773a368-2056-460a-8b33-0d31bf5ebccd)
![image](https://github.com/user-attachments/assets/0d8ea662-034f-460a-a4f9-a71567a0a796)

24. Выходим вписав команду `:wq`

![image](https://github.com/user-attachments/assets/0e4cdcc2-0c99-47df-8fbd-caa9b05aeb88)

# Prometheus

25. Переходи в директорию `cd grafana_stack_for_docker/` и копируем конфигурационные файлы с gitgub `sudo git clone https://github.com/Azamatov63/INSTALL-GRAFANA`

![image](https://github.com/user-attachments/assets/8aeda7b7-6580-4abe-bb81-8bb56b2dd459)

26. Проверяем, что репозиторий установился `ls`

![image](https://github.com/user-attachments/assets/591610c5-7c88-4f3a-a024-d0fc417fe30f)

27. Копируем конфигурационный файл докера в папку с Grafan `cp docker-compose.yaml /home/Azamatov/grafana_stack_for_docker/`

![image](https://github.com/user-attachments/assets/d06a93a8-05c2-4b72-ba05-f285659c7b2b)

28. Тоже самое делаем с файлом prometheus`cp prometheus.yaml /home/Azamatov/grafana_stack_for_docker/`

![image](https://github.com/user-attachments/assets/a9554a9e-aff1-4cc5-9a34-cc318aeafbbd)

29. Переносим конфигурационный файл prometheus.yaml в конфиг Grafana, используя команду `mv prometheus.yaml /mnt/common_volume/swarm/grafana/config`

![image](https://github.com/user-attachments/assets/d73236ce-f596-48e1-aead-03614c83b2cc)

30. Проверяем наличие файла `ls`

![image](https://github.com/user-attachments/assets/0869b094-dc81-40cb-93bf-63a009fcbac5)

31. Запускаем docker compose `sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/513df9ac-7c85-4edb-af3a-008dffba5eac)

32. Переходим на вкладку Dashboards

![image](https://github.com/user-attachments/assets/163be610-81f9-4e98-b809-09437a10cd91)

33. Жмем + Create Dashbord

![image](https://github.com/user-attachments/assets/142fcb3d-652d-48e9-81ca-9bf597106c1a)

34. Нажимаем кнопку +Add visualization

![image](https://github.com/user-attachments/assets/85f7d89c-ea76-43bf-8096-e506e422bac2)

35. После Configure a new data source

![image](https://github.com/user-attachments/assets/bcf32f4c-4648-490d-97f8-bd8a9c2dbdc2)

36. Выбираем Prometheus

![image](https://github.com/user-attachments/assets/e3c96d1c-cd70-4a5d-95ac-29d7f41c93d9)

37. Пункт Connection: `http://prometheus:9090`

![image](https://github.com/user-attachments/assets/a186bcdc-fd75-4482-9661-2a2331800a20)

38. Пункт Authentication:

 Выбирем Basic authentication

<b>User:</b> admin

<b>Password:</b> admin


![image](https://github.com/user-attachments/assets/a242e5de-ed97-4d15-bde3-d5a04a8e6f5a)

39. Нажимаем на Save & test и должно показывать зелёную галочку

![image](https://github.com/user-attachments/assets/3163dc1d-e73b-456b-a509-31301703024f)

40. В меню выбираем вкладку Dashboards и создаем Dashboard. Жмем кнопку "Import dashboard

![image](https://github.com/user-attachments/assets/e1329d27-03e6-4fc7-94f3-dde11dad117e)

41. Вписываем 1860 и жмем Load

![image](https://github.com/user-attachments/assets/8f627d86-1163-4079-b291-312a3ab43748)

42. Нажимаем Import

![image](https://github.com/user-attachments/assets/38898e38-da02-480f-ac44-f2e0193a586a)

43. Открывается такой Dashboard для мониторинга загрузки ОС

![image](https://github.com/user-attachments/assets/4b3ad6eb-2321-42f4-9df2-abb881f3260a)

# Victoria

44. Вводим команду `echo -e "# TYPE light_metric1 gauge\nlight_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus` которая, отправляет бинарные данные на локальный сервер, который слушает на порту 8428.

![image](https://github.com/user-attachments/assets/2c86bbe4-6229-4fbf-a2bf-83539c06b97e)

45. Переходим в браузере по ссылке `http://localhost:8428/`, открывается такое меню в нём нужно выбрать `vmui`

![image](https://github.com/user-attachments/assets/9a2413cf-a57e-4c67-ad68-2043b01fb557)

46. Вписываем `light_metric1` и нажимаем Execute Query

![image](https://github.com/user-attachments/assets/ae07f680-c535-441e-8b04-a8c6e97b34cf)

47. Переходим на `http://localhost:3000` выбираем Dashboard и нажимаем New Dashboard

![image](https://github.com/user-attachments/assets/a454def3-abe2-4f18-8546-8c2c55f0978a)

48. Далее Add Visualization

![image](https://github.com/user-attachments/assets/35f00c3b-9f54-4b84-8f4f-7c9854bbd4ad)

49. Нажимаем Configure a new data source 

![image](https://github.com/user-attachments/assets/f4e1c86c-4320-4ac2-bba6-1986c63fea1f)

50. И выбираем Prometheus

![image](https://github.com/user-attachments/assets/acb7a216-8e7b-427a-bff5-0bb45462a490)

51. Вписываем:

Name: Victoria

Connection: http://victoriametrics:8428

![image](https://github.com/user-attachments/assets/cc0c9cf3-0428-4984-8301-88531d881b67)

52. Нажимаем Save & Test

![image](https://github.com/user-attachments/assets/41b017bf-5e19-41b3-9280-6ef4385b934b)

53. Переходим на вкладку Code

![image](https://github.com/user-attachments/assets/afcd6be1-8c26-4e7b-8645-01b5dfa16136)

53. Вписываем light_metric1

![image](https://github.com/user-attachments/assets/10d294d3-e374-4cbf-9506-6a8ac33f7a7a)

54. Выходит панель с графиком, где есть активность light_metric1

![image](https://github.com/user-attachments/assets/87321546-f167-49f5-95e9-be35b4a475e5)
