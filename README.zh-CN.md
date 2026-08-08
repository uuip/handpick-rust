# 一份简短的 Rust Crate 精选清单

## 错误处理

* `cargo add anyhow` - 让应用程序的错误处理保持简洁，并保留错误上下文与完整错误链。
* `cargo add thiserror` - 无需手写 `Display` 和 `Error` 实现即可定义符合 Rust 习惯的强类型错误。

## 宏

* `cargo add duplicate` - 声明式宏的写法仍然冗长时，可用它批量生成结构相似的声明。

## 集合与迭代器

* `cargo add dashmap` - 无需为整个 `HashMap` 加一把全局锁，即可安全地并发读写映射。
* `cargo add indexmap` - 在保持接近哈希表查询效率的同时，确保迭代顺序与插入顺序一致。
* `cargo add itertools` - 提供丰富的迭代器适配器，让复杂的数据处理链更短、更清晰。

## 初始化与共享状态

| 标准库                          | crate                               | 优势                         |
|---------------------------------|-------------------------------------|------------------------------|
| std::cell::{OnceCell, LazyCell} | once_cell::unsync::{OnceCell, Lazy} | 单线程场景可直接使用标准库完成一次性或惰性初始化，无需引入 `once_cell`。 |
| std::sync::OnceLock             | once_cell::sync::OnceCell           | 多线程场景可直接使用标准库完成线程安全的一次性初始化。 |
| std::sync::LazyLock             | once_cell::sync::Lazy               | 多线程场景可直接使用标准库完成线程安全的惰性初始化。 |

* `cargo add arc-swap` - 共享 `Arc` 值读多写少时，读取无需加锁，可有效减少锁竞争。

## 数据类型

### UUID

* `cargo add uuid --features v4,fast-rng` - 支持标准 UUID 格式，并可快速生成随机 v4 UUID。
* `cargo add short-uuid` - 将 UUID 可逆编码为更短的字符串，便于展示和存储。

### 字节

* `cargo add byteorder bytes` - `byteorder` 负责按指定字节序读写数值，`bytes` 提供可低成本克隆和共享的字节缓冲区。

### 枚举工具

* `cargo add num_enum` - 通过派生生成基本数值与枚举变体之间的安全转换，免去手写转换代码。
* `cargo add strum --features derive` - 通过派生为枚举生成解析、显示、迭代和元数据相关实现。

## 日期与时间

1. `cargo add jiff --features serde` - 需要可靠的时区运算和受 Temporal 启发的现代 API 时优先选择它。
2. `cargo add time --features formatting,macros` - 只需要轻量的日期时间类型、编译期宏和格式化能力时选择它。

## 数值与数学

### 随机数

1. `cargo add rand` - 需要多种随机数生成器、概率分布或生态兼容性时优先选择它。
2. `cargo add fastrand` - 只需要简单、快速的非密码学随机数，并希望减少 API 复杂度时选择它。

### 十进制

1. `cargo add rust_decimal` - 财务等场景优先使用固定精度十进制数，避免二进制浮点舍入误差。
2. `cargo add bigdecimal` - 数值或精度可能超过 `rust_decimal` 的范围时选择任意精度十进制数。

### 大整数

* `cargo add num-bigint` - 需要表示超过原生整数上限的值时，可使用不受固定位数限制的任意精度整数。

## 日志

* `cargo add log --features release_max_level_info` - 让库代码只依赖统一日志接口，不绑定具体日志后端。
* `cargo add env_logger` - 无需复杂配置即可通过环境变量控制日志级别和输出。

## 文本处理

### 模式匹配

1. `cargo add regex` - 需要支持 Unicode 的灵活正则匹配和可预测的最坏搜索时间时优先选择它。
2. `cargo add aho-corasick` - 需要在一次扫描中同时查找大量固定字符串时选择它。

### 排序

* `cargo add alphanumeric-sort` - 按人类习惯进行字母数字混合排序，例如让 `item2` 排在 `item10` 之前。

## 路径与文件查找

### 主目录与平台目录

1. `std::env::home_dir()` - 只需要当前用户主目录时，优先使用标准库，避免增加依赖。
2. `cargo add directories` - 需要遵循各平台规范获取配置、缓存、数据或用户目录时选择它。

### 路径与通配符匹配

