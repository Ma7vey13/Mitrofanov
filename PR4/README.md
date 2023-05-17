# Развертывание Threat intelligence Platform OpenCTI
Матвей Митрофанов

## Цель работы

1. Освоить базовые подходы процессов Threat Intelligence
2. Освоить современные инструменты развертывания контейнеризованных приложений
3. Получить навыки поиска информации об угрозах ИБ

## Ход выполнения работы
Разворачивание системы Threat Intelligence OpenCTI осуществлялось с помощью Docker.

1. Для работы с ElasticSearch требуется увеличить размер виртуальной памяти системы:
```()
sudo sysctl -w vm.max_map_count=1048575
```

2. В новой директории был создан файл .env для хранения параметров окружения

Использованы следующие команды для генерации UUIDv4 и записи их в файл .env:
```()
echo "OPENCTI_ADMIN_TOKEN=$(uuidgen)" >> .env
echo "CONNECTOR_EXPORT_FILE_STIX_ID=$(uuidgen)" >> .env
echo "CONNECTOR_EXPORT_FILE_CSV_ID=$(uuidgen)" >> .env
echo "CONNECTOR_EXPORT_FILE_TXT_ID=$(uuidgen)" >> .env
echo "CONNECTOR_IMPORT_FILE_STIX_ID=$(uuidgen)" >> .env
echo "CONNECTOR_IMPORT_DOCUMENT_ID=$(uuidgen)" >> .env
```
![image](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/20160060-bb0d-4fa5-ba83-a2fcb0381365)

3. В этой же директории создан файл docker-compose.yml

Запуск контейнера с помощью команды:
```()
sudo docker-compose up -d
```
![image](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/f93df294-38a9-497a-87d8-9be991b5d30e)

4. Заходим в веб-интерфейс OpenCTI `localhost:8088`

Входим по данным пользователя из файла конфигурации окружения:
![1](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/29facec5-dc91-424a-990c-7dce2c3c8007)

5. Попадаем на главную страницу
![Снимок экрана 2023-05-17 170828](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/273a5532-4f61-4a56-bcee-9422360dbe03)

6. Далее используем данный код через оболочку Python внутри контейнера для импорта данных из файла hosts.txt

``` python
import pycti
from stix2 import TLP_GREEN
from datetime import datetime
date = datetime.today().strftime("%Y-%m-%dT%H:%M:%SZ")
api_url = 'http://localhost:8080'
api_token = 'bd78ebc1-d5c8-466f-bbd3-126a9479472c'
client = pycti.OpenCTIApiClient(api_url, api_token)

TLP_GREEN_CTI = client.marking_definition.read(id=TLP_GREEN["id"])
with open('hosts.txt', 'r') as f:
    domains = f.read().splitlines()
k = 1
for domain in domains:
    indicator = client.indicator.create(
    name="Malicious domain {}".format(k),
    description="MPVS hosts",
    pattern_type="stix",
    label="mpvs hosts",
    pattern="[domain-name:value = '{}']".format(domain),
    x_opencti_main_observable_type="IPv4-Addr",
    valid_from=date,
    update=True,
    score=75,
    markingDefinitions=[TLP_GREEN_CTI["id"]],
    )
    print("Создан индикатор:", indicator["id"])
    k += 1
```

Получен список индикаторов нежелательных доменов:
![Снимок экрана 2023-05-18 001324](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/cefc6ded-924d-4af5-85c8-668297f68287)

7. Преобразуем все индикаторы в Observables
![Снимок экрана 2023-05-18 001620](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/bc688176-18f5-431d-a4d0-054d747e8b00)

8. Импортируем сетевой трафик (файл dns.log), полученный в PR2 в OpenCTI
![Снимок экрана 2023-05-17 224707](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/100acd3b-7e72-402b-9a2e-7045740f21ca)

9. Информация с главной страницы OpenCTI
![image](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/90c743ef-5e90-4622-8982-02e17c647b6d)

10. Переходим в раздел Analitics -> Report, чтобы посмотреть домены с нежелательным трафиком
![Снимок экрана 2023-05-18 015022](https://github.com/Ma7vey13/Mitrofanov/assets/92400475/3b2e4b5a-2c2c-4a2c-b605-5240ddc009ac)

## Оценка результата

С помощью платформы OpenCTI удалось проанализировать трафик на предмет перехода по нежелательным доменам.

## Выводы

Таким образом, были изучены возможности работы с платформой threat intelligence OpenCTI
