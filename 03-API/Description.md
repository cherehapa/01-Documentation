# API v.2
## Общие сведения
Для расчета и выписки страхового полиса нужны:

 * Страна назначения (country)
 * Страховой продукт(ы), по которому выписывается полис (insuranceProduct)
 * Виды спорта (sport) (не обязательно, в зависимости от выбора пользователя)

Функциям расчета и создания полиса передаются те же параметры, что и при создании запроса. Создание запроса (request) - не обязательный этап, но в дальнейшем можно использовать код запроса вместо повторной передачи всех параметров.

## Реквизиты доступа
Адрес тестового сервера: http://api.staging.cherehapa.ru/  
Ключ доступа: [key]

## Схема работы с API v2
API v.2 строится на базе RESTful схемы, т.е., в целом обращение идет по одним и тем же адресам, а действие, выполняемое через API определяется указанным в запросе HTTP-методом.

Обозначения:

 * [api_base] - базовый адрес конкретного API. Например: https://api.staging.cherehapa.ru/v2/
 * [resource] - название ресурса (объекта), с которым ведется работа. Например: country или order
 * [function] - идетификатор дополнительной функции действия над объектом
 * [id] - уникальный код элемента в базе данных
 * [ ] - необязательные параметры

## Перечень общих методов API

| Название метода    | Описание                                               | URL                        |HTTP-метод | Пример URL |                            
|--------------------|--------------------------------------------------------|----------------------------|-----------|------------|
| index              | Получение перечня объектов                             | api_base/resource      | GET       | http://api.staging.cherehapa.ru/v2/country |
| store              | Создание нового объекта                                | api_base/resource      | POST      | http://api.staging.cherehapa.ru/v2/country |
| show               | Получение подробных данных об объекте                  | api_base/resource/id | GET       | http://api.staging.cherehapa.ru/v2/country/1 |
| update             | Обновление свойств объекта                             | api_base/resource/id | PUT       | http://api.staging.cherehapa.ru/v2/country/1 |
| destroy            | Удаление объекта из базы или отмена действия объекта   | api_base/resource/id | DELETE    | http://api.staging.cherehapa.ru/v2/country/1 |

## Полный перечень объектов и методов

