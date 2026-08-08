# A Short, Handpicked List of Rust Crates

## Error Handling

* `cargo add anyhow` - Keeps application error handling concise while preserving context and source chains.
* `cargo add thiserror` - Produces idiomatic typed errors without handwritten `Display` and `Error` implementations.

## Macros

* `cargo add duplicate` - Removes repetitive declarations when declarative macros alone become verbose.

## Collections and Iterators

* `cargo add dashmap` - Allows concurrent map access without wrapping a `HashMap` in one global lock.
* `cargo add indexmap` - Preserves deterministic insertion order while retaining hash-table lookups.
* `cargo add itertools` - Makes complex iterator pipelines shorter and more expressive.

## Initialization and Shared State

| std                             | crate                               | advantage                                                                |
|---------------------------------|-------------------------------------|--------------------------------------------------------------------------|
| std::cell::{OnceCell, LazyCell} | once_cell::unsync::{OnceCell, Lazy} | Avoids an external dependency for single-threaded one-time initialization. |
| std::sync::OnceLock             | once_cell::sync::OnceCell           | Avoids an external dependency for thread-safe one-time initialization.   |
| std::sync::LazyLock             | once_cell::sync::Lazy               | Avoids an external dependency for thread-safe lazy initialization.       |

* `cargo add arc-swap` - Avoids read-side locking when shared `Arc` values are read frequently and replaced occasionally.

## Data Types

### UUID

* `cargo add uuid --features v4,fast-rng` - Provides standards-compliant UUIDs with fast random v4 generation.
* `cargo add short-uuid` - Produces compact, reversible UUID strings for display and storage.

### Bytes

* `cargo add byteorder bytes` - Combines explicit endian conversion with cheap, shareable byte buffers.

### Enum Utilities

* `cargo add num_enum` - Eliminates handwritten checked conversions between primitives and enum variants.
* `cargo add strum --features derive` - Generates parsing, display, iteration, and metadata code for enums.

## Date and Time

1. `cargo add jiff --features serde` - Prefer its robust time-zone-aware arithmetic and modern Temporal-inspired API.
2. `cargo add time --features formatting,macros` - Choose it when compact calendar types and formatting are sufficient.

## Numeric and Mathematical

### Random

1. `cargo add rand` - Prefer its broad RNG, distribution, and ecosystem support.
2. `cargo add fastrand` - Choose it for a tiny API and fast non-cryptographic random values.

### Decimal

1. `cargo add rust_decimal` - Prefer bounded fixed precision to avoid floating-point rounding in financial calculations.
2. `cargo add bigdecimal` - Choose arbitrary precision when values can exceed `Decimal::MAX` 7.92e28.

### Big Integers

* `cargo add num-bigint` - Removes integer size limits when values can exceed `i128::MAX` 1.7e38.

## Logging

* `cargo add log --features release_max_level_info` - Decouples libraries from a concrete logging backend.
* `cargo add env_logger` - Adds lightweight logging controlled at runtime through environment variables.

## Text Processing

### Pattern Matching

1. `cargo add regex` - Prefer flexible, Unicode-aware matching with predictable worst-case search time instead of backtracking.
2. `cargo add aho-corasick` - Choose it to search for many literal patterns in a single pass.

### Sorting

* `cargo add alphanumeric-sort` - Produces natural ordering such as `item2` before `item10`.

## Paths and File Discovery

### Home and User Directories

1. `std::env::home_dir()` - Prefer this dependency-free option when only the current user's home directory is needed.
2. `cargo add directories` - Choose platform-native config, cache, data, and user directories without OS-specific code.

### Paths and Globbing

* `cargo add camino` - Avoids repeated UTF-8 checks when application paths must be valid strings.
* `cargo add glob` - Selects groups of filesystem paths concisely with familiar wildcard patterns.

## Data Formats and Serialization

### Serde

* `cargo add serde --features derive` - Avoids format-specific conversion code through a shared derive-based data model.
* `cargo add serde_with` - Handles awkward wire representations without custom serializer boilerplate.
* `cargo add serde_repr` - Preserves numeric wire formats for fieldless enums with a derive.

### JSON

* `cargo add serde_json` - Reuses Serde models for fast, interoperable JSON conversion.
* `cargo add serde_json_path` - Avoids manual tree traversal for complex JSON queries.

### TOML

* `cargo add toml` - Reuses Serde models for Rust-friendly TOML configuration files.

### YAML

* `cargo add saphyr` - Provides pure-Rust YAML 1.2 compliance for both parsing and emitting.

### XML

1. `cargo add roxmltree` - Prefer fast read-only traversal when the whole XML document fits in memory.
2. `cargo add quick_xml` - Choose streaming, writing, async I/O, or Serde support for larger workflows.

### Schema

* `cargo add schemars` - Keeps JSON schemas synchronized with Rust types through derives.

### Binary-to-Text Encoding

* `cargo add base64` - Provides configurable, allocation-aware Base64 encoding and decoding.

### URL Encoding

* `cargo add serde_urlencoded` - Reuses Serde models for form and query encoding instead of manual key-value pairs.

## Excel Processing

* `cargo add calamine` - Reads multiple spreadsheet formats without requiring Excel or native libraries.
* `cargo add rust_xlsxwriter --features zlib,ryu` - Creates feature-rich XLSX files without requiring Excel.

## Configuration

1. `cargo add envy dotenvy` - Prefer this small combination for `.env` loading and typed environment configuration.
2. `cargo add config --no-default-features --features convert-case,yaml` - Choose it when multiple configuration sources need precedence and merging.

