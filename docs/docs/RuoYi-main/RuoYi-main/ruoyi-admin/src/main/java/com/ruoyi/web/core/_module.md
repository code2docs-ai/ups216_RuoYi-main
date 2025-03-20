# 基础信息

|      |      |
|------|------|
| 名称 | core |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-admin/src/main/java/com/ruoyi/web/core |
| 包名 | RuoYi-main.ruoyi-admin.src.main.java.com.ruoyi.web.core |
| 概述说明 | Swagger配置类支持启用状态配置，通过扫描注解生成API文档。 |

# 说明

Swagger配置类用于生成API文档，支持通过扫描注解接口自动生成文档内容。该配置类的启用状态可以根据需要进行灵活配置，确保在不同环境下能够方便地启用或禁用Swagger功能。通过这种方式，开发者可以快速生成并维护API文档，提升开发效率和文档的准确性。


### 包内部结构视图

```mermaid
graph TD
    core --> config
    config --> SwaggerConfig.java
```

流程图展示了RuoYi项目中核心模块的层级关系。`core`目录下包含`config`子目录，而`config`目录中则包含`SwaggerConfig.java`文件。这种结构清晰地反映了Swagger配置文件的存放位置，便于开发人员快速定位和管理相关配置。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [config](config/_module.md) | package | Swagger配置类支持启用状态配置，通过扫描注解生成API文档。 |


