# Get started

- Make `.env`

```
POSTGRES_PASSWORD=1234
POSTGRES_USER=postgres
POSTGRES_DB=mydb
POSTGRES_PORT=5432
POSTGRES_HOST=localhost

POSTGRES_APP_USER=appuser
POSTGRES_APP_PASSWORD=1234
```

- `docker compose up -d`

# User management

- `docker exec -it pf-db bash`
- `psql -U postgres -d mydb`
- Don't forget to change the password.

```
REVOKE CONNECT ON DATABASE mydb FROM public;
REVOKE ALL ON SCHEMA public FROM PUBLIC;
CREATE USER appuser WITH PASSWORD '1234';
CREATE SCHEMA drizzle;
GRANT ALL ON DATABASE mydb TO appuser;
GRANT ALL ON SCHEMA public TO appuser;
GRANT ALL ON SCHEMA drizzle TO appuser;
```
