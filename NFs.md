# Тестовая талица
| Сотрудник | Контакт |
| --- | ----------- |
| Иванов И.И | 123-456-789, 987-654-321 |
| Сергеев С.С. | Рабочий телефон 555-666-777, Домашний телефон 777-888-999 |
| John Smith | 123-456-789 |
	

# 1. Первая нормальная форма
Таблица сотрудников в первой нормальной форме.

| Сотрудник | Телефон | Тип телефона |
| --- | ----------- | --------|
| Иванов И.И. | 123-456-789 |
| Иванов И.И. | 987-654-321 |
| Сергеев С.С. | 555-666-777 | Рабочий телефон|
| Сергеев С.С. | 777-888-999 | Домашний телефон|
| John Smith | 123-456-789 | |


Таким образом, главное правило первой нормальной формы звучит следующим образом
Строки, столбцы и ячейки в таблицах необходимо использовать строго по назначению.


# 2. Вторая нормальная форма
- Таблица должна находиться в первой нормальной форме
- Таблица должна иметь ключ
- Все неключевые столбцы таблицы должны зависеть от полного ключа (в случае если он составной)

|Табельный номер |	ФИО	Должность	|Подразделение|	Описание подразделения|
|-------|-----| -------- |  -------|
|1	Иванов И.И.|	Программист	|Отдел разработки	|Разработка и сопровождение приложений и сайтов|
|2	Сергеев С.С.|	Бухгалтер	|Бухгалтерия	|Ведение бухгалтерского и налогового учета финансово-хозяйственной деятельности|
|3	John Smith |	Продавец	|Отдел реализации	| Организация сбыта продукции |

https://info-comp.ru/second-normal-form

# 3. Третья нормальная форма

- Требование третьей нормальной формы (3NF) заключается в том, чтобы в таблицах отсутствовала транзитивная зависимость.
- Транзитивная зависимость – это когда неключевые столбцы зависят от значений других неключевых столбцов.

Таблица сотрудников в третьей нормальной форме.

|Табельный номер	|ФИО	|Должность	|Подразделение|
|---- | ---- | --- | --- |
|1|	Иванов И.И.	|Программист	|1|
|2	|Сергеев С.С.|	Бухгалтер	|2 |
|3	|John Smith	Продавец	|3|

Таблица подразделений в третьей нормальной форме.

|Идентификатор подразделения	|Подразделение|	Описание подразделения| 
|-----|----|----|
|1	|Отдел разработки	|Разработка и сопровождение приложений и сайтов|
|2	|Бухгалтерия	|Ведение бухгалтерского и налогового учета финансово-хозяйственной деятельности|
|3	| Отдел реализации|Организация сбыта продукции|
https://info-comp.ru/third-normal-form



#4. Нормальная форма Бойса-Кодда (BCNF)
- Таблица должна находиться в третьей нормальной форме. Здесь все как обычно, т.е. как и у всех остальных нормальных форм, первое требование заключается в том, чтобы таблица находилась в предыдущей нормальной форме, в данном случае в третьей нормальной форме;
- Ключевые атрибуты составного ключа не должны зависеть от неключевых атрибутов. Часть составного первичного ключа не должна зависеть от неключевого столбца.

Таблица проектов и кураторов.

|Проект	|Направление	|Куратор|
|---|----|---|
|1	|Разработка|	Иванов И.И.|
|1	|Бухгалтерия	|Сергеев С.С.|
|2	|Разработка	|Иванов И.И.|
|2	|Бухгалтерия|	Петров П.П.|
|2	|Реализация	|John Smith|
|3	|Разработка|	Андреев А.А.|


Таблица кураторов в BCNF.

|Идентификатор куратора	|ФИО|	Направление|
|---|---|---|
|1	|Иванов И.И.	|Разработка|
|2	|Сергеев С.С.	|Бухгалтерия|
|3	|Петров П.П.	|Бухгалтерия
|4	|John Smith	|Реализация|
|5	|Андреев А.А.|Разработка|
Таблица связи кураторов и проектов.

|Проект	|Идентификатор куратора|
|---|---|
|1 |1|
|1|	2|
|2|	1|
|2|	3|
|2|	4|
|3|	5|


#5. Четвертая нормальная форма 
- Требование четвертой нормальной формы (4NF) заключается в том, чтобы в таблицах отсутствовали нетривиальные многозначные зависимости.
- Начнем с того, что таблица должна иметь как минимум три столбца, допустим A, B и C, при этом B и C между собой никак не связаны и не зависят друг от друга, но по отдельности зависят от A, и для каждого значения A есть множество значений B, а также множество значений C.

Курсы.

|Идентификатор курса	|Название курса|
| --- | --- |
|1|	SQL|
|2	|Python|
|3	|JavaScript|

Преподаватели.

|Идентификатор преподавателя|	ФИО|
| --- | ---|
|1	|Иванов И.И.|
|2	|Сергеев С.С.|
|3	|John Smith|

Аудитории.

|Идентификатор аудитории	|Название аудитории|
| --- | ---|
|1| 101|
|2|	203|
|3|	305|
|4|	407|
|5|	502|

Таблица связей курсов, преподавателей и аудиторий. после преобразования

|Курс|Преподаватель|	Аудитория|
| --- | --- | --- |
|SQL|	Иванов И.И.	|101|
|SQL	|Иванов И.И.	|203|
|SQL|	Сергеев С.С.|	305|
|SQL|	Сергеев С.С.|	407|
|Python|	John Smith|	502|
|Python	|John Smith	|305|

В данном случае первичный ключ здесь состоит из всех трех столбцов, поэтому эта таблица автоматически находится в третьей нормальной форме и нормальной форме Бойса-Кодда. Однако она не находится в четвертой нормальной форме, так как здесь есть многозначная зависимость

_Для соответствия четвертой форме:_

Связь курсов и преподавателей.

|Курс	|Преподаватель
| --- | --- |
|SQL	|Иванов И.И.|
|SQL	|Сергеев С.С.|
|Python	|John Smith|


Связь курсов и аудиторий.

|Курс	|Аудитори|
| --- | --- |
|SQL	|101|
|SQL	|203|
|SQL	|305|
|SQL	|407|
|Python	|502|
|Python	|305|

#6. Пятая нормальная форма
- Переменная отношения находится в пятой нормальной форме (иначе – в проекционно-соединительной нормальной форме) тогда и только тогда, когда каждая нетривиальная зависимость соединения в ней определяется потенциальным ключом (ключами) этого отношения.
- Требование пятой нормальной формы (5NF) заключается в том, чтобы в таблице каждая нетривиальная зависимость соединения определялась потенциальным ключом этой таблицы.
https://info-comp.ru/fifth-normal-form
  
#7. Доменно ключевая норальная форма
Требования доменно-ключевой нормальной формы (DKNF)
- Ограничение домена – это ограничение, предписывающее использование для определенного атрибута значений только из некоторого заданного домена (набора значений).
- Ограничение ключа – это ограничение, утверждающее, что некоторый атрибут или комбинация атрибутов представляет собой потенциальный ключ.
  
https://info-comp.ru/domain-key-normal-form

#8. Шестая нормальная форма (6NF) базы данных
- Требование шестой нормальной формы заключается в том, что таблица должна удовлетворять всем нетривиальным зависимостям соединения.

  