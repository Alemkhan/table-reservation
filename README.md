#Table reservation app

##Prerequisites

Create .env file in both directories and add following values:
```dotenv
POSTGRES_URI=postgres://<username>:<password>@127.0.0.1:5432/<db_name>
SESSION_SECRET=<any secret>
```
(databases should be different)

Manually give admin role to certain user that is admin
```postgresql
    update users set role_id = 1 where id = ?
```

## Use Cases

Use `go run ./cmd/app` to run project (make sure you are in the right directory first)

-- Example of getting tables that haven't been reserved yet in cafe
```postgresql
select *
from tables t
where not exists(
        select from reservations where table_id = t.id
    );
```