| Объект        | Метод         | Описание      | Тестовый запрос    |
|---------------|---------------|---------------|--------------------|
| country       | GET /country  | Получение перечня стран | http://api.staging.cherehapa.ru/v2/country?key=[key] |
| | GET /country/[id] | Получение информации о стране с кодом [id] | http://api.staging.cherehapa.ru/v2/country/570?key=[key] |
| countryGroup  | GET /countryGroup | Возвращает список групп стран | http://api.staging.cherehapa.ru/v2/countryGroup?key=[key] |
| | GET /countryGroup/[id] | Отображает подробные данные группы стран по id | http://api.staging.cherehapa.ru/v2/countryGroup/3?key=[key] |
| company       | GET /company  | Возвращает список страховых компаний, доступных партнеру | http://api.staging.cherehapa.ru/v2/company?key=[key] |
| | GET /company/[id] | Отображает подробную информацию о компании по id | http://api.staging.cherehapa.ru/v2/company/1?key=[key] |
| service       | GET /service  | Возвращает список страховых услуг, доступных партнеру | http://api.staging.cherehapa.ru/v2/service?key=[key] |
| | GET /service/[id] | Отображает подробную информацию о страховой услуге по id | http://api.staging.cherehapa.ru/v2/service/1?key=[key] |
| serviceGroup  | GET /serviceGroup | Возвращает список групп страховых услуг, доступных партнеру | http://api.staging.cherehapa.ru/v2/serviceGroup?key=[key] |
| | GET /serviceGroup/[id] | Отображает подробную информацию о группе страховых услуг по id | http://api.staging.cherehapa.ru/v2/serviceGroup/21?key=[key] |
| sport | GET /sport | Возвращает список видов спорта | http://api.staging.cherehapa.ru/v2/sport?key=[key] |
| | GET /sport/[id] | Отображает подробную информацию о виде спорта по id | http://api.staging.cherehapa.ru/v2/sport/2?key=[key] |
| insuranceProduct | GET /insuranceProduct | Возвращает список страховых продуктов, доступных партнеру | http://api.staging.cherehapa.ru/v2/insuranceProduct?key=[key] |
| | GET /insuranceProduct/[id] | Отображает подробную информацию о страховом продукте по id | http://api.staging.cherehapa.ru/v2/insuranceProduct/1?key=[key] |
| request | GET /request | Получает список запросов, сделанных партнером | http://api.staging.cherehapa.ru/v2/request?key=[key]
| | GET /request/[id] | Получает подробную информацию о запросе | http://api.staging.cherehapa.ru/v2/request/91?key=[key] |
| | POST /request/ | Создает новый запрос | http://api.staging.cherehapa.ru/v2/request?insurer%5Bname%5D=Alexander&insurer%5BlastName%5D=Pavlov&insurer%5Bemail%5D=ap%40tsys.pw&dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&tourist%5B0%5D%5BfirstName%5D=Alexander&tourist%5B0%5D%5BlastName%5D=Pavlov&service%5Bmultipolicy%5D=0&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&service%5BtripCancel%5D=0&service%5Bpregnancy%5D=0&service%5Baccident%5D=0&service%5BcivilLiability%5D=0&service%5Bproperty%5D=0&key=[key]&country%5B%5D=italy&_method=post |
| | PUT /request/[id] | Обновляет свойства ранее созданного запроса | http://api.staging.cherehapa.ru/v2/request/468?insurer%5Bname%5D=Alexander&insurer%5BlastName%5D=Pavlov&insurer%5Bemail%5D=ap%40tsys.pw&dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&tourist%5B0%5D%5BfirstName%5D=Alexander&tourist%5B0%5D%5BlastName%5D=Pavlov&service%5Bmultipolicy%5D=0&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&service%5BtripCancel%5D=0&service%5Bpregnancy%5D=0&service%5Baccident%5D=0&service%5BcivilLiability%5D=0&service%5Bproperty%5D=0&key=[key]&country%5B%5D=italy&_method=put |
| | DELETE /request/[id] | Удаляет запрос | http://api.staging.cherehapa.ru/v2/request/10?key=[key]&_method=delete |
| quote | GET /quote | Возвращает стоимость всех продуктов, рассчитанную по данным в запросе | http://api.staging.cherehapa.ru/v2/quote?dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&service%5Bmultipolicy%5D=0&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&service%5BtripCancel%5D=0&service%5Bpregnancy%5D=0&service%5Baccident%5D=0&service%5BcivilLiability%5D=0&service%5Bproperty%5D=0&key=[key]&country%5B%5D=italy |
| | GET /quote/[id] | Возвращает стоимость одного продукта id, рассчитанную по данным в запросе | http://api.staging.cherehapa.ru/v2/quote/39?dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&key=[key]&country%5B%5D=italy&currency=EUR |
| policy | POST /policy/ | Создает новый полис | http://api.staging.cherehapa.ru/v2/policy?insuranceProduct%5B%5D=39&insurer%5Bname%5D=Alexander&insurer%5BlastName%5D=Pavlov&insurer%5Bemail%5D=ap%40tsys.pw&dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&tourist%5B0%5D%5BfirstName%5D=Alexander&tourist%5B0%5D%5BlastName%5D=Pavlov&service%5Bmultipolicy%5D=0&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&service%5BtripCancel%5D=0&service%5Bpregnancy%5D=0&service%5Baccident%5D=0&service%5BcivilLiability%5D=0&service%5Bproperty%5D=0&key=[key]&country%5B%5D=italy&paymentSystem=8&_method=post |
| | DELETE /policy/[id] | Отменяет выписанный ранее полис | http://api.staging.cherehapa.ru/v2/policy/74?key=[key]&_method=delete |
| task | GET /task/[id] | Получает подробную информацию о задаче и текущем статусе выполнения | http://api.staging.cherehapa.ru/v2/task/1986?key=[key] |
| file | GET /file/[id] | Возвращает информацию о файле и ссылку на загрузку | |

## Параметры для создания полиса

