
## Short and handpick Rust crates list.
just `cargo add ...` or edit Cargo.toml.
### Rust patterns

* anyhow
* thiserror
* once_cell
* dotenvy
* duplicate
* rand
* regex
* itertools
* generator
* sysinfo
* num_cpus
* pin-project-lite

### Data Type

* indexmap
* enum-iterator
* uuid = { version = "1.5.0", features = ["v4", "fast-rng"]}
* rust_decimal  
Decimal::MAX = 79228162514264337593543950335 7.92e28
* bigdecimal  
when num > Decimal::MAX
* num-bigint  
when num > i128::MAX (170141183460469231731687303715884105727) 1.7e38

### Date and Time

* chrono = { version = "0.4.31", features = ["serde"] }
* chrono-tz
* time = { version = "0.3.21", features = ["formatting","macros"] }

### Logging
* log = "0.4.20"
* env_logger = "0.10.0"
* tracing-appender = { package = "clia-tracing-appender", version = "0.2" }
* tracing-subscriber = { version = "0.3", features = ["local-time","time"] }
* tracing =  "0.1"

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

* reqwest = { version = "0.11.22", features = ["json", "cookies", "native-tls-alpn"] }
* ureq
* scraper - web content extracting
* url

### ORM & SQL Tools

* tokio-postgres = { version = "0.7.10", features=["with-serde_json-1","with-chrono-0_4"]}
* deadpool-postgres = "0.11.0"
* postgres-from-row = "0.5.2"
* postgres-types = { version = "0.2.6", features = ["derive"]}
* sea-orm = { version = "0.12.4", features = ["sqlx-postgres", "runtime-tokio-native-tls", "macros"] }
* sqlx = { version = "0.7.2", features = ["runtime-tokio-native-tls", "postgres", "chrono"] }

### Web Framework

* axum = { version = "0.6.20", features = ["headers"] }<br>
[axum](https://github.com/uuip/axum-demo/blob/main/Cargo.toml)
* tower-http = { version = "0.4.4", features = ["cors"] }
* serde_urlencoded
* jsonwebtoken
* validator = { version = "0.16.1", features = ["derive"] }

### Async

* tokio = { version = "1", features = ["full"] }
* futures, futures-util
* async-channel, deadqueue

### Concurrency

* rayon

### Shell

* pico-args
* clap = { version = "4", features = ["derive"] }
* enable-ansi-support&#160;&#160;&#160;&#160;-- *for windows*
* colored, mincolor
* indicatif
* ratatui

### Version Structure

* semver

### Optimize Performance

* arc-swap
* phf
* ahash
* slab
  
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

### Web3

* ethers = { version = "2.0.10", features = ["legacy"] }

### Data Analysis

* polars = { git = "https://github.com/pola-rs/polars", branch = "master", features = [
  "parquet", "lazy", "is_in", "rank", "abs", "streaming", "algo", "propagate_nans", "dtype-full", "random"] }
