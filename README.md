# Описание
Сайт представлят собой площадку, где люди(в основном конечно же соседи) могут найти способ связаться с человеком, адрес которого их известен

Есть возможность найти людей, которые проживают с тобой в одном доме, подъезде и даже квартире(с учётом заполненности информации об этих людях)

Использование:
1) регистрируетесь
2) ищете пользователей по адресам
3) отправляете запрос нужному
4) связываетесь с ним
5) ДОП - можно лайкнуть пользователя, если он тот, за кого себя выдаёт, или дизлайкнуть в противном случае (цель введения данной фичи именно такова)

# Наименование
Neighbour

# Предметная область
Аналог GetContact - только через Адрес. Цель - дать пользователю возможность связаться (по средствам сторонних сервисов) с нужным человеком.

# Данные
## Для каждого элемента данных - ограничения
### User
| name | type | constrains |
| ---- | ---- | ---------- |
| user_id   | Integer|  primary_key|
| email| Varchar(50)| unique, not null |
| password | Varchar(50) | not null |
| name | Varchar(50)| nullable |
| com_method | String(100) | nullable |
| count_likes | Integer | nullable |
| count_dislikes | Integer | nullable |

`com_method` - Ссылка на предпочитаемый способ связи (Телеграм, ВК и т.д.)
 
 Пользователь может зарегистрироваться без адреса, но для использования основного функционала приложения, он должен указать адрес.
 
### Neighbour
| name | type | constrains |
| ---- | ---- | ---------- |
| user_id | Integer | not null |
| adress_id | Integer | not null |

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
| county_id   | Integer |  primary_key|
| name_country | Varchar(40) | uniqie, not null |

### City
| name | type | constrains |
| ---- | ---- | ---------- |
| city_id   | Integer|  primary_key|
| name_city | Varchar(40) | uniqie, not null |

### Street
| name | type | constrains |
| ---- | ---- | ---------- |
| street_id   | Integer | primary_key|
| name_street | Varchar(40) | uniqie, not null |

### Request_info
| name | type | constrains |
| ---- | ---- | ---------- |
| request_info_id | Integer | primary_key |
| text | Text | nullable |
| from_user_id | Integer | ForeignKey(User) ON DELETE CASCADE |
| to_user_id | Integer | ForeignKey(User) ON DELETE CASCADE |
| is_approved | Boolean | default = false |

Запрос на получение информации о способе связи

## Общие ограничения целостности
* Между таблицами `User` и `Request_info`, `Adress` и `Country`, `Adress` и `City`, `Adress` и `Street` отношение `One to many`.
* Между таблицами `User` `Adress` отношение `Many to many` - `neighbour`
# Пользовательские роли
## Для каждой роли - наименование, ответственность, количество пользователей в этой роли?

User (Кол-во: неограничено)
* Создавать/редактировать/удалять свои адресса
* Находить людей по определённому адресу
* Отправлять/подтверждать запросы на получение информации о методе общения
* Оценивать информацию о других пользователях

# UI / API 
* UI -  React
* API -  Java Spring
# Технологии разработки
## Язык программирования

* Backend - Java, sql, xml
* Frontend - js, css, html

## СУБД
PostgreSQL
