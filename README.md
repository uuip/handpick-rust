## Short and handpick Rust crates list.

### Rust patterns

* `cargo add eyre`
* `cargo add anyhow`
* `cargo add thiserror`
* `cargo add once_cell`
* `cargo add dotenvy`
* `cargo add fastrand`
* `cargo add rand`
* `cargo add regex`
* `cargo add itertools`
* `cargo add duplicate`
* `cargo add generator`
* `cargo add sysinfo`
* `cargo add num_cpus`
* `cargo add display_json`

### Data Type

* `cargo add uuid --features v4,fast-rng`
* `cargo add byteorder`
* `cargo add bytes`
* `cargo add indexmap`
* `cargo add rust_decimal`
    - support Decimal::MAX 7.92e28
* `cargo add bigdecimal`
    - used when num > Decimal::MAX
* `cargo add num-bigint`
    - when num > i128::MAX 1.7e38

#### Enum

* `cargo add num_enum`
* `cargo add strum --features derive`
* `cargo add enum-iterator`
* `cargo add serde_with`
    - **[ has extra features ]**
    - serde string enum
* `cargo add serde_repr`
    - serde num enum

### Date and Time

* `cargo add chrono --no-default-features --features clock,serde`
* `cargo add chrono-tz`
* `cargo add time --features formatting,macros`

### Logging

* `cargo add log --features release_max_level_info`
* `cargo add env_logger`
* `cargo add flexi_logger`
    - **[ has extra features ]**

### File System

* `cargo add glob`

### Excel Processing

* `cargo add calamine`
    - **[ has extra features ]**
* `cargo add rust_xlsxwriter --features zlib,ryu`

### Xml Processing

* `cargo add roxmltree`
* `cargo add quick-xml`
    - **[ has extra features ]**

### Serialization

* `cargo add serde --features derive`
* `cargo add serde_json`
    - **[ has extra features ]**
* `cargo add yaml-rust2`

### Web Client

* `cargo add reqwest --features json,gzip,native-tls-alpn`
* `cargo add scraper`
    - web content extracting

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
* ~~ethers = { version = "2.0.13", default-features = false, features = ["abigen", "legacy", "openssl"] }~~

### KV DataBase

* `cargo add rocksdb`

### Message Queue

* `cargo add pulsar --no-default-features --features tokio-runtime,compression`
* `cargo add schemars`
    - **[ has extra features ]**
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
* `cargo add mincolor`
* `cargo add crossterm --no-default-features --features events`
* `cargo add enable-ansi-support`
    - for windows
* `cargo add clap --features derive`
* `cargo add pico-args`
* `cargo add indicatif`
* `cargo add ratatui`

### Cryptography

* [hashes](https://github.com/RustCrypto/hashes)

### Algorithm

* `cargo add aho-corasick`
* `cargo add alphanumeric-sort`
* `cargo add float-ord`

### Language bindings

* [pyo3](https://github.com/PyO3/pyo3)

### Optimize Performance

* arc-swap
* phf
