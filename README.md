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
3. Введите имя таблицы: `users`.
4. Укажите количество столбцов: `6`.

![image](https://github.com/user-attachments/assets/b8b6ea43-bc2a-4bf3-9969-cdc438174251)


5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `username` (VARCHAR(255), UNIQUE
   - `password` (VARCHAR(255))
   - `full_name` (VARCHAR(255))
   - `phone` (VARCHAR(20))
   - `email` (VARCHAR(255))
6. Нажмите **"Сохранить"**.

![image](https://github.com/user-attachments/assets/508ed211-076e-4795-999f-2c4995b9fd41)


##### Таблица 2: Заявки (requests)
1. Вернитесь в базу данных `cleaning_portal`.
2. Нажмите на вкладку **"Создать таблицу"**.
3. Введите имя таблицы: `requests`.
4. Укажите количество столбцов: `10`.
5. Заполните поля:
   - `id` (INT, PRIMARY KEY, AUTO_INCREMENT)
   - `user_id` (INT, FOREIGN KEY)
   - `address` (VARCHAR(255))
   - `phone` (VARCHAR(20))
   - `service_type` (VARCHAR(255))
   - `custom_service` (TEXT)
   - `desired_date` (TIMESTAMP) - По умолчанию: `CURRENT_TIME`
   - `payment_type` (VARCHAR(50))
   - `status` (ENUM('новая', 'в работе', 'выполнено', 'отменено'))
   - `cancel_reason` (TEXT)
6. Нажмите **"Сохранить"**.

![image](https://github.com/user-attachments/assets/29bbb6c7-10a1-4660-a14d-9d7569f5156c)


---

#### Шаг 4: Добавление внешнего ключа (FOREIGN KEY)
1. Перейдите в таблицу `requests`.
2. Нажмите на вкладку **"Структура"**.
3. Нажмите на кнопку **"Связи"**.

![image](https://github.com/user-attachments/assets/ed13e6f2-d505-4f0d-8c82-852eeb24e344)

4. В выпадающем списке столбец выберите `user_id`
5. В таблице выберите `users`
6. Последний столбец - `id`
7. Нажмите **"Сохранить"**.

![image](https://github.com/user-attachments/assets/d2a89073-5a74-41b5-bbab-380be9c3b9d6)



---

#### Шаг 5: Проверка базы данных
1. Убедитесь, что таблицы созданы и связаны.
2. Проверьте, что все поля заполнены корректно.
3. Вы можете добавить тестовые данные вручную через вкладку **"Вставить"**.
4. Проверьте связи во вкладке **"Дизайнер"**

![image](https://github.com/user-attachments/assets/4a52b7a0-cb69-4cf4-a391-81ab83f2ec19)


---

### Итог
Теперь у вас есть база данных `cleaning_portal` с двумя таблицами: `users` и `requests`. Эти таблицы связаны через внешний ключ `user_id`. 

### [Следующая лекция](https://github.com/petrocollege-web/2.-Yii2-install/tree/main)
