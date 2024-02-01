# Яндекс Практикум

Во время обучения в [Яндекс Практикуме](https://practicum.yandex.ru/qa-engineer/) мною было протестировано 6 приложений Яндекса.<br />

Здесь я расскажу про самый масштабный проект - это тестрирование веб- и мобильной версии, а также API приложения Яндекс Самокат. Я спроектировал и выполнил проверки приложения Яндекс Самокат, оформил баг-репорты. Тестирование API приложения я проводил, используя инструмент Postman. Работу в Charles я покажу при тестировании фичи, которую реализовали только во фронтенде, а бэкенд ещё не был готов.
Все баг-репорты описаны в YouTrack.


## Описание проекта:

Приложение Яндекс Самокат - это сервис, который позволяет арендовать электрический самокат на несколько дней.
<a name="headers1"/>**1. Тест-анализ** <br />
Задача: Декомпозировать и визуализировать требования, исключить серые зоны<br />
Инструменты: Figma, draw.io
Результат: Построение mindmap для формы заказа самоката

Прежде чем проектировать проверки, необходимо определить, что предстоить тестировать, проанализировать требования и макеты, составить список объектов тестирования. Для проведения тестирования веб-приложения Яндекс Самокат макеты были представлены в Figma. Далее каждый объект тестирования необходимо декомпозировать и визуализировать, а затем найти серые зоны.

Mindmap можно посмотреть в архиве.

Декомпозируя требования до атомарного уровня, мне удалось закрыть много серых зон.

После проведения тест-анализа переходим к проектированию тестовой документации. Техники тест-дизайна, которые я применял: разбиение по классам эквивалентности и выделение граничных значений, оптимизация количества проверок.

*2.1 Составление чек-листов* <br />

Пример составления чек-листа для формы "Статус заказа" [здесь](https://docs.google.com/spreadsheets/d/18hV4HR-UZvtfX5aoAEnhuhZeLBvwdoAAsKLePHcO2uA/edit?usp=sharing) <br />

Применение техник тест-дизайна хорошо видно при составлении проверок на валидацию полей для формы заказа самоката. Посмотреть, как я применяла техники тест-дизайна можно, перейдя по [ссылке](https://docs.google.com/spreadsheets/d/18hV4HR-UZvtfX5aoAEnhuhZeLBvwdoAAsKLePHcO2uA/edit?usp=sharing) <br />

*2.2 Составление тест-кейсов* <br />

Пример составления тест-кейса очень хорошо представлен при тестировании мобильной версии приложения Яндекс Самокат.<br /> [Здесь](https://docs.google.com/spreadsheets/d/18hV4HR-UZvtfX5aoAEnhuhZeLBvwdoAAsKLePHcO2uA/edit?usp=sharing) можно посмотреть тест-кейсы, составленные при тестировании нотификации и отсутствии интернет-соединения.<br />
Тестирование мобильной версии приложения Яндекс Самокат я проводила в эмуляторе Android Studio и на реальном устройстве.<br />

<a name="headers3"/>**3. Тестирование API** <br />
Документация к API была представлена в Apidoc<br />

<img src="https://github.com/Shvarikova-Elena/Yandex.Scooter/blob/main/pics/Apidoc.jpg" width=70% height=70%> <br />

Тестирование API проводила через Postman. Чек-лист и результаты выполнения тестов API приложения Яндекс Самокат можно посмотреть по [ссылке](https://docs.google.com/spreadsheets/d/18hV4HR-UZvtfX5aoAEnhuhZeLBvwdoAAsKLePHcO2uA/edit?usp=sharing)<br />

<a name="headers4"/>**4. Баг-репорты** <br />
После проведения тестирования приложения Яндекс Самокат было обнаружено порядка 50 багов. Все баг-репорты были заведены в YouTrack.<br />
Примеры оформления баг-репортов:<br />
	[для веб-приложения](https://elena-s.youtrack.cloud/issue/59M-84/Mozhno-vybrat-proshedshuyu-datu-v-pole-Kogda-privezti-samokat-na-ekrane-Sdelat-zakaz-v-prilozhenii-Yandeks-Samokat)<br />
	[для мобильного приложения](https://elena-s.youtrack.cloud/issue/59M-119/Vsplyvayushee-okno-soderzhit-tekst-Net-dostupa-k-internetu-pri-otsutstvii-internet-soedineniya-v-mobilnom-prilozhenii-Yandeks)<br />
	[для API](https://elena-s.youtrack.cloud/issue/59M-122/Uspeshnoe-sozdanie-uchetnoj-zapisi-pri-otpravke-api-v1-courier-zaprosa-v-pole-login-esli-vvesti-nekorrektnye-dannye)<br />

<a name="headers5"/>**5. Работа в Charles** <br />
Согласно требованиям в приложение была добавлена фича (добавлен пятый статус), которую реализовали только во фронтенде, бэкенд ещё не был готов.<br />
Задача: протестировать реализацию на фронтенде, не дожидаясь бэкенда.<br />
Для автоматического перехвата и изменения ответа от бэкенда я использовала функцию Map Local в Charles. Таким образом, мне удалось изменить статус заказа и протестировать его, в результате чего был обнаружен [баг](https://elena-s.youtrack.cloud/issue/59M-107/Nadpis-Arenda-zakonchitsya...-v-pyatom-statuse-kogda-vremya-arendy-uzhe-zakonchilos-na-ekrane-Status-zakaza-v-prilozhenii).<br />

<a name="headers6"/>**6. Работа с БД** <br />
По требованиям БД состояла из двух таблиц: Couriers и Orders. Первая таблица содержала данные о курьерах, вторая — данные о заказах.<br />
В требованиях к бэкенду приложения было условие, что при удалении учетной записи курьера связанные заказы в БД в таблице Orders должны быть стёрты. Проверить данное условие можно было только подключившись к удалённому серверу через консоль.  Наличие заказа я проверяла с помощью команды:
```
SELECT * FROM "Orders";
```
