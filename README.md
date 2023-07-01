# DE-DB-2.1-LOG_STRUCT
## Задание:
- Разработать логическую структуру БД для создания "Библиотеки" с использованием следующей информации:
- Читатели (Номер читательского билета, ФИО, Адрес,  Телефон)
- Книги (Шифр книги, Название, Автор(ы), Год издания, Объем (в страницах), Цена, Количество экземпляров в фонде)
- Издательства (Название, Город)

## Необходимо в логической структуре БД:

# Выявить все сущности в разрабатываемой БД.
# Определить связи между сущностями.
# Пояснить выбор связей (почему вы решили создать именно такие связи).
# Определить первичные и внешние ключи.

### Логика решения задачи:

1. Для построения логической схемы по условию задания выделил следующие основные сущности: 
 - Читатели
 - Книги
 - Издательства
 - Города
 - Авторы
   
Помимо этого необходимо было определить сущности-связки для построения взаимодействия таблиц:
 - Выдача книги
 - Экземпляр книги
 - Книга-Автор
 - Издательство-город

2. Далее определяем связи между таблицами
 - Выдача книги - многие ко кмногим, т.к. Читатель может взять несколько книг, а книгу может взять несколько читателей (реализовано посредством сущности-связки , где связи один (Читатели или экземпляры книги) ко многим (ЧВыдача Книги))
 - Книги и Авторы - многие ко кмногим, т.к. у Книги может быть несколько Авторов, а у Автора может быть несколько Книг (реализовано посредством сущности-связки , где связи один(Авторы или Книги) ко многим(Книги_Авторы))
 - Издательства - один ко многим, т.к. у Издательства может быть несколько опубликованных книг, но у книги конкретное издательство.
 - Издательства и Города - многие ко кмногим, т.к. Издательство может иметь несколько филиалов в разных Городах, а в одном Городе может быть несколько Издательств (реализовано посредством сущности-связки , где связи один(Издательства или Города) ко многим(Издательства_Города))


4. Типы ключей по сущностям:
- Читатели: поле Номер Билета - первичный ключ;
- Книги: поле Шифр книги - первичный ключ;
- Книга-автор: поле ID Автора - внешний ключ к таблице "Авторы", поле Шифр Книги - внешний ключ к таблице "Книги", ID Книга-автор - первичный ключ;
- Авторы: ID_автора - первичный ключ;
- Книги_Авторы: поле Шифр_книги - внешний ключ к таблице "Книги", поле id_автора - внешний ключ к таблице "Авторы", оба этих поля составной первичный ключ таблицы;
- Издательство: поле ID_издательства - первичный ключ;
- Города: поле ID_города - первичный ключ;
- Издательство-Города: поле ID_издательства - внешний ключ к таблице "Издательства", поле ID_города - внешний ключ к таблице "Города", ID Издательство-города - первичный ключ;
- Экземпляр книги: Шифр книги - внешний ключ к таблице "Книги", поле ID_издательства - внешний ключ к таблице "Издательства", ID (экземпляра) книги - первичный ключ;
- Выдача книги: номер читательского билета - внешний ключ к таблице "Читатели", ID Выдачи экземпляра - первичный ключ;