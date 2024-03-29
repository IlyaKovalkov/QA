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

Применение техник тест-дизайна хорошо видно при составлении проверок на валидацию полей для формы заказа самоката. Посмотреть, как я применял техники тест-дизайна можно в архиве

*2.2 Составление тест-кейсов* <br />

Пример составления тест-кейса очень хорошо представлен при тестировании мобильной версии приложения Яндекс Самокат.<br /> Можно посмотреть тест-кейсы, составленные при тестировании нотификации и отсутствии интернет-соединения.<br />
Тестирование мобильной версии приложения Яндекс Самокат я проводил в эмуляторе Android Studio.<br />

<a name="headers3"/>**3. Тестирование API** <br />
Документация к API была представлена в Apidoc<br />

Тестирование API проводил через Postman. Чек-лист и результаты выполнения тестов API приложения Яндекс Самокат можно посмотреть в архиве

<a name="headers4"/>**4. Баг-репорты** <br />
Все баг-репорты были заведены в YouTrack.<br />

<a name="headers5"/>**5. Работа в Charles** <br />
Согласно требованиям в приложение была добавлена фича (добавлен пятый статус), которую реализовали только во фронтенде, бэкенд ещё не был готов.<br />
Задача: протестировать реализацию на фронтенде, не дожидаясь бэкенда.<br />
Для автоматического перехвата и изменения ответа от бэкенда я использовал функцию Map Local в Charles. Таким образом, мне удалось изменить статус заказа и протестировать его, в результате чего был обнаружен баг.

<a name="headers6"/>**6. Работа с БД** <br />
По требованиям БД состояла из двух таблиц: Couriers и Orders. Первая таблица содержала данные о курьерах, вторая — данные о заказах.<br />
В требованиях к бэкенду приложения было условие, что при удалении учетной записи курьера связанные заказы в БД в таблице Orders должны быть стёрты. Проверить данное условие можно было только подключившись к удалённому серверу через консоль.  Наличие заказа я проверял с помощью команды:
```
SELECT * FROM "Orders";
```
