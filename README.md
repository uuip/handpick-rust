
## Short and handpick Rust crates list.

### Rust patterns

* anyhow
* once_cell
* rand
* regex
* sysinfo

### Date and Time

* chrono
* chrono-tz

### Logging

* tracing-appender = { package = "clia-tracing-appender", version = "0.2" }
* tracing-subscriber = { version = "0.3", features = ["local-time","time"] }
* tracing =  "0.1"
* time = { version = "0.3.21", features = ["formatting","macros"] }

### Serialization

* serde = { version = "1", features = ["derive"] }
* serde_json
* serde_yaml
* display_json

### File System

* glob

### File Processing

* calamine - read xlsx
* rust_xlsxwriter - write xlsx

### Web

* reqwest = { version = "0", features = ["blocking", "json"] }
* scraper - web content extracting

### ORM

* sea-orm = { version = "0", features = ["sqlx-postgres", "runtime-tokio-native-tls", "macros"] }

### Async

* tokio = { version = "1", features = ["full"] }
* futures

### Concurrency

* rayon

### Shell

* clap = { version = "4", features = ["derive"] }
* enable-ansi-support - for windows
* mincolor

### Version Structure

* semver

### Data Analysis

* polars = { git = "https://github.com/pola-rs/polars", branch = "master", features = [
  "parquet", "lazy", "is_in", "rank", "abs", "streaming", "algo", "propagate_nans", "dtype-full", "random"] }