* `cargo add camino` - 应用要求路径始终为有效 UTF-8 时，可避免反复进行编码检查和转换。
* `cargo add glob` - 使用熟悉的通配符语法简洁地匹配一组文件系统路径。

## 数据格式与序列化

### Serde

* `cargo add serde --features derive` - 通过统一的 `Serialize` 和 `Deserialize` 派生接口复用数据模型，避免为每种格式单独编写转换代码。
* `cargo add serde_with` - 无需编写自定义序列化器，即可处理特殊的字段表示和转换规则。
* `cargo add serde_repr` - 通过派生让无字段枚举按数值表示进行序列化。

### JSON

* `cargo add serde_json` - 直接复用 Serde 数据模型读写 JSON，减少重复类型转换代码。
* `cargo add serde_json_path` - 使用 JSONPath 查询复杂 JSON 结构，无需手动逐层遍历。

### TOML

* `cargo add toml` - 直接复用 Serde 类型读写 TOML 配置文件。

### YAML

* `cargo add saphyr` - 使用纯 Rust 实现解析和输出符合 YAML 1.2 的文档。

### XML

1. `cargo add roxmltree` - XML 文档可以整体载入内存且只需读取时，优先选择它进行快速树遍历。
2. `cargo add quick_xml` - 处理大型 XML、需要流式读写、异步 I/O 或 Serde 集成时选择它。

### JSON Schema

* `cargo add schemars` - 从 Rust 类型派生 JSON Schema，避免分别维护类型和 Schema 导致二者不一致。

### 二进制到文本编码

* `cargo add base64` - 支持自定义字母表、填充策略和复用缓冲区，便于控制 Base64 编解码行为与内存分配。

### URL 编码

* `cargo add serde_urlencoded` - 直接复用 Serde 类型处理表单和查询字符串，无需手动拼装键值对。

## Excel 处理

* `cargo add calamine` - 无需安装 Excel 或系统原生依赖，即可读取 XLSX、XLS、ODS 等多种电子表格格式。
* `cargo add rust_xlsxwriter --features zlib,ryu` - 无需调用 Excel 即可生成格式丰富的 XLSX 文件。

## 配置

1. `cargo add envy dotenvy` - 配置仅来自环境变量和 `.env` 文件时，优先使用这个轻量组合直接反序列化为强类型结构体。
2. `cargo add config --no-default-features --features convert-case,yaml` - 需要合并文件、环境变量和默认值，并控制覆盖优先级时选择它。

## 缓存

* `cargo add reqwest-middleware http-cache-reqwest` - 为 Reqwest 客户端增加可复用中间件，并按照 HTTP 缓存标准复用响应。
* `cargo add cached` - 通过宏和现成的缓存容器减少函数结果缓存的样板代码。

## 数据库

### 嵌入式 KV

* `cargo add rocksdb` - 无需部署独立数据库服务，即可在进程内获得持久化、高吞吐的键值存储。

### PostgreSQL 客户端

* `cargo add tokio-postgres --features with-serde_json-1,with-jiff-0_2` - 以轻量且贴近原生协议的方式访问 PostgreSQL。
* `cargo add deadpool-postgres` - 在保留 tokio-postgres 使用方式的同时增加异步连接池和预处理语句缓存。
* `cargo add postgres-from-row` - 自动把 PostgreSQL 查询结果行转换为 Rust 结构体，减少逐列取值代码。
* `cargo add postgres-types --features derive` - 通过派生为自定义类型生成 `ToSql` 和 `FromSql` 实现。

### SQL 工具链

* `cargo add sqlx --features runtime-tokio,postgres` - 在保留手写 SQL 的同时获得编译期查询校验和内置连接池。
* `cargo add jiff-sqlx --features postgres` - 让 Jiff 日期时间类型直接参与 SQLx 编解码，无需改用其他日期时间库。

### ORM

* `cargo add sea-orm --features sqlx-postgres,runtime-tokio,macros` - 通过实体模型和关系 API 减少异步 CRUD 的样板代码。

## 异步与并发

### 异步运行时与工具

* `cargo add futures` - 提供与运行时无关的 `Future`、`Stream` 及组合子，便于在不同异步生态间复用代码。
* `cargo add tokio --features full` - 提供成熟的任务调度、异步 I/O、定时器和同步原语，适合构建网络服务。
* `cargo add async-channel` - 提供多生产者、多消费者异步通道，且不绑定 Tokio 等具体运行时。

### 数据并行

