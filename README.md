# PostgreSQL Task 1: Simple Database Schema

## Задание
Создайте базу данных `university` с таблицами:
- `students` (id SERIAL PRIMARY KEY, name VARCHAR(100) NOT NULL, email VARCHAR(100) UNIQUE NOT NULL, age INTEGER CHECK (age >= 18))
- `courses` (id SERIAL PRIMARY KEY, title VARCHAR(200) NOT NULL, credits INTEGER CHECK (credits > 0))
- `enrollments` (student_id INTEGER REFERENCES students(id), course_id INTEGER REFERENCES courses(id), grade CHAR(1) CHECK (grade IN ('A','B','C','D','F')), PRIMARY KEY (student_id, course_id))

Добавьте 3-4 студента, 2-3 курса и несколько записей о зачислении.

## Что нужно сделать
1. Создайте файл `solution.sql` в корне репозитория.
2. В файле напишите SQL-скрипт, который:
   - Создаёт базу данных `university` (если не существует)
   - Создаёт таблицы с указанными ограничениями
   - Вставляет тестовые данные
   - (Опционально) добавляет несколько полезных запросов

## Как запустить локально
```bash
# Запустить PostgreSQL (если не запущен)
docker run --name postgres-test -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres:15

# Выполнить скрипт
psql -h localhost -U postgres -d postgres -f solution.sql
```

## Как проверяются тесты
- Тесты подключаются к временной базе данных PostgreSQL
- Выполняют ваш `solution.sql`
- Проверяют наличие таблиц, ограничений и данных
- Валидируют структуру и целостность

## Примечания
- Используйте стандартный синтаксис PostgreSQL
- Все ограничения (constraints) должны быть явно указаны
- Данные должны быть реалистичными и соответствовать ограничениям
