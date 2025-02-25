# VaccineViewBackend
### **后端服务概述**
VaccineView 后端服务有着可扩展、安全、高效的设计，核心功能为支持VaccineView平台的疫苗情绪跟踪、用户订阅管理和实时通知。后端系统采用Spring Boot作为框架开发，采用微服务架构以增强模块化和可维护性。

## **核心功能**

1. **用户认证与授权**
    - 采用**JWT 认证**机制，确保 API 访问的安全性。
    - 用户可安全注册、登录并管理个性化订阅信息。
2. **疫苗数据管理**
    - 存储**结构化疫苗数据**，包括情绪趋势、疫苗接种统计信息和疫苗接种提供商信息。
    - 采用**MySQL 设计关系型数据库模式**，使用**外键约束和索引**保证数据完整性。
    - 开发**RESTful API**，支持前端获取、筛选和展示疫苗相关数据。
3. **情绪分析 API**
    - VaccineView 收集媒体数据后，通过**自然语言处理 (NLP)**模型分析社交媒体的疫苗相关讨论，在该后端服务提供** API**查询**情绪分析结果**
4. **实时通知系统**
    - 采用**订阅通知服务**，当疫苗相关数据更新时，订阅用户将收到电子邮件提醒。
    - 使用**Debezium**监听 MySQL 二进制日志，实时捕获疫苗数据变更事件。
    - 通过**Kafka**处理实时数据流，实现高效、解耦的消息处理。
    - 使用**Spring Mail 和 SMTP**发送电子邮件通知，确保可靠的信息推送。
5. **自动生成和部署的接口文档**
    - 本后端项目集成了Open API 3

    
## **技术栈与实现**

|组件|使用技术|作用|
|-|-|-|
|**后端框架**|Spring Boot|快速开发高效的后端 API 服务|
|**数据库**|MySQL|关系型数据库，存储疫苗数据和用户信息|
|**ORM 框架**|MyBatis-Plus|简化数据库操作，提高查询性能|
|**认证机制**|JWT  |实现安全的 API 访问和基于角色的权限管理|
|**消息流处理**|Apache Kafka|处理实时疫苗数据更新消息|
|**数据库变更捕获**|Debezium|监听 MySQL 数据变更并推送至 Kafka|
|**邮件服务**|Spring Mail (SMTP)|发送疫苗数据更新通知|
|**API 文档**|SpringDoc OpenAPI (即以前的swagger)|自动生成交互式 API 文档，方便前端开发与测试|


## **后端系统实现**

1. **使用 Spring Boot 开发 API**
    - 采用**RESTful API 架构**，确保模块化和可维护性。
    - 实现**异常处理和输入校验**，防止 API 滥用。
    - 使用**OPENAPI3 (Swagger3)** 生成 API 文档，便于前端团队集成。
2. **数据库优化**
    - 设计**规范化数据库模式**，使用**索引优化查询性能**。
    - 采用**MyBatis-Plus**进行 ORM 数据访问，提高 CRUD 操作效率。
    - 配置**数据库读写分离**，优化查询负载，提高数据库响应速度。
3. **基于 Kafka 和 Debezium 的事件驱动架构**
    - 配置**Debezium 连接器**监听 MySQL 数据库的变更事件。
    - 设定**Kafka 主题**以处理不同类型的疫苗数据更新。
    - 开发**Kafka 消费者服务**，异步处理疫苗数据变更，并触发邮件通知机制。


## 注意
由于对本项目测试环境的安全性考虑，application-dev配置未上传，因此无法直接在拉取后运行