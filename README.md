# Short and handpick Rust crates list.

## Exceptions

* `cargo add anyhow`
* `cargo add thiserror`

## Macros

* `cargo add duplicate`

## Data structures

* `cargo add dashmap`
* `cargo add indexmap`
* `cargo add itertools`

## Global Variable

| std                             | crate                               |
|---------------------------------|-------------------------------------|
| std::cell::{OnceCell, LazyCell} | once_cell::unsync::{OnceCell, Lazy} |
| std::sync::OnceLock             | once_cell::sync::OnceCell           |
| std::sync::LazyLock             | once_cell::sync::Lazy               |

## Data Types

### uuid

* `cargo add uuid --features v4,fast-rng`
* `cargo add short-uuid`

### bytes

* `cargo add byteorder bytes`

### datetime

* `cargo add chrono --no-default-features --features clock,serde`
* `cargo add chrono-tz`
* `cargo add time --features formatting,macros`

### enum

* `cargo add num_enum`
* `cargo add strum --features derive`
* `cargo add serde_with` - serializing string enum
* `cargo add serde_repr` - serializing num enum

## Numeric and Mathematical

* `cargo add rand`
* `cargo add fastrand`
* `cargo add rust_decimal` - support Decimal::MAX 7.92e28
* `cargo add bigdecimal` - used when num > Decimal::MAX
* `cargo add num-bigint` - used when num > i128::MAX 1.7e38

## Logging

* `cargo add log --features release_max_level_info`
* `cargo add env_logger`
* `cargo add flexi_logger`

## Text Processing

* `cargo add regex`

## File Processing

* `std::env::home_dir()`
* `cargo add camino`
* `cargo add glob`
* `cargo add toml`
* `cargo add yaml-rust2`
* `cargo add roxmltree`

## Excel Processing

* `cargo add calamine`
* `cargo add rust_xlsxwriter --features zlib,ryu`

## Serialization

* `cargo add serde --features derive`
* `cargo add serde_json`
* `cargo add serde_json_path`

## Configuration

* `cargo add envy dotenvy`

## Caching

* `cargo add http-cache-reqwest`
* `cargo add cached` - python lru_cache
* `cargo add moka` - common cache

## KV DataBase

* `cargo add rocksdb`

## Async

* `cargo add futures`
* `cargo add tokio --features full`
* `cargo add async-channel`

## Web Client

* `cargo add reqwest --features json,gzip`
* `cargo add scraper`

## ORM & SQL Tools

* `cargo add tokio-postgres --features with-serde_json-1,with-chrono-0_4`
* `cargo add deadpool-postgres`
* `cargo add postgres-from-row`
* `cargo add postgres-types --features derive`
* `cargo add sqlx --features runtime-tokio,postgres,chrono`
* `cargo add sea-orm --features sqlx-postgres,runtime-tokio,macros`

## Web Framework

* `cargo add axum`
* `cargo add axum-extra --features typed-header`
* `cargo add tower-http --features cors`
* `cargo add jsonwebtoken`
* `cargo add validator --features derive`
* `cargo add serde_urlencoded`

## Web3

* `cargo add alloy`
* ~~ethers = { version = "2.0.13", default-features = false,
  features = ["abigen", "legacy", "openssl"] }~~

## Concurrency

* `cargo add rayon`

## Shell

* `cargo add colored`
* `cargo add crossterm --no-default-features --features events`
* `cargo add clap --features derive`
* `cargo add enable-ansi-support`     - for windows
* `cargo add indicatif`
* `cargo add ratatui`
* `cargo add comfy-table`

## System Info

* `cargo add sysinfo`
* `cargo add num_cpus`

## Cryptography

* [hashes](https://github.com/RustCrypto/hashes)
* `cargo add base64`

## Message Queue

* `cargo add pulsar --no-default-features --features tokio-runtime,compression`
* `cargo add schemars` - make pulsar json schema

## Data Analysis

* `cargo add polars --features parquet,lazy,is_in,rank,abs,streaming,cutqcut,propagate_nans`
* `cargo add ndarray --features rayon`

## Version Structure

* `cargo add semver`

## Algorithm

* `cargo add aho-corasick`
* `cargo add alphanumeric-sort`

## Language bindings

* [pyo3](https://github.com/PyO3/pyo3)

## Alternative

* `cargo add serde_yaml_ng`
* `cargo add quick_xml`
* `cargo add simple_excel_writer`
* `cargo add phf`
* `cargo add arc-swap`
* `cargo add papaya`
* `cargo add eyre` - include exc file name and line
* `cargo add home`
* `cargo add directories`
* `cargo add config --no-default-features --features convert-case,yaml`
