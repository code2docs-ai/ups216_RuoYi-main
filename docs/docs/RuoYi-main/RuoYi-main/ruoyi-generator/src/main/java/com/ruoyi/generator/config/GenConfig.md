# 基础信息

|      |      |
|------|------|
| 名称 | GenConfig |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-generator/src/main/java/com/ruoyi/generator/config/GenConfig.java |
| 包名 | com.ruoyi.generator.config |
| 依赖项 | ['org.springframework.beans.factory.annotation.Value', 'org.springframework.boot.context.properties.ConfigurationProperties', 'org.springframework.context.annotation.PropertySource', 'org.springframework.stereotype.Component'] |
| 概述说明 | GenConfig类配置生成器属性，含作者、包路径、表前缀、去前缀及文件覆盖权限。 |

# 说明

GenConfig类用于配置生成器的各项属性，主要包括作者信息、包路径、表前缀、自动去除前缀的功能以及文件覆盖的权限设置。通过这些配置，用户可以定制生成器的行为，确保生成的代码符合项目需求。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| GenConfig | class | GenConfig类用于配置生成器属性，包括作者、包路径、表前缀、自动去除前缀及文件覆盖权限。 |



## 类 GenConfig

|      |      |
|------|------|
| 访问范围 | @Component;@ConfigurationProperties(prefix = "gen");@PropertySource(value = { "classpath:generator.yml" });public |
| 类型 | class |
| 名称 | GenConfig |
| 说明 | GenConfig类用于配置生成器属性，包括作者、包路径、表前缀、自动去除前缀及文件覆盖权限。 |


### UML类图

```mermaid
classDiagram
    class GenConfig {
        <<Component>>
        <<ConfigurationProperties>>
        <<PropertySource>>
        +static String author
        +static String packageName
        +static boolean autoRemovePre
        +static String tablePrefix
        +static boolean allowOverwrite
        +static String getAuthor()
        +static void setAuthor(String author)
        +static String getPackageName()
        +static void setPackageName(String packageName)
        +static boolean getAutoRemovePre()
        +static void setAutoRemovePre(boolean autoRemovePre)
        +static String getTablePrefix()
        +static void setTablePrefix(String tablePrefix)
        +static boolean isAllowOverwrite()
        +static void setAllowOverwrite(boolean allowOverwrite)
    }
```

**描述：**  
`GenConfig` 类是一个配置类，使用了 `@Component`、`@ConfigurationProperties` 和 `@PropertySource` 注解，用于从 `generator.yml` 文件中加载配置属性。类中定义了多个静态属性，如 `author`、`packageName`、`autoRemovePre`、`tablePrefix` 和 `allowOverwrite`，并提供了对应的 getter 和 setter 方法。这些方法通过 `@Value` 注解将配置文件中的值注入到静态属性中，以便在应用程序中使用。


### 内部方法调用关系图

```mermaid
graph TD
    A["类GenConfig"]
    B["属性: static String author"]
    C["属性: static String packageName"]
    D["属性: static boolean autoRemovePre"]
    E["属性: static String tablePrefix"]
    F["属性: static boolean allowOverwrite"]
    G["方法: static String getAuthor()"]
    H["方法: @Value('${author}') void setAuthor(String author)"]
    I["方法: static String getPackageName()"]
    J["方法: @Value('${packageName}') void setPackageName(String packageName)"]
    K["方法: static boolean getAutoRemovePre()"]
    L["方法: @Value('${autoRemovePre}') void setAutoRemovePre(boolean autoRemovePre)"]
    M["方法: static String getTablePrefix()"]
    N["方法: @Value('${tablePrefix}') void setTablePrefix(String tablePrefix)"]
    O["方法: static boolean isAllowOverwrite()"]
    P["方法: @Value('${allowOverwrite}') void setAllowOverwrite(boolean allowOverwrite)"]

    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    A --> G
    A --> H
    A --> I
    A --> J
    A --> K
    A --> L
    A --> M
    A --> N
    A --> O
    A --> P
```

这段代码定义了一个名为`GenConfig`的类，该类用于配置生成代码的相关属性。类中包含多个静态属性，如`author`、`packageName`、`autoRemovePre`等，每个属性都有对应的`getter`和`setter`方法。`setter`方法通过`@Value`注解从配置文件中读取值并赋值给相应的属性。类通过`@Component`和`@ConfigurationProperties`注解进行配置，并指定了配置文件的路径。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| author | String | 定义了一个公有的静态字符串变量author。 |
| allowOverwrite | boolean | 静态布尔变量允许覆盖操作。 |
| autoRemovePre | boolean | 自动移除前缀的静态布尔变量。 |
| packageName | String | 静态字符串变量，用于存储包名。 |
| tablePrefix | String | 静态字符串变量tablePrefix的声明。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| setAllowOverwrite | void | 设置允许覆盖配置的布尔值方法。 |
| setTablePrefix | void | 通过注解设置表前缀并更新配置。 |
| setAuthor | void | 通过注解设置作者信息并更新配置。 |
| setAutoRemovePre | void | 设置自动移除前缀的配置方法。 |
| getAuthor | String | 方法getAuthor返回作者名称。 |
| getPackageName | String | 获取包名的静态方法。 |
| getTablePrefix | String | 静态方法返回表前缀字符串。 |
| getAutoRemovePre | boolean | 获取自动移除前置配置的布尔值。 |
| isAllowOverwrite | boolean | 静态方法isAllowOverwrite返回allowOverwrite布尔值。 |
| setPackageName | void | 设置包名方法，将传入值赋给GenConfig.packageName。 |




