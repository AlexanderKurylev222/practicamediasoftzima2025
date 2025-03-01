Задание 2.
Основные функции данного приложения (список должен быть составлен в порядке убывания важности функций для пользователя).
1.Создание и управление списками покупок
Создание нового списка покупок.
Редактирование существующего списка (добавление, удаление, изменение товаров).
Просмотр списка покупок.

2.Отметка купленных товаров
Возможность помечать товары как купленные.
Автоматическое обновление статуса списка.

3. Синхронизация данных с сервером
Сохранение данных для доступа с разных устройств.
Автосинхронизация в режиме онлайн.


4. Работа в оффлайн-режиме
4.1 Возможность создавать, редактировать и просматривать списки без доступа к интернету.

5. Уведомления о состоянии списка
Напоминания о необходимости завершить покупки.
Уведомления об изменениях списка, если он синхронизирован с другими пользователями.

6. Шаблоны списков
Создание шаблонов для часто используемых покупок.
Быстрое добавление товаров из шаблонов в список.

7. Поделиться списком
Возможность отправить список другим пользователям или через мессенджеры.
Совместное редактирование списка в режиме реального времени.

8. Категоризация товаров
Упорядочивание товаров по категориям (продукты, бытовая химия и т.д.).
Фильтрация списка по категориям.

9. История покупок
Просмотр ранее купленных товаров.
Возможность восстанавливать списки из истории.

10 Поиск товаров в списк
10.1 Быстрый поиск по названию или категории.

11. Визуализация данных
Статистика по покупкам (например, на что тратится больше всего).
Графики и диаграммы для анализа расходов.

Задание 3.

Процесс синхронизации данных между клиентом и сервером (добавление и удаление списка, наполнение и редактирование списка, покупка/«откупка продукта» и т.д.). Представить все в диаграммах UML, API методах и других представлениях, также составить ER-диаграмму сущностей

API методы
Метод: POST
Добавление:
Запрос { "name": "Grocery Shopping" }
Ответ { "list_id": "12345", "name": "Grocery Shopping", "created_at": "2025-02- 13T10:00:00Z" }
Метод: DELETE
Удаление:
Удаление пример: { "message": "List deleted successfully" }
Метод: POST
Добавление товара в список:
Запрос: { "name": "Milk", "quantity": 2 }

Ответ { "item_id": "67890", "name": "Milk", "quantity": 2, "purchased": false }
Метод: PUT
Редактирование товара
Запрос : { "name": "Almond Milk", "quantity": 1, "purchased": true }


Задание 4.
Подготовить прототип одного из экранов мобильного приложения и описать пользовательский интерфейс для данного экрана (например, покупка товара).
https://www.figma.com/design/zvDbNXyl26qpUqiPD5kJka/Untitled?node-id=0- 1&p=f&t=UgzmMqra90qIciaX-0


Задание 5.
Подготовить подробное описание функции покупки товара, которую можно было бы использовать в качестве постановки задачи для разработки (помимо текстового описания использовать UML диаграммы, указать используемые API методы, передаваемые и получаемые параметры, описать процесс хранения информации о покупках пользователя).


UML Диаграмма

Api методы
Получение информации о заказе.

Метод GET:
GET /orders/{order_id}
Пример: { "order_id": "12345", "items": [ { "product_id": "67890",
"name": "Продукт 1", "quantity": 2, "price": 500 } ], "total_price": 1000 }
Обновление информации о заказе.
Метод: PUT /orders/{order_id}:
Пример: { "items": [ { "product_id": "67890", "quantity": 3 } ] }
ответ: { "message": "Order updated successfully" }


Задание 6:
Основные, на ваш взгляд, сложности разработки такого приложения. Вопросы, возникшие при выполнении тестового задания, которые вы бы задали заказчику

Основные сложности разработки:

Синхронизация данных — нужно синхронизировать изменения на разных устройствах.
Управление состоянием — обработка актуальности списка покупок и ошибок при сети.
Безопасность — защита данных пользователей и использование безопасных протоколов.
Уведомления — реализация системы уведомлений для напоминаний о покупках.
Масштабируемость — сервер должен справляться с большим количеством пользователей.
Платформенная совместимость — поддержка разных ОС и экранов.

Хранение данных — кэширование и локальное хранение данных на устройствах.

Вопросы заказчику:
Как обрабатывать дублирующиеся товары в списках?
Какие категории товаров должны быть?
Должны ли пользователи редактировать товары?
Нужно ли синхронизировать данные между устройствами?
Требуется ли аутентификация пользователей?
Какие требования к интерфейсу?
Есть ли потребность в интеграции с другими сервисами?



Задание 7:
Есть таблицы Books и Authors, где AuthorId табл. Books равно Id табл. Authors. Необходимо написать SQL-запрос, чтобы найти: 1. Общую стоимость книг для каждого автора и отсортировать результат в порядке убывания; 2. Стоимость книг автора превышает 1500; 3. Вывести авторов с количеством книг; 4. Получить автора без книг.
Общая стоимость книг для каждого автора, отсортированная по убыванию:
SELECT a.Name AS AuthorName, SUM(b.Price) AS TotalCost FROM Authors a JOIN Books b ON a.Id = b.AuthorId GROUP BY a.Name ORDER BY TotalCost DESC;

Стоимость книг автора превышает 1500:
SELECT a.Name AS AuthorName, SUM(b.Price) AS TotalCost FROM Authors a JOIN Books b ON a.Id = b.AuthorId GROUP BY a.Name HAVING SUM(b.Price) > 1500;

Вывести авторов с количеством книг:
SELECT a.Name AS AuthorName, COUNT(b.Id) AS BookCount FROM Authors a LEFT JOIN Books b ON a.Id = b.AuthorId GROUP BY a.Name;

Получить автора без книг:
SELECT a.Name AS AuthorName FROM Authors a LEFT JOIN Books b ON a.Id = b.AuthorId WHERE b.Id IS NULL;
