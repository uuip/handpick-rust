## Short and handpick Rust crates list.

### Exceptions

* `cargo add eyre`
    - include error location: file name and line
* `cargo add anyhow`
    - without location
* `cargo add thiserror`

### Global Variable

| std                             |  crate                                   |
|---------------------------------|-------------------------------------|
| std::cell::{OnceCell, LazyCell} | once_cell::unsync::{OnceCell, Lazy} |
| std::sync::OnceLock             | once_cell::sync::OnceCell           |
| std::sync::LazyLock             | once_cell::sync::Lazy               |

### Rust patterns

* `cargo add regex`
* `cargo add dotenvy`
* `cargo add fastrand`
* `cargo add rand`
* `cargo add duplicate`
* `cargo add itertools`

### Data Type

* `cargo add uuid --features v4,fast-rng`
* `cargo add short-uuid`
* `cargo add byteorder bytes`
* `cargo add indexmap`
* `cargo add rust_decimal`
    - support Decimal::MAX 7.92e28
* `cargo add bigdecimal`
    - used when num > Decimal::MAX
* `cargo add num-bigint`
    - used when num > i128::MAX 1.7e38

### Date and Time

* `cargo add chrono --no-default-features --features clock,serde`
* `cargo add chrono-tz`
* `cargo add time --features formatting,macros`

### Enum

* `cargo add num_enum`
* `cargo add strum --features derive`
* `cargo add serde_with`
    - serde string enum
* `cargo add serde_repr`
    - serde num enum

### Logging

* `cargo add log --features release_max_level_info`
* `cargo add env_logger`
* `cargo add flexi_logger`

### File Access

* `cargo add glob`
* `cargo add home`
* `cargo add yaml-rust2`
* `cargo add toml`
* `cargo add roxmltree`

### Excel Processing

* `cargo add calamine`
* `cargo add rust_xlsxwriter --features zlib,ryu`

### Serialization

* `cargo add serde --features derive`
* `cargo add serde_json`
* `cargo add serde_json_path`

### Web Client

* `cargo add reqwest --features json,gzip,native-tls-alpn`
* `cargo add scraper`

### ORM & SQL Tools

* `cargo add tokio-postgres --features with-serde_json-1,with-chrono-0_4`
* `cargo add deadpool-postgres`
* `cargo add postgres-from-row`
* `cargo add postgres-types --features derive`
* `cargo add sqlx --features runtime-tokio,tls-native-tls,postgres,chrono`
* `cargo add sea-orm --features sqlx-postgres,runtime-tokio-native-tls,macros`

### Web Framework

* `cargo add axum`
* `cargo add axum-extra --features typed-header`
* `cargo add tower-http --features cors`
* `cargo add jsonwebtoken`
* `cargo add validator --features derive`
* `cargo add serde_urlencoded`

### Web3

* `cargo add alloy`
* ~~ethers = { version = "2.0.13", default-features = false,
  features = ["abigen", "legacy", "openssl"] }~~

### KV DataBase

* `cargo add rocksdb`

### Message Queue

* `cargo add pulsar --no-default-features --features tokio-runtime,compression`
* `cargo add schemars`
    - make pulsar json schema

### Data Analysis

* `cargo add polars --features parquet,lazy,is_in,rank,abs,streaming,cutqcut,propagate_nans`
* `cargo add ndarray --features rayon`

### Version Structure

* `cargo add semver`

### Async

* `cargo add futures-util`
* `cargo add tokio --features full`
* `cargo add async-channel`

### Concurrency

* `cargo add rayon`

### Shell

* `cargo add colored`
* `cargo add crossterm --no-default-features --features events`
* `cargo add pico-args`
* `cargo add clap --features derive`
* `cargo add enable-ansi-support`
    - for windows
* `cargo add indicatif`
* `cargo add ratatui`
* `cargo add comfy-table`

#### System Info

* `cargo add sysinfo`
* `cargo add num_cpus`

### Cryptography

* [hashes](https://github.com/RustCrypto/hashes)
* `cargo add base64`

### Algorithm

* `cargo add aho-corasick`
* `cargo add alphanumeric-sort`

### Language bindings

* [pyo3](https://github.com/PyO3/pyo3)

### Optimize Performance

* arc-swap
* phf