- **обязательные** - эти параметры необходимы
- необязательные - эти параметры опциональные

 * **dateStart** - дата начала поездки (22.03.2015)
 * **dateEnd** - дата окончания поездки (25.03.2015)
 * **country[]** - код или id одной или нескольких стран путешествия (количество не ограниченно)
 * countryGroup[] - код или id группы стран (schengen, asia)
 * sport[] - коды видов спортивной активности (surfing, divingCompetition)
 * **insuranceProduct[]** - массив кодов страховых продуктов (1, 57)
 * **service[<код услуги>]** - коды и значения страховых сумм поивыбранным услугам (service[medicine]=30000, service[legal]=1)
 * **insurer** - массив данных о покупателе полиса (страхователе)
 * **insurer[name]** - имя страхователя (Alexander)
 * **insurer[lastName]** - фамилия страхователя (Pavlov)
 * **insurer[email]** - электронная почта страхователя (ap@tsys.pw)
 * insurer[phone] - телефон страхователя в международном формате, без + (79264240454)
 * **tourist[]** - массив данных о туристах
 * **tourist[#][firstName]** - имя туриста (Alexander)
 * **tourist[#][lastName]** - фамилия туриста (Pavlov)
 * **tourist[#][birthday]** - дата рождения туриста (31.12.1982)
 * tourist[#][age] - возраст туриста (можно указывать, когда не известна точная дата рождения)
 * paymentSystem - код платежной системы (для безналичной оплаты paymentSystem=8)
 * currency - код валюты страхования (USD, EUR, RUB, по-умолчанию - USD)
 * card - массив данных о банковской карте пользователя (нужен только в том случае, когда выбрана соответствующая платежная система).
 * card[number] - номер банковской карты (4111111111111111)
 * card[cvc] - код безопасности карты (123)
 * card[month] - месяц окончания срока действия карты (12)
 * card[year] - год окончания срока действия карты (15)
 * card[holder] - фамилия и имя держателя карты (Alexander Pavlov)

Расчёт стоимости страховых продуктов
Для расчета стоимости страховых продуктов необходимо отправить GET-запрос по адресу /quote (для расчета всех продуктов) или /quote/[id] (для расчета конкретного продукта с указанным id).

Пример запроса на расчет всех продуктов:
http://api.staging.cherehapa.ru/v2/quote?dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&service%5Bmultipolicy%5D=0&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&service%5BtripCancel%5D=0&service%5Bpregnancy%5D=0&service%5Baccident%5D=0&service%5BcivilLiability%5D=0&service%5Bproperty%5D=0&key=[key]&country%5B%5D=italy

Пример запроса на расчет продукта с id=39:
http://api.staging.cherehapa.ru/v2/quote/39?dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&key=[key]&country%5B%5D=italy&currency=EUR

Пример ответа:
```
{
   "status": 200,
   "data": {
      "productId": 39,
      "companyId": 26,
      "insuranceSubProductId": 88,
      "territory": {
         "id": 78,
         "code": "t7",
         "countryGroup": [
            "rgs-gte30e",
            "rgs-t1",
            "rgs-t5",
            "rgs-t7"
         ]
      },
      "insuredDays": "1",
      "services": null,
      "sport": null,
      "currency": "EUR",
      "price": 3.21,
      "priceRub": 224.21,
      "infoPerTourist": [
         {
            "age": "32",
            "referenceValue": 1,
            "perTourist": [
               {
                  "result": 3.21,
                  "serviceId": "1"
               }
            ],
            "resultPerTourist": 3.21
         }
      ]
   },
   "request": {
      "dateStart": "22.12.2014",
      "dateEnd": "22.12.2014",
      "currencyId": "EUR",
      "insuredDays": true,
      "dateUpdated": "04.03.2015",
      "dateCreated": "04.03.2015",
      "id": 1335
   }
}
```

При расчете полиса автоматически создается запрос (request), который можно использовать в дальнейшем для выписки страхового полиса. Если есть id запроса, то достаточно передать его параметром requestId вместо всех условий запроса. Если при формировании запроса на расчет не были указаны данные туристов, то их лучше передать вместе с requestId - в этом случае запрос в БД будет обновлен данными из HTTP-запроса.

## Выписка страховых полисов
Для создания страховых полисов по продукту необходимо отправть POST-запрос функции /policy. В ответ на этот запрос будет создана задача выписки полиса, в свойствах которой, по окончании выполнения, будут доступны ссылки на загрузку файлов и дополнительная информация по выписанным полисам. Полисов может быть несколько, в зависимотси от туристов и правил выписки полиса у страховой компании. В этом случае, в ответе будет несколько ссылок на загрузку.

Пример запроса:
http://api.staging.cherehapa.ru/v2/policy?insuranceProduct%5B%5D=39&insurer%5Bname%5D=Alexander&insurer%5BlastName%5D=Pavlov&insurer%5Bemail%5D=ap%40tsys.pw&dateStart=22.12.2014&dateEnd=22.12.2014&tourist%5B0%5D%5Bbirthday%5D=03.01.1983&tourist%5B0%5D%5BfirstName%5D=Alexander&tourist%5B0%5D%5BlastName%5D=Pavlov&service%5Bmultipolicy%5D=0&service%5Bmedicine%5D=30000&service%5BaviaCargo%5D=1500&service%5BtripCancel%5D=0&service%5Bpregnancy%5D=0&service%5Baccident%5D=0&service%5BcivilLiability%5D=0&service%5Bproperty%5D=0&key=[key]&country%5B%5D=italy&paymentSystem=8&_method=post

Ответ:
```
{
   "status": 201,
   "task": {
      "code": "CreateOrderTwoStep",
      "id": 2439,
      "isSuccess": false,
      "isProcessing": true,
      "isCancelled": false,
      "isFatal": false,
      "hasError": false,
      "completeness": 0,
      "currentAction": {
         "description": "Сохранение данных запроса"
      }
   }
}
```

Отслеживать статус выполнения задачи можно опрашивая функцию /task.

Пример запроса (id задачи взят из примера выше):
http://api.staging.cherehapa.ru/v2/task/2439?key=[key]

Если в запросе указать в параметре longPoll временной штамп, то функция task вернет ответ только тогда, когда время изменения задачи будет позже, чем время, обозначенное в штампе.
http://api.staging.cherehapa.ru/v2/task/2439?key=[key]&longPoll=1425482634

Пример промежуточного ответа (completeness - процент выполнения задачи):

```
{
   "status": 200,
   "request": {
      "id": 1319,
      "insurerId": 117,
      "dateStart": "22.12.2014",
      "dateEnd": "22.12.2014",
      "dateVisa": null,
      "insuredDays": 1,
      "currencyId": null,
      "source": null,
      "url": null,
      "dateCreated": "04.03.2015",
      "dateUpdated": "04.03.2015"
   },
   "tourist": [
      {
         "id": 3,
         "birthday": "03.01.1983",
         "firstName": "Alexander",
         "lastName": "Pavlov",
         "secondName": null,
         "age": 32
      }
   ],
   "task": {
      "id": 2439,
      "code": "CreateOrderTwoStep",
      "isSuccess": true,
      "isProcessing": true,
      "isCancelled": false,
      "isFatal": false,
      "hasError": false,
      "completeness": 0.84705883,
      "currentAction": {
         "description": "Ожидание выполнения задач"
      }
   }
}
```

Пример окончательного ответа:
```
{
   "status": 200,
   "task": [
      {
         "id": 1990,
         "code": "ProcessBlockPayment",
         "isSuccess": true,
         "isProcessing": false,
         "isCancelled": false,
         "isFatal": false,
         "hasError": false,
         "completeness": 1,
         "currentAction": false
      },
      {
         "id": 1986,
         "code": "CreateOrderTwoStep",
         "isSuccess": true,
         "isProcessing": false,
         "isCancelled": false,
         "isFatal": false,
         "hasError": false,
         "completeness": 1,
         "currentAction": false
      }
   ],
   "data": {
      "links": {
         "E6011-0000000158-00111": "https://cherehapatst.s3.amazonaws.com/E6011-0000000158-00111.pdf?AWSAccessKeyId=AKIAI2DDUKJRKZSY3JCA&Expires=1422256758&Signature=L5PdmIYH0JbbAaRaJDU8Nfyx0AU%3D"
      }
   },
   "request": {
      "id": 1075,
      "insurerId": 117,
      "dateStart": "22.03.2015",
      "dateEnd": "22.03.2015",
      "dateVisa": null,
      "insuredDays": 1,
      "currencyId": "USD",
      "source": null,
      "url": null,
      "dateCreated": "23.01.2015",
      "dateUpdated": "28.01.2015"
   },
   "tourist": [
      {
         "id": 3,
         "birthday": "03.01.1983",
         "firstName": "Alexander",
         "lastName": "Pavlov",
         "secondName": null,
         "age": 32
      }
   ],
   "order": {
      "id": 173,
      "datePayed": null,
      "dateCanceled": null,
      "statusId": "F",
      "dateStatus": null,
      "price": 191.45,
      "currency": "RUB",
      "discountValue": "0.00",
      "userId": 2,
      "paySystemId": null,
      "dateInsert": null,
      "dateUpdate": null,
      "payVoucherNum": null,
      "payVoucherDate": null,
      "updated1c": "N",
      "id1c": null,
      "version1c": null
   },
   "policy": [
      {
         "id": 442,
         "code": "E6011-0000000158-00111",
         "externalId": 5779906,
         "additionalId": null,
         "companyId": 1,
         "file": 439,
         "insuranceSubProductId": 6,
         "calculationId": 286,
         "insurerId": 117,
         "taskId": 1988,
         "dateCreated": "26.01.2015 06:02:32",
         "dateConfirmed": "26.01.2015 06:38:38",
         "dateUpdated": "26.01.2015 07:04:44",
         "dateCancelled": null
      }
   ],
   "transaction": {
      "id": 254,
      "dateCreate": "26.01.2015 09:08:35",
      "dateUpdate": "26.01.2015 07:10:16",
      "paymentSystemId": 7,
      "orderId": 173,
      "type": 2,
      "status": "success",
      "remoteUrl": "",
      "additionalData": null
   }
}
```
