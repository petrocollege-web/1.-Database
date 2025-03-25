### Лекция 1: Создание базы данных в phpMyAdmin

#### Шаг 1: Вход в phpMyAdmin
1. Откройте браузер и перейдите по адресу, где установлен phpMyAdmin (обычно это `http://localhost/phpmyadmin`).
2. Введите логин и пароль для доступа к MySQL (по умолчанию логин — `root`, пароль может быть пустым или заданным вами).

![image](https://github.com/user-attachments/assets/722e7064-266a-4c19-b85a-bbdd0c2849bd)


---

#### Шаг 2: Создание базы данных
1. На главной странице phpMyAdmin найдите раздел **"Базы данных"**.
2. В поле **"Создать базу данных"** введите имя базы данных, например, `cleaning_portal`.

![image](https://github.com/user-attachments/assets/8324891d-1d5f-4a55-8042-4eabdc28e7e4)

3. Выберите кодировку `utf8mb4_general_ci` (это обеспечит поддержку кириллицы и специальных символов).
4. Нажмите кнопку **"Создать"**.

![image](https://github.com/user-attachments/assets/614a60f0-00f0-4ebb-a98e-ad3320918641)


---

#### Шаг 3: Создание таблиц
Теперь создадим таблицы для нашей базы данных. Мы будем создавать таблицы вручную через интерфейс phpMyAdmin.

##### Таблица 1: Пользователи (users)
1. Перейдите в созданную базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `user`.
4. Укажите количество столбцов: `6`.



5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `username` (VARCHAR(255), UNIQUE
   - `password` (VARCHAR(255))
   - `full_name` (VARCHAR(255))
   - `phone` (VARCHAR(20))
   - `email` (VARCHAR(255))
   - `role_id` (INT) - По умолчанию - 1
6. Нажмите **"Сохранить"**.


![image](https://github.com/user-attachments/assets/948cdc76-6204-4aa2-a2e6-cc8d626ee106)




##### Таблица 2: Тип оплаты (payment)
1. Перейдите в созданную базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `payment`.
4. Укажите количество столбцов: `2`.


![image](https://github.com/user-attachments/assets/e8ad55ba-3687-4fd6-b2c9-fbf3471d5177)



5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `type` (VARCHAR(255))
   
6. Нажмите **"Сохранить"**.

##### Таблица 3: Роли (role)
1. Перейдите в созданную базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `role`.
4. Укажите количество столбцов: `2`.


![image](https://github.com/user-attachments/assets/1e6212b5-fe68-42ae-b362-b5cf01129dd5)



5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `type` (VARCHAR(255))
6. Нажмите **"Сохранить"**.

##### Таблица 4: Тип работы (service)
1. Перейдите в созданную базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `service`.
4. Укажите количество столбцов: `2`.


![image](https://github.com/user-attachments/assets/eb000125-8f26-42cc-8780-81572d4a2beb)



5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `type` (VARCHAR(255))
6. Нажмите **"Сохранить"**.

##### Таблица 5: Статус заявки (status)
1. Перейдите в созданную базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `status`.
4. Укажите количество столбцов: `2`.


![image](https://github.com/user-attachments/assets/d8e43f2a-19a9-4b1d-8e3a-14687b896537)




5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `type` (VARCHAR(255))
6. Нажмите **"Сохранить"**.

##### Таблица 6: Заявки (requests)
1. Вернитесь в базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `requests`.
4. Укажите количество столбцов: `10`.
5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `user_id` (INT, FOREIGN KEY)
   - `address` (VARCHAR(255))
   - `phone` (VARCHAR(20))
   - `service_id` (INT)
   - `custom_service` (TEXT) - По умолчанию: NULL
   - `desired_date` (TIMESTAMP) - По умолчанию: `CURRENT_TIME`
   - `payment_id` (VARCHAR(50))
   - `status_id` (INT)
   - `cancel_reason` (TEXT)
6. Нажмите **"Сохранить"**.

![image](https://github.com/user-attachments/assets/fa98087a-d098-4726-91ff-af9bff49079f)




---

#### Шаг 4.1: Добавление внешнего ключа в заявках (FOREIGN KEY)
1. Перейдите в таблицу `requests`.
2. Нажмите на вкладку **"Структура"**.
3. Нажмите на кнопку **"Связи"**.

![image](https://github.com/user-attachments/assets/ed13e6f2-d505-4f0d-8c82-852eeb24e344)

4. В выпадающем списке столбец выберите `user_id`
5. В таблице выберите `users`
6. Последний столбец - `id`
7. Проделайте те же действия с другими таблицами, как на скриншоте ниже
8. Нажмите **"Сохранить"**.

![image](https://github.com/user-attachments/assets/8b6525bb-dcf1-4266-94e5-13f87fc6b6b5)

#### Шаг 4.2: Добавление внешнего ключа в пользоватлях (FOREIGN KEY)
1. Перейдите в таблицу `user`.
2. Нажмите на вкладку **"Структура"**.
3. Нажмите на кнопку **"Связи"**.
4. В выпадающем списке столбец выберите `role_id`
5. В таблице выберите `role`
6. Последний столбец - `id`
7. Проделайте те же действия с другими таблицами, как на скриншоте ниже
8. Нажмите **"Сохранить"**.


![image](https://github.com/user-attachments/assets/b786c8ce-dad4-497d-b067-db39d5696fc3)



---

#### Шаг 5: Проверка базы данных
1. Убедитесь, что таблицы созданы и связаны.
2. Проверьте, что все поля заполнены корректно.
3. Вы можете добавить тестовые данные вручную через вкладку **"Вставить"**.
4. Проверьте связи во вкладке **"Дизайнер"**

![image](https://github.com/user-attachments/assets/2569adf0-041d-4234-a53f-d64a23616446)



---

### Итог
Теперь у вас есть база данных `cleaning_portal`.

### [Следующая лекция](https://github.com/petrocollege-web/2.-Yii2-install/tree/main)
