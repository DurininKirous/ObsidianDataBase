Язык управления данными (DML) - это часть языка SQL, которая позволяет пользователям с помощью специальных команд получать, вставлять, изменять или удалять данные в базе данных.
Основные команды для PostgreSQL:
	1. SELECT - получать строки из таблицы или из представления.
		1. SELECT user_id, username, password FROM users;
	2. INSERT - добавить строки в таблицу.
		1. INSERT INTO users(firstname, lastname, username, password) VALUES ('max','weber','web_admin','web_admin_strong_password');
	3. UPDATE - изменить строки таблицы, поменять там какой-либо столбец.
		1. UPDATE users SET username = 'Dramatic' WHERE username = 'hero1';
	4. DELETE - удалить записи (строки) таблицы
		1. DELETE FROM users WHERE user_id=2;
		2. DELETE FROM users;
[[Data Manipulation Language (DML)]]
[[SQL Language]]
