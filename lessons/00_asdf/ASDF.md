# Setup

```bash
docker compose exec postgres psql -U postgres -d postgres -c "CREATE DATABASE asdf;"
```

# Cleanup

```bash
docker compose exec postgres psql -U postgres -d postgres -c "DROP DATABASE asdf;"
```

# ASDF

```bash
docker compose exec postgres pgbench -U postgres -d asdf -i -s 10
```

Connect with `psql` to the database.
```bash
docker compose exec postgres psql -U postgres -d asdf
```