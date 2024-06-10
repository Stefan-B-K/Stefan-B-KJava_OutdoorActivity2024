# OutdoorActivity2024 (Project 2/3 of Methodia Workshop / Self-training 2024)

## Игра на федербал

Напишете програма, която определя възможните времеви интервали за игра на федербал на открито пространство, в които метеорологичните условия са подходящи. Примерни стойности:
- поривите на вятъра трябва да са по-малки от 5 км/ч;
- вероятността за валежи да бъде по-малка от 50%;
- трябва да е светло (след изгрев слънце и преди залез слънце);
- температурата да бъде между 10 и 30 градуса Целзий;
- трябва да има поне два часа с тези условия;
- уикендите и облачното време (над 50% облачна покривка) са за предпочитане.

Изведете възможните времеви интервали до 2 дена напред. Трябва да изведете в конзолата диапазон от часове за всеки ден, в който има подходящи условия.
Пример за форматиране на изходните данните:
```json
[
{
"date": "2023-05-15",
"hours": ["10-13", "15-19"]
},
{
"date": "2023-05-16",
"hours": ["08-11", "14-16", "17-20"]
},
{
"date": "2023-05-17",
"hours": ["14-20"]
}
]
```

Информацията за часовете е за всеки кръгъл час, т.е."10-13" означава, че от 10:00 до 13:00 часа е подходящо за игра.
За нуждите на задачата можете да ползвате, която и да е безплатна уеб услуга, която предоставя прогноза за времето. Една от тях е https://www.weatherapi.com/. Разгледайте и разучете какво Ви предоставя API на секция Forecast API.

````diff
+ Implemented two interchangable weather forecast services (through ForecastService interface) - with WehaterAPI and OpenWeatherMap API
````
![](https://github.com/Stefan-B-K/Java_ImageBlur2024/blob/main/src/main/resources/images/Screenshot1.png)

## Допълнение 1
Потребителят да може да дефинира файл (ръчно), където да описва условията за различни видове спорт. Форматът на този файл го определете вие. Изходът на програмата вече ще извежда подходящите интервали за всеки вид спорт.

## Допълнение 2
Програмата да може да се стартира в наблюдаващ режим, изпълнявайки се продължително време, тоест ще е вид service. През определен интервал ще извлича прогнозата за времето. При достигане на определени критерии, ще изпраща мейл. Критериите отново потребителят ги задава чрез файл. Например, да прати мейл ако за следващия уикенд има подходящи условия за даден спорт в определен часови интервал. Опционално може да са и всички почивни дни. За целта [този](https://bulgaria.workingdays.org/setup) или подобен сървис би ви свършил работа.

### Изпращане на мейл
Може да използвате стандартния SMTP клиент за Java като си добавите тази зависимост:
```
implementation 'com.sun.mail:jakarta.mail:2.0.1'
```

#### През Gmail
Ако не искате да създадете OAuth2 оторизация, по простият вариант е да генерирате парола за приложение. Имайте предвид, че ще трябва да създадете парола, с която да достъпите вашия личен акаунт, затова внимавайте да не я къмитнете в репозиторито. За малко по-голяма сигурност може да направите това допълнение заедно с допълнение 3. Използвайки вашия акаунт, ще пращате мейли от ваше име. За да настроите парола за вашия клиент, вижте https://support.google.com/mail/answer/185833?hl=en Базови настройки:

- SMTP host - smtp.gmail.com
- port - 25/587/465

Ако използвате порт 465 в настройките на Java mail трябва да сложите `mail.smtp.ssl.enable` - true, в противен случай `mail.smtp.starttls.enable` - true

## Допълнение 3
При откриване на подходящи условия за спорт, програмата трябва да създаде събитие в Google Calendar.
Детайлите около събитието можете сами да ги определите - създаване/редактиране/изтриване на събитие, припокриващи се събития, цвят, участници, местоположение, нотификация и т.н.

Полезни линкове за разработване на допълнение 3:
- https://auth0.com/docs/get-started/auth0-overview
- https://console.cloud.google.com/
- https://developers.google.com/workspace/guides/configure-oauth-consent
- https://developers.google.com/calendar/api/guides/overview