



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












