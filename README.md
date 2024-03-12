



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

