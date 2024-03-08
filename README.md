# Домашнее задание к занятию "`Резервное копирование баз данных`" - `Воронин Алексей`


---

### Задание 1. Резервное копирование

### Кейс
Финансовая компания решила увеличить надёжность работы баз данных и их резервного копирования. 

Необходимо описать, какие варианты резервного копирования подходят в случаях: 

1.1. Необходимо восстанавливать данные в полном объёме за предыдущий день.

### Ответ
- Раз в неделю делать полный бэкап + каждый день делать дифференциальное.


1.2. Необходимо восстанавливать данные за час до предполагаемой поломки.

### Ответ
- Раз в неделю делать полный бэкап + каждый день делать дифференциальное + каждый час инкрементальное.

1.3.* Возможен ли кейс, когда при поломке базы происходило моментальное переключение на работающую или починенную базу данных.

*Приведите ответ в свободной форме.*

---

### Задание 2. PostgreSQL

2.1. С помощью официальной документации приведите пример команды резервирования данных и восстановления БД (pgdump/pgrestore).

### Ответ

```
pg_dump [параметр-подключения...] [параметр...] [имя_бд]
pg_dump -Fc mydb > db.sql

pg_restore [параметр-подключения...] [параметр...] [имя_файла]
pg_restore -C -d postgres db.dump
```

2.1.* Возможно ли автоматизировать этот процесс? Если да, то как?

*Приведите ответ в свободной форме.*

---

### Задание 3. MySQL

3.1. С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySQL. 

### Ответ
```
mysqlbackup --defaults-file=/home/dbadmin/my.cnf \
  --incremental --incremental-base=history:last_backup \
  --backup-dir=/home/dbadmin/temp_dir \
  --backup-image=incremental_image1.bi \
   backup-to-image
```


3.1.* В каких случаях использование реплики будет давать преимущество по сравнению с обычным резервным копированием?

*Приведите ответ в свободной форме.*

---

Задания, помеченные звёздочкой, — дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.