## Caching

* `cargo add reqwest-middleware http-cache-reqwest` - Adds reusable middleware and standards-aware caching to Reqwest clients.
* `cargo add cached` - Removes memoization boilerplate through macros and ready-made cache stores.

## Databases

### Embedded KV

* `cargo add rocksdb` - Provides durable, high-throughput key-value storage without running a database server.

### PostgreSQL Client

* `cargo add tokio-postgres --features with-serde_json-1,with-jiff-0_2` - Keeps PostgreSQL access lightweight and close to the native protocol.
* `cargo add deadpool-postgres` - Adds async pooling and statement caching without changing tokio-postgres semantics.
* `cargo add postgres-from-row` - Removes repetitive PostgreSQL row-to-struct extraction code.
* `cargo add postgres-types --features derive` - Removes handwritten `ToSql` and `FromSql` implementations for custom types.

### SQL Toolkit

* `cargo add sqlx --features runtime-tokio,postgres` - Retains direct SQL control while adding compile-time query validation and pooling.
* `cargo add jiff-sqlx --features postgres` - Keeps Jiff types usable with SQLx without reverting to another date-time crate.

### ORM

* `cargo add sea-orm --features sqlx-postgres,runtime-tokio,macros` - Reduces CRUD and relationship boilerplate with an entity-based async ORM.

## Async and Concurrency

### Async Runtime and Utilities

* `cargo add futures` - Supplies runtime-neutral `Future` and `Stream` combinators shared across async ecosystems.
* `cargo add tokio --features full` - Combines a mature scheduler, async I/O, timers, and synchronization in one runtime.
* `cargo add async-channel` - Keeps multi-producer, multi-consumer channels independent of any async runtime.

### Data Parallelism

* `cargo add rayon` - Parallelizes iterator workloads with minimal code and work-stealing scheduling.

## HTTP and Web

### HTTP Client

* `cargo add reqwest --features json,gzip` - Combines ergonomic async HTTP with JSON and transparent gzip support.

### HTML Parsing

* `cargo add scraper` - Provides browser-grade HTML parsing and CSS selectors without browser automation.

### Web Framework

* `cargo add axum` - Uses Tower middleware and Rust types to keep web handlers modular and testable.
* `cargo add axum-extra --features typed-header` - Avoids custom extractors for common typed Axum patterns.
* `cargo add tower-http --features cors` - Adds reusable CORS middleware without custom Tower layers.

### Authentication and Validation

* `cargo add jsonwebtoken` - Provides interoperable JWT signing and verification across common algorithms.
* `cargo add validator --features derive` - Keeps validation rules next to data types through derives.

## Web3

* `cargo add alloy` - Unifies Ethereum types, ABI handling, providers, and signing in a modular ecosystem.

## CLI and Terminal

### Terminal Styling

1. `cargo add anstream anstyle` - Prefer automatic ANSI adaptation for TTY detection, color environment variables, and Windows consoles.
2. `cargo add colored enable-ansi-support` - Choose fluent string styling when explicit Windows ANSI setup is acceptable.

### Tables

* `cargo add comfy-table` - Builds readable, adaptive terminal tables with little formatting code.

### Terminal Control

* `cargo add crossterm --no-default-features --features events` - Provides one terminal event and control API across Unix and Windows.

### Command-Line Parsing

* `cargo add clap --features derive` - Generates robust parsers, validation, and help text from typed derives.

### Interactive Prompts

1. `cargo add dialoguer --no-default-features` - Prefer focused prompts with flexible themes and minimal UI assumptions.
2. `cargo add cliclack` - Choose a cohesive, polished experience for multi-step command-line interactions.

### Progress

* `cargo add indicatif` - Adds efficient progress bars, spinners, and multi-progress rendering.

## Desktop UI

* `cargo add rfd --no-default-features` - Opens native dialogs without committing the application to a full GUI toolkit.

## System Information

### General System Metrics

* `cargo add sysinfo` - Replaces platform-specific code with one API for broad system and process metrics.

### CPU Counts

* `cargo add num_cpus` - Provides simple, infallible logical and physical CPU counts with affinity awareness.

### Network Interfaces

* `cargo add netdev` - Exposes richer network interface and address details than general system-information crates.

## Cryptography

* [hashes](https://github.com/RustCrypto/hashes) - Provides a consistent family of pure-Rust cryptographic hash implementations.

## Message Queue

* `cargo add pulsar --no-default-features --features tokio-runtime,compression` - Integrates Apache Pulsar with Tokio while reducing payload size through compression.

## Data Analysis

### DataFrames

* `cargo add polars --features parquet,lazy,is_in,rank,abs,streaming,cutqcut,propagate_nans` - Accelerates columnar analytics with lazy optimization, streaming, and Parquet support.

### N-Dimensional Arrays

* `cargo add ndarray --features rayon` - Brings NumPy-like N-dimensional arrays with optional Rayon parallelism.

## Versioning

* `cargo add semver` - Avoids incorrect version-string comparisons by implementing Semantic Versioning rules.

## Process and Signals

* `cargo add duct` - Makes pipelines, redirection, and subprocess composition safer than shell strings.
* `cargo add ctrlc` - Enables graceful shutdown without manual platform-specific Ctrl-C handling.

## Language Bindings

* [pyo3](https://github.com/PyO3/pyo3) - Shares Rust code with Python while retaining native performance and type safety.
