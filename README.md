![2024-11-24_14-23-21](https://github.com/user-attachments/assets/32f97e96-9d12-4ea2-bccb-b0dc7a695be5)

Описание ER-диаграммы к приложению filmorate.
Структура базы данных к приложению filmorate.
База данных (далее БД) к приложению filmorate состоит из следующих таблиц:

films (таблица хранения фильмов);
users (таблица хранения пользователей);
films_like (таблица хранения лайков фильмов);
adding_friends (таблица хранения друзей);
mpa (таблица хранения рейтингов);
genre (таблица хранения жанров фильмов);
directors (таблица хранения режисеров);
users_events (таблица хранения истории);
reviews (таблица хранения отзывов);
review_user_likes (таблица хранения лайков отзывов).
Структура таблицы adding_friends.
Таблица состоит из 4 полей:

outgoing_request_user_id (id пользователя, который отправил заявку на добавления в друзья);
incoming_request_user_id (id пользователя, которому пришла заявка на добавления в друзья);
confimation (true или false - информация о том, была ли принята заявка или нет, по умолчанию false).
Логика работы таблицы adding_friends.
По умолчанию в поле confimation заполняется значение false. Если пользователь incoming_request_user_id принимает заяку, то в БД происходит попытка добавить новую запись, если находится запись с подходящей комбинацией (порядок неважен), то поле confimation меняется на true.

Структура таблицы films.
Таблица состоит из 7 полей:

id (id фильма);
name (название фильма);
description (описание фильма);
releaseDate (дата релиза фильма);
duration (продолжительность фильма в минутах);
genre (список id жанров, который хранится в виде varchar);
mpa_id (внешний ключ, который ссылается на таблицу mpa);
directors (список id режисеров, который хранится в виде varchar).

Функциональность «Лента событий».
Возможность просмотра последних событий на платформе — добавление в друзья, удаление из друзей, лайки и отзывы, которые оставили друзья пользователя. 

Функциональность «Поиск».
Поиск по названию фильмов и по режиссёру.
Алгоритм способен искать по подстроке. Например, вы вводите «крад», а в поиске возвращаются следующие фильмы: «Крадущийся тигр, затаившийся дракон», «Крадущийся в ночи» и другие.

Функциональность «Фильмы по режиссёрам». 
В информацию о фильмах добавлено имя режиссёра. 
Вывод всех фильмов режиссёра, отсортированных по количеству лайков.
Вывод всех фильмов режиссёра, отсортированных по годам.

Функциональность «Рекомендации». 
Реализована рекомендательная система для фильмов.
Функцонал:
Найти пользователей с максимальным количеством пересечения по лайкам.
Определить фильмы, которые один пролайкал, а другой нет.
Рекомендовать фильмы, которым поставил лайк пользователь с похожими вкусами, а тот, для кого составляется рекомендация, ещё не поставил.

Функциональность «Удаление фильмов и пользователей».
В приложению добавлена функциональность для удаления фильма и пользователя по идентификатору.

Функциональность «Общие фильмы».
Реализован вывод общих с другом фильмов с сортировкой по их популярности.

Функциональность «Популярные фильмы».
Добавлена возможность выводить топ-N фильмов по количеству лайков.
Фильтрация по двум параметрам:
1. По жанру.
2. За указанный год.

Функциональность «Отзывы». 
В приложении добавлены отзывы на фильмы. Добавленные отзывы имеют рейтинг и несколько дополнительных характеристик.
Характеристики отзыва:
Оценка — полезно/бесполезно.
Тип отзыва — негативный/положительный.
Рейтинг отзыва.
У отзыва имеется рейтинг. При создании отзыва рейтинг равен нулю. Если пользователь оценил отзыв как полезный, это увеличивает его рейтинг на 1. Если как бесполезный, то уменьшает на 1.
Отзывы сортируются по рейтингу полезности.

