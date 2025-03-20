# 基础信息

|      |      |
|------|------|
| 名称 | SysPost |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-system/src/main/java/com/ruoyi/system/domain/SysPost.java |
| 包名 | com.ruoyi.system.domain |
| 依赖项 | ['javax.validation.constraints', 'org.apache.commons.lang3.builder.ToStringBuilder', 'org.apache.commons.lang3.builder.ToStringStyle', 'com.ruoyi.common.annotation.Excel', 'com.ruoyi.common.annotation.Excel.ColumnType', 'com.ruoyi.common.core.domain.BaseEntity'] |
| 概述说明 | SysPost类包含岗位ID、编码、名称、排序、状态和标识字段，并提供getter和setter方法。 |

# 说明

SysPost类是一个用于管理岗位信息的实体类，包含岗位ID、编码、名称、排序、状态和标识字段。该类提供了getter和setter方法，用于获取和设置这些字段的值，确保数据的封装性和可访问性。通过这些方法，可以方便地操作和管理岗位信息。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| SysPost | class | SysPost类包含岗位ID、编码、名称、排序、状态和标识字段，提供getter和setter方法。 |



## 类 SysPost

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | SysPost |
| 说明 | SysPost类包含岗位ID、编码、名称、排序、状态和标识字段，提供getter和setter方法。 |


### UML类图

```mermaid
classDiagram
    class BaseEntity {
        <<Interface>>
    }

    class SysPost {
        -Long postId
        -String postCode
        -String postName
        -String postSort
        -String status
        -boolean flag
        +Long getPostId()
        +void setPostId(Long postId)
        +String getPostCode()
        +void setPostCode(String postCode)
        +String getPostName()
        +void setPostName(String postName)
        +String getPostSort()
        +void setPostSort(String postSort)
        +String getStatus()
        +void setStatus(String status)
        +boolean isFlag()
        +void setFlag(boolean flag)
        +String toString()
    }

    SysPost --> BaseEntity : 继承
```

这段代码定义了一个`SysPost`类，它继承自`BaseEntity`接口。`SysPost`类包含多个私有属性，如`postId`、`postCode`、`postName`等，并提供了相应的getter和setter方法。`toString`方法用于返回对象的字符串表示，包含所有属性的值。`SysPost`类通过继承`BaseEntity`接口，扩展了其功能，用于管理岗位相关的信息。


### 内部方法调用关系图

```mermaid
graph TD
    A["类SysPost"]
    B["属性: Long postId"]
    C["属性: String postCode"]
    D["属性: String postName"]
    E["属性: String postSort"]
    F["属性: String status"]
    G["属性: boolean flag"]
    H["方法: Long getPostId()"]
    I["方法: void setPostId(Long postId)"]
    J["方法: String getPostCode()"]
    K["方法: void setPostCode(String postCode)"]
    L["方法: String getPostName()"]
    M["方法: void setPostName(String postName)"]
    N["方法: String getPostSort()"]
    O["方法: void setPostSort(String postSort)"]
    P["方法: String getStatus()"]
    Q["方法: void setStatus(String status)"]
    R["方法: boolean isFlag()"]
    S["方法: void setFlag(boolean flag)"]
    T["重写方法: String toString()"]

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
    A --> Q
    A --> R
    A --> S
    A --> T
```

这段代码定义了一个名为`SysPost`的类，该类继承自`BaseEntity`，并包含了多个属性和方法。属性包括`postId`、`postCode`、`postName`、`postSort`、`status`和`flag`，分别表示岗位的序号、编码、名称、排序、状态以及用户是否存在此岗位的标识。类中提供了这些属性的getter和setter方法，并且在`toString`方法中重写了对象的字符串表示形式，用于输出对象的详细信息。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| serialVersionUID = 1L | long | 定义序列化版本号，确保对象版本兼容性。 |
| postSort | String | 岗位排序字段为数值类型。 |
| postName | String | 岗位名称字段定义为私有字符串类型。 |
| postId | Long | 岗位序号字段为长整型数字。 |
| status | String | Excel字段"状态"映射：0表示正常，1表示停用。 |
| flag = false | boolean | 定义一个私有布尔变量flag，初始值为false。 |
| postCode | String | 岗位编码字段为字符串类型。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| getPostName | String | 岗位名称不能为空且长度不超过50个字符。 |
| setFlag | void | 设置布尔类型标志的方法。 |
| setPostSort | void | 定义方法setPostSort，用于设置postSort属性。 |
| isFlag | boolean | 该方法返回布尔类型的标志变量flag的值。 |
| getPostId | Long | 获取帖子ID的方法，返回类型为Long。 |
| getPostCode | String | 岗位编码长度限制为64字符，不能为空。 |
| setStatus | void | 设置状态的方法，将传入的status赋值给当前对象的status属性。 |
| getStatus | String | 方法getStatus返回status字符串值。 |
| setPostName | void | 设置岗位名称的方法，接收字符串参数并赋值给成员变量。 |
| setPostId | void | 设置帖子ID的方法，将参数postId赋值给类的postId属性。 |
| toString | String | 重写toString方法，返回多行格式的字符串，包含多个属性信息。 |
| getPostSort | String | 方法`getPostSort`返回`postSort`，显示顺序不能为空。 |
| setPostCode | void | 设置邮政编码的方法。 |




