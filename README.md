TheHive + Cassandra + Cortex

1. Создать в директории с ***docker-compose.yml*** файл .env и бобавить в него:
```
job_directory=/tmp/cortex-jobs
```
2. ***docker-compose up***
3. Создать в Cortex организацию и пользователя. Сгенерировать API ключ и вставить в его конфигурационный файл TheHive вместо {API_KEY}:
```
cortex {
  servers = [
    {
      name = Cortex
      url = "http://cortex:9001"
      auth {
        type = "bearer"
        key = "{API_KEY}"
      }
      includedTheHiveOrganisations = ["*"]
      excludedTheHiveOrganisations = []
    }
  ]
```
4. ***docker restart {thehive_container_id} ***
5. Готово.