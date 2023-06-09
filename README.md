
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

* rust_decimal  
Decimal::MAX = 79228162514264337593543950335 7.92e28
* bigdecimal  
when num > Decimal::MAX
* num-bigint  
when num > i128::MAX (170141183460469231731687303715884105727) 1.7e38
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

### Web Client 

* reqwest = { version = "0", features = ["blocking", "json"] }
* ureq
* scraper - web content extracting
* url

### Web Framework

* [axum](https://github.com/uuip/axum-demo/blob/main/Cargo.toml)

### ORM & SQL Tools

* sea-orm = { version = "0", features = ["sqlx-postgres", "runtime-tokio-native-tls", "macros"] }
* sqlx = { version = "0.6", features = ["runtime-tokio-native-tls", "postgres", "all-types"] }

### Async

* tokio = { version = "1", features = ["full"] }
* futures
* async-trait

### Concurrency

* rayon

### Shell

* clap = { version = "4", features = ["derive"] }
* enable-ansi-support&#160;&#160;&#160;&#160;-- *for windows*
* mincolor
* indicatif

### Version Structure

* semver

### Algorithm

* aho-corasick
* alphanumeric-sort
* float-ord

### Language bindings

* [pyo3](https://github.com/PyO3/pyo3)
* libloading
* rustix

### Cryptography

* [hashes](https://github.com/RustCrypto/hashes)

### Data Analysis

* polars = { git = "https://github.com/pola-rs/polars", branch = "master", features = [
  "parquet", "lazy", "is_in", "rank", "abs", "streaming", "algo", "propagate_nans", "dtype-full", "random"] }
