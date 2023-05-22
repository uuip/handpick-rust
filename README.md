
## Short and handpick Rust crates list.
just `cargo add ...` or edit Cargo.toml.
### Rust patterns

* anyhow
* once_cell
* rand
* regex
* sysinfo
* num_cpus

### Data Type

* bigdecimal
* rust_decimal
* num-bigint
* uuid = { version = "1", features = ["v4"] }

### Date and Time

* chrono
* chrono-tz

### Logging
[How to use tracing](https://github.com/uuip/rust_study/commit/fa658a3bfa1f82e0271b8499af7fcfc9c0bb41df)
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
* url

### ORM

* sea-orm = { version = "0", features = ["sqlx-postgres", "runtime-tokio-native-tls", "macros"] }

### Async

* tokio = { version = "1", features = ["full"] }
* futures
* async-trait

### Concurrency

* rayon

### Shell

* clap = { version = "4", features = ["derive"] }
* enable-ansi-support - for windows
* mincolor
* indicatif

### Version Structure

* semver

### Algorithm

* aho-corasick

### Cryptography

* [hashes](https://github.com/RustCrypto/hashes)

### Data Analysis

* polars = { git = "https://github.com/pola-rs/polars", branch = "master", features = [
  "parquet", "lazy", "is_in", "rank", "abs", "streaming", "algo", "propagate_nans", "dtype-full", "random"] }
