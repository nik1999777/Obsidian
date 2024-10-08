  

  

[https://jira.autotests.cloud/browse/QAGDEV-272](https://jira.autotests.cloud/browse/QAGDEV-272)

# RELEASE NOTES:

## Работа с пользователями (API + частично UI):

1. Создание нового пользователя (+ редактирование и получение сведений).
2. Изменение логина и пароля пользователя (как со стороны самого пользователя, так и со стороны менеджера).
3. Блокировка и разблокировка пользователя.
4. Изменение ролей пользователя (список ролей: STUDENT, ADMIN, MANAGER, LECTOR, MENTOR и MASTER).
5. Авторизация пользователя.

## Работа с лекциями (API + частично UI):

1. Создание новой лекции (+ редактирование и удаление).
2. Получение сведений о лекции: материал урока и домашнее задание (отдельные запросы).
3. Создание уровней сложности домашнего задания (+ редактирование, удаление и получение сведений).

## Работа с курсами (API + частично UI):

1. Создание нового курса (+ редактирование и удаление).
2. Добавление лекций в курс.
3. Получение сведений о курсе: информация как о самом курсе, так и о входящем в него лекциям.

## Работа с покупками (API):

1. Создание тарифов на основании курса (+ редактирование, удаление и получение сведений).Доступность сдачи дз студентом регулируется именно на уровне тарифа.
2. Оформление покупок пользователям.
3. Получение списка покупок пользователя как со стороны самого пользователя, так и со стороны менеджера.

## Работа с домашним заданием (API + частично UI):

1. Отправка на проверку ответа на домашнее задание студентом (+ редактирование, получение и удаление).
2. Взять ответ на домашнее задание на проверку (со стороны наставника).
3. Принять либо отклонить ответ на домашнее задание (со стороны наставника).
4. Отправить комментарий к ответу на домашнее задание (+ редактирование, удаление и получение с учетом пагинации).

  

# **Отчет о тестировании:**

## **Прогон автотестов (api часть).**

Allure отчет можно посмотреть [allure-results.zip](https://jira.autotests.cloud/secure/attachment/10901/10901_allure-results.zip) (распаковать и запустить командой _allure serve_).

## **Ручное тестирование (ui часть):**

### **Студент с тарифом с поддержкой проверки домашнего задания:**

1. Получение сведений лекции с домашним заданием.
2. Получение сведений лекции без домашнего задания.
3. Отправка на проверку ответа на домашнее задание.
4. Валидация во время отправки на проверку ответа на домашнее задание (пустое поле, превышение max размера - 2к символов).
5. Редактирование уже существующего ответа на домашнее задание.
6. Валидация во время редактирование уже существующего ответа на домашнее задание (пустое поле, превышение max размера - 2к символов).
7. Отображение ответа на домашнее задание в статусе NEW.
8. Отображение ответа на домашнее задание в статусе IN REVIEW.
9. Отображение ответа на домашнее задание в статусе APPROVED.
10. Отображение ответа на домашнее задание в статусе NOT APPROVED.
11. Отправка комментария к ответу на домашнее задание.
12. Валидация во время отправки комментария (пустое поле, превышение max размера - 10к символов).
13. Отправка нескольких комментариев.
14. Отправка комментариев разными пользователями.
15. Редактирование комментария.
16. Валидация во время редактирования комментария (пустое поле, превышение max размера - 10к символов).
17. Пагинация комментариев во время загрузки (при большом кол-ве комментариев).

### **Студент с тарифом без поддержки проверки домашнего задания:**

1. Получение сведений лекции с домашним заданием.
2. Получение сведений лекции без домашнего задания.
3. Отображение заглушки "Купить тариф с ДЗ".