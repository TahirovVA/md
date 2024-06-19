# 1. Тахиров Владимир Азадович ИС22/9-1
# 2. База данных библиотеки

## Описание БД

Создана база данных для управления библиотекой. Она включает таблицы для хранения информации о книгах, авторах, читателях и выдачах книг. Каждая таблица имеет свои атрибуты и связи с другими таблицами.

### 2. Описание сущностей (таблиц)

#### 2.1. Таблица Authors (Авторы)
- **author_id**: INTEGER PRIMARY KEY AUTOINCREMENT - уникальный идентификатор автора.
- **name**: TEXT NOT NULL - имя автора.
- **birth_year**: INTEGER - год рождения автора.

Пример записи:
| author_id | name             | birth_year |
|-----------|------------------|------------|
| 1         | Лев Толстой      | 1828       |
| 2         | Федор Достоевский| 1821       |
| 3         | Иван Тургенев    | 1818       |

#### 2.2. Таблица Books (Книги)
- **book_id**: INTEGER PRIMARY KEY AUTOINCREMENT - уникальный идентификатор книги.
- **title**: TEXT NOT NULL - название книги.
- **author_id**: INTEGER - идентификатор автора, внешний ключ на таблицу Authors.
- **published_year**: INTEGER - год публикации книги.
- **genre**: TEXT - жанр книги.

Пример записи:
| book_id | title                    | author_id | published_year | genre |
|---------|--------------------------|-----------|----------------|-------|
| 1       | Война и мир              | 1         | 1869           | Роман |
| 2       | Преступление и наказание | 2         | 1866           | Роман |
| 3       | Отцы и дети              | 3         | 1862           | Роман |

#### 2.3. Таблица Readers (Читатели)
- **reader_id**: INTEGER PRIMARY KEY AUTOINCREMENT - уникальный идентификатор читателя.
- **name**: TEXT NOT NULL - имя читателя.
- **email**: TEXT - электронная почта читателя.

Пример записи:
| reader_id | name         | email               |
|-----------|--------------|---------------------|
| 1         | Иван Иванов  | ivanov@example.com  |
| 2         | Мария Петрова| petrova@example.com |
| 3         | Алексей Смирнов| smirnov@example.com|

#### 2.4. Таблица Loans (Выдачи)
- **loan_id**: INTEGER PRIMARY KEY AUTOINCREMENT - уникальный идентификатор выдачи.
- **book_id**: INTEGER - идентификатор книги, внешний ключ на таблицу Books.
- **reader_id**: INTEGER - идентификатор читателя, внешний ключ на таблицу Readers.
- **loan_date**: TEXT NOT NULL - дата выдачи книги.
- **return_date**: TEXT - дата возврата книги.

Пример записи:
| loan_id | book_id | reader_id | loan_date  | return_date |
|---------|---------|-----------|------------|-------------|
| 1       | 1       | 1         | 2023-01-10 | 2023-02-10  |
| 2       | 2       | 2         | 2023-01-15 | NULL        |
| 3       | 3       | 3         | 2023-01-20 | NULL        |

### 3. Демонстрация работы функции UNION + описание результирующей таблицы

```sql
SELECT name AS person_name, 'Author' AS role FROM Authors
UNION
SELECT name AS person_name, 'Reader' AS role FROM Readers;
```
![union](![image](https://github.com/TahirovVA/md/assets/158167377/e4c9884a-be46-4669-8c76-ec99ab652143)
)
