# Описание
Сайт представлят собой плоадку, где люди(в основном конечно же соседи) могут знакомиться, обмениваться какой-то информацией и находить людей, которые близки тебе не только по интересам, но и по местоположению.

Есть возможность найти людей, которые проживают с тобой в одном доме, подъезде и даже квартире(с учётом заполненности информации об этих людях)

# Наименование
Neighbour

# Предметная область
Сайт знакомств

# Данные
## Для каждого элемента данных - ограничения
### User
| name | type | constrains |
| ---- | ---- | ---------- |
| user_id   | Integer|  primary_key|
| email| Varchar(50)| unique, not null |
| password | Varchar(
| name | Varchar(50)| nullable |
| com_method | String(100) | nullable |

`com_method` - Ссылка на предпочитаемый способ связи (Телеграм, ВК и т.д.)

### Neighbour
| name | type | constrains |
| ---- | ---- | ---------- |
| neighbour_id | Integer | primary_key |
| user_id | Integer | unique |
| adress_id | Integer | unique |

### Adress
| name | type | constrains |
| ---- | ---- | ---------- |
| adress_id   | Integer|  primary_key|
| country_id | Integer | ForeignKey(Country), ON DELETE CASCADE |
| city_id | Integer | ForeignKey(Country), ON DELETE CASCADE |
| street_id | Integer | ForeignKey(Country), ON DELETE CASCADE |
| house_number | Varchar(10) | not null |
| entrance_nubmer | Integer | nullable |
| flat_number | Integer | nullable |

### Country
| name | type | constrains |
| ---- | ---- | ---------- |
| county_id   | Integer|  primary_key|
| name_country | Varchar(40) | uniqie, not null |


### City
| name | type | constrains |
| ---- | ---- | ---------- |
| city_id   | Integer|  primary_key|
| name_country | Varchar(40) | uniqie, not null |

### Street
| name | type | constrains |
| ---- | ---- | ---------- |
| street_id   | Integer|  primary_key|
| name_country | Varchar(40) | uniqie, not null |

### Message
| name | type | constrains |
| ---- | ---- | ---------- |
| message_id | Integer | primary_key |
| text | Text | not null |
| user_id | Integer | ForeignKey(User) ON DELETE CASCADE |

## Общие ограничения целостности
* Между таблицами `User` и `Message`, `Adress` и `Country`, `Adress` и `City`, `Adress` и `Street` отношение `One to many`.
* Между таблицами `User` `Adress` отношение `Many to many` - `neighbour`
# Пользовательские роли
## Для каждой роли - наименование, ответственность, количество пользователей в этой роли?

User (Кол-во: неограничено)
* Создавать/редактировать/удалять свои адресса
* Находить людей, живущих рядом с ним
* Связывать с помощью сообщений с соседями

# UI / API 
* UI -  React
* API -  Java Spring
# Технологии разработки
## Язык программирования

* Backend - Java, sql, xml
* Frontend - js, css, html

## СУБД
PostgreSQL
