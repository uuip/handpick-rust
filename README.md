## Short and handpick Rust crates list.

just `cargo add ...` or edit Cargo.toml.

### Rust patterns

* anyhow = "1.0.80"
* thiserror = "1.0.57"
* once_cell = "1.19.0"
* dotenvy = "0.15.7"
* rand = "0.8.5"
* regex = "1.10.3"
* duplicate = "1.0.0"
* itertools
* generator
* sysinfo
* num_cpus

### Data Type

* uuid = { version = "1.7.0", features = ["v4", "fast-rng"] }
* byteorder = "1.5.0"
* bytes = "1.5.0"
* indexmap
* rust_decimal  
  Decimal::MAX = 79228162514264337593543950335 7.92e28
* bigdecimal  
  when num > Decimal::MAX
* num-bigint  
  when num > i128::MAX (170141183460469231731687303715884105727) 1.7e38

#### Enum

* num_enum = "0.7.2"
* strum = { version = "0.26.1", features = ["derive"] }
* enum-iterator
* serde_with = "3.6.1" # serde string enum
* serde_repr = "0.1.18" # serde num enum

### Date and Time

* chrono = { version = "0.4.34", default-features = false, features = ["clock", "serde",] }
* chrono-tz = "0.8.6"
* time = { version = "0.3.31", features = ["formatting","macros"] }

### Logging

* log = { version = "0.4.20", features = ["release_max_level_info"] }
* env_logger = "0.11.2"
* flexi_logger = "0.27.4"

* tracing = "0.1.40"
* tracing-rolling-file = "0.1.2" # support rolling by log file size
* tracing-subscriber = { version = "0.3.18", features = ["local-time"]} # use time crate and local time zone
* tracing-subscriber = { version = "0.3.18", features = ["chrono"]} # use chromo crate, can choose Local when defining
* tracing-appender = "0.2.3" # time in log's file name is UTC
* tracing-appender = { package = "clia-tracing-appender", version = "0.2.5", optional = true } # time in log's file name
  is Local

### Serialization

* serde = { version = "1.0.196", features = ["derive"] }
* serde_json = "1.0.113"
* serde_yaml = "0.9.32"
* display_json = "0.2.1"

### File System

* glob = "0.3.1"

### File Processing

* calamine = "0.24.0" # read xlsx
* rust_xlsxwriter = "0.62.0" # write xlsx

### Web Client

* reqwest = { version = "0.11.24", features = ["json", "gzip"] }
* scraper = "0.18.1" # web content extracting
* ureq

### ORM & SQL Tools

* tokio-postgres = { version = "0.7.10", features=["with-serde_json-1","with-chrono-0_4"]}
* deadpool-postgres = "0.12.1"
* postgres-from-row = "0.5.2"
* postgres-types = { version = "0.2.6", features = ["derive"]}
* sqlx = { version = "0.7.3", features = ["runtime-tokio", "sqlite", "chrono"] }
* sea-orm = { version = "0.12.14", features = ["sqlx-sqlite", "runtime-tokio-native-tls", "macros"] }

### KV DataBase

* rocksdb = "0.22.0"

### Web Framework

* axum = { version = "0.7.4"}
* axum-extra = { version = "0.9.2", features = ["typed-header"] }<br>
  [axum](https://github.com/uuip/axum-demo/blob/main/Cargo.toml)
* tower-http = { version = "0.5.1", features = ["cors"] }
* jsonwebtoken = "9.2.0"
* validator = { version = "0.16.1", features = ["derive"] }
* serde_urlencoded = "0.7.1"

### Async

* futures-util = "0.3.30"
* tokio = { version = "1.36.0", features = ["full"] }
* async-channel = "2.2.0" # deadqueue

### Concurrency

* rayon

### Shell

* colored = "2.1.0" # mincolor = "2"
* enable-ansi-support = "0.2.1" # for windows
* clap = { version = "4", features = ["derive"] }
* pico-args
* indicatif
* ratatui

### Version Structure

* semver = "1.0.21"

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

* ethers = { version = "2.0.13", default-features = false, features = ["abigen", "legacy", "openssl"] }
* rustc-hex = "2.1.0" # only use uint::FromHexError with thiserror
* uint = "0.9.5" # only use rustc_hex::FromHexError with thiserror

### Message Queue

* pulsar = { version = "6.1.0", default-features = false, features = ["tokio-runtime", "compression"]}
* schemars = "0.8.16" # make pulsar json schema

### Data Analysis

* polars = { git = "https://github.com/pola-rs/polars", branch = "main", features = [
  "parquet", "lazy", "is_in", "rank", "abs", "streaming", "cutqcut", "propagate_nans", "dtype-full", "random"] }