* `cargo add rayon` - 通过并行迭代器和工作窃取调度，只需少量改动即可并行处理 CPU 密集型任务。

## HTTP 与 Web

### HTTP 客户端

* `cargo add reqwest --features json,gzip` - 用易用的异步 API 发起 HTTP 请求，并直接处理 JSON 和 gzip 响应。

### HTML 解析

* `cargo add scraper` - 无需启动浏览器即可按浏览器规则解析 HTML，并使用 CSS 选择器提取内容。

### Web 框架

* `cargo add axum` - 借助 Rust 类型系统和 Tower 中间件，让 Web 处理器易于拆分和测试。
* `cargo add axum-extra --features typed-header` - 提供常用的类型化提取器，减少 Axum 项目中的自定义样板代码。
* `cargo add tower-http --features cors` - 直接复用成熟的 CORS 中间件，无需自行实现 Tower 中间件层。

### 认证与校验

* `cargo add jsonwebtoken` - 使用常见算法签发和校验标准 JWT，便于与其他系统互操作。
* `cargo add validator --features derive` - 通过派生把校验规则与类型定义放在一起，减少手写检查代码。

## Web3

* `cargo add alloy` - 以模块化组件统一以太坊类型、ABI、RPC Provider 和签名流程。

## CLI 与终端

### 终端样式

1. `cargo add anstream anstyle` - 优先使用它自动处理 TTY 检测、`NO_COLOR` 等环境变量和 Windows ANSI 兼容。
2. `cargo add colored enable-ansi-support` - 偏好简单的链式字符串着色 API，且可以显式启用 Windows ANSI 时选择它。

### 表格

* `cargo add comfy-table` - 以少量配置生成对齐清晰、可自动适应内容的终端表格。

### 终端控制

* `cargo add crossterm --no-default-features --features events` - 用同一套 API 处理 Unix 和 Windows 的终端事件与控制操作。

### 命令行解析

* `cargo add clap --features derive` - 通过派生生成参数解析、校验和帮助文本，减少手写 CLI 解析代码。

### 交互式提示

1. `cargo add dialoguer --no-default-features` - 只需输入、确认或选择等独立提示，且希望自由定制主题时优先使用它。
2. `cargo add cliclack` - 需要风格统一、视觉更精致的多步骤命令行交互时选择它。

### 进度显示

* `cargo add indicatif` - 可高效渲染进度条、旋转指示器和多个并行进度任务。

## 桌面 UI

* `cargo add rfd --no-default-features` - 无需引入完整 GUI 框架即可调用各平台的原生文件和消息对话框。

## 系统信息

### 通用系统指标

* `cargo add sysinfo` - 通过统一的跨平台 API 获取系统、进程、CPU、内存和磁盘信息。

### CPU 数量

* `cargo add num_cpus` - 通过简单 API 获取逻辑和物理 CPU 数量，并自动考虑 CPU 亲和性，无需处理错误。

### 网络接口

* `cargo add netdev` - 需要比通用系统信息库更完整的网卡和地址信息时使用它。

## 密码学

* [hashes](https://github.com/RustCrypto/hashes) - 以一致的接口提供一组纯 Rust 密码学哈希实现，便于在算法间切换。

## 消息队列

* `cargo add pulsar --no-default-features --features tokio-runtime,compression` - 在 Tokio 应用中异步访问 Apache Pulsar，并使用压缩减少消息传输体积。

## 数据分析

### DataFrame

* `cargo add polars --features parquet,lazy,is_in,rank,abs,streaming,cutqcut,propagate_nans` - 利用列式存储、惰性查询优化、流式执行和 Parquet 支持提高表格数据处理效率。

### N 维数组

* `cargo add ndarray --features rayon` - 提供类似 NumPy 的 N 维数组，并可借助 Rayon 并行执行数值运算。

## 版本管理

* `cargo add semver` - 按语义化版本规则解析和比较版本，避免直接比较字符串得到错误结果。

## 进程与信号

* `cargo add duct` - 无需拼接 Shell 命令字符串，即可安全组合子进程、管道和重定向。
* `cargo add ctrlc` - 用统一接口处理 Ctrl-C，从而在不同平台上执行清理并优雅退出。

## 语言绑定

* [pyo3](https://github.com/PyO3/pyo3) - 让 Python 调用 Rust 代码或在 Rust 中嵌入 Python，同时保留原生性能和类型安全。
