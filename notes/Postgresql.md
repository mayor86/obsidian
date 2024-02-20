## Архитектура
![[postgresqldba1_02_architecture.pdf]]

### Создание пользователя
```sql
CREATE ROLE dblink_user WITH
NOSUPERUSER
NOCREATEDB
NOCREATEROLE
NOINHERIT
LOGIN
NOREPLICATION
NOBYPASSRLS
ENCRYPTED PASSWORD 'Cnhjqrf2023'
CONNECTION LIMIT 3; -- Максимальное количество коннектов для пользователя
```
### Permissions
```sql
GRANT SELECT ON TABLE public.auth_group TO analytics;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO mirzoev;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO mirzoev;
```
### Изменение CONNECTION LIMIT для пользователя
```sql
ALTER USER johndoe WITH CONNECTION LIMIT 2;
```

### Изменение времени жизни IDLE транзакции для пользователя
```sql
ALTER ROLE mayorov SET idle_in_transaction_session_timeout = '10min';
```
### Проверка прав пользователя
```sql
SELECT * FROM pg_roles;