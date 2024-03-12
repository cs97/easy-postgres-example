



### connect to pool
```rust
use std::error::Error;

#[tokio::main]
async fn main() -> Result<(), Box<dyn Error>> {
  let url = "postgres://postgres:password@127.0.0.1:5432";
	let conn = sqlx::postgres::PgPool::connect(url).await?;
	Ok(())
}
```


### migrate
```rust

async fn migrate(pool: &sqlx::PgPool) -> Result<(), Box<dyn Error>> {
	let query = "create table table_name (var1 varchar not null, var2 varchar not null, var3 varchar not null);";
	sqlx::query(query)
		.execute(pool)
		.await?;
	Ok(())
}
```


### INSERT
```rust
async fn create(kunde: &Kunde, pool: &sqlx::PgPool) -> Result<(), Box<dyn Error>> {
	let query = "INSERT INTO table_name (var1, var2, var3) VALUES ($1, $2, $3)";

	sqlx::query(query)
		.bind(&data.var1)
		.bind(&data.var2)
		.bind(&data.var3)
		.execute(pool)
		.await?;
	
	Ok(())
}
```




