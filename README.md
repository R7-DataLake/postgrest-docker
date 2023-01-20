
# Create configure
```
postgrest -e > postgrest.conf
```

Edit `postgrest.conf`

# Run
```
postgrest postgrest.conf 
```

# Create user

```sql
create role authenticator noinherit login password 'xxxxxx';

create role admin nologin;
grant admin to authenticator;
grant usage on schema public to admin;
grant all on public.users to admin;
```

# Create jwt with payload

```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "iat": 1516239022,
  "exp": 1674217011,
  "role": "admin"
}
```