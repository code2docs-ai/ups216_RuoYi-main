# 基础信息

|      |      |
|------|------|
| 名称 | SysLogininfor |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-system/src/main/java/com/ruoyi/system/domain/SysLogininfor.java |
| 包名 | com.ruoyi.system.domain |
| 依赖项 | ['org.apache.commons.lang3.builder.ToStringBuilder', 'org.apache.commons.lang3.builder.ToStringStyle', 'java.util.Date', 'com.ruoyi.common.annotation.Excel', 'com.ruoyi.common.annotation.Excel.ColumnType', 'com.ruoyi.common.core.domain.BaseEntity'] |
| 概述说明 | SysLogininfor类记录登录信息，包含账号、状态、IP、地点、浏览器、系统、消息和时间。 |

# 说明

SysLogininfor类用于记录用户的登录信息，包含多个关键字段。这些字段包括用户的账号信息、登录状态（如成功或失败）、登录时的IP地址、登录地点、使用的浏览器类型、操作系统、相关的消息内容以及登录的具体时间。通过这些字段，SysLogininfor类能够全面、详细地记录每次登录的详细信息，便于后续的审计和分析。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| SysLogininfor | class | SysLogininfor类记录登录信息，包含账号、状态、IP、地点、浏览器、系统、消息和时间等字段。 |



## 类 SysLogininfor

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | SysLogininfor |
| 说明 | SysLogininfor类记录登录信息，包含账号、状态、IP、地点、浏览器、系统、消息和时间等字段。 |


### UML类图

```mermaid
classDiagram
    class BaseEntity {
        <<Interface>>
    }

    class SysLogininfor {
        -Long infoId
        -String loginName
        -String status
        -String ipaddr
        -String loginLocation
        -String browser
        -String os
        -String msg
        -Date loginTime
        +Long getInfoId()
        +void setInfoId(Long infoId)
        +String getLoginName()
        +void setLoginName(String loginName)
        +String getStatus()
        +void setStatus(String status)
        +String getIpaddr()
        +void setIpaddr(String ipaddr)
        +String getLoginLocation()
        +void setLoginLocation(String loginLocation)
        +String getBrowser()
        +void setBrowser(String browser)
        +String getOs()
        +void setOs(String os)
        +String getMsg()
        +void setMsg(String msg)
        +Date getLoginTime()
        +void setLoginTime(Date loginTime)
        +String toString()
    }

    SysLogininfor --> BaseEntity : 继承
```

### 描述
`SysLogininfor` 类继承自 `BaseEntity` 接口，用于管理系统登录信息。它包含多个私有字段，如 `infoId`、`loginName`、`status` 等，分别表示登录信息的唯一标识、用户账号、登录状态等。类中提供了这些字段的 getter 和 setter 方法，以及一个重写的 `toString` 方法，用于将对象转换为字符串表示。该类通过继承 `BaseEntity` 接口，可能实现了某些基础实体类的通用功能。


### 内部方法调用关系图

```mermaid
graph TD
    A["类SysLogininfor"]
    B["属性: Long infoId"]
    C["属性: String loginName"]
    D["属性: String status"]
    E["属性: String ipaddr"]
    F["属性: String loginLocation"]
    G["属性: String browser"]
    H["属性: String os"]
    I["属性: String msg"]
    J["属性: Date loginTime"]
    K["方法: Long getInfoId()"]
    L["方法: void setInfoId(Long infoId)"]
    M["方法: String getLoginName()"]
    N["方法: void setLoginName(String loginName)"]
    O["方法: String getStatus()"]
    P["方法: void setStatus(String status)"]
    Q["方法: String getIpaddr()"]
    R["方法: void setIpaddr(String ipaddr)"]
    S["方法: String getLoginLocation()"]
    T["方法: void setLoginLocation(String loginLocation)"]
    U["方法: String getBrowser()"]
    V["方法: void setBrowser(String browser)"]
    W["方法: String getOs()"]
    X["方法: void setOs(String os)"]
    Y["方法: String getMsg()"]
    Z["方法: void setMsg(String msg)"]
    AA["方法: Date getLoginTime()"]
    AB["方法: void setLoginTime(Date loginTime)"]
    AC["重写方法: String toString()"]

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
    A --> U
    A --> V
    A --> W
    A --> X
    A --> Y
    A --> Z
    A --> AA
    A --> AB
    A --> AC
```

这段代码定义了一个名为`SysLogininfor`的类，该类继承自`BaseEntity`，并包含多个属性及其对应的getter和setter方法。`toString`方法被重写，用于返回对象的字符串表示。该类主要用于存储和操作登录信息，包括用户账号、登录状态、IP地址、登录地点、浏览器类型、操作系统、提示消息和访问时间等。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| loginLocation | String | 登录地点字段定义为私有字符串类型。 |
| msg | String | Excel类中定义了一个私有字符串变量msg，用于存储提示消息。 |
| browser | String | Excel表格中定义了一个名为“浏览器”的私有字符串变量。 |
| os | String | 定义了一个名为操作系统的Excel字段变量。 |
| ipaddr | String | Excel登录地址字段为ipaddr。 |
| loginTime | Date | Excel字段：访问时间，格式为yyyy-MM-dd HH:mm:ss。 |
| status | String | Excel字段"登录状态"：0表示成功，1表示失败。 |
| infoId | Long | Excel列“序号”为长整型数据，字段名为infoId。 |
| serialVersionUID = 1L | long | 定义私有静态常量serialVersionUID，值为1L。 |
| loginName | String | Excel中定义用户账号字段为loginName。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| setBrowser | void | 设置浏览器属性的方法。 |
| getOs | String | 获取操作系统信息的方法。 |
| getStatus | String | 获取状态值的方法。 |
| getLoginTime | Date | 获取登录时间的方法。 |
| getBrowser | String | 该方法返回浏览器字符串。 |
| getLoginName | String | 获取登录名的字符串方法。 |
| setLoginTime | void | 设置登录时间的方法，参数为Date类型。 |
| getIpaddr | String | 该方法返回字符串类型的ipaddr变量值。 |
| getInfoId | Long | 获取信息ID的方法，返回类型为Long。 |
| getLoginLocation | String | 获取登录位置的方法。 |
| setInfoId | void | 设置infoId属性的方法，接收Long类型参数。 |
| setLoginName | void | 设置登录名的方法。 |
| setOs | void | 该方法用于设置操作系统属性。 |
| toString | String | 重写toString方法，返回多行格式的对象信息。 |
| setStatus | void | 设置对象状态的方法，参数为状态字符串。 |
| setMsg | void | 该方法用于设置消息内容，将传入的字符串赋值给成员变量msg。 |
| getMsg | String | 该方法返回字符串变量msg的值。 |
| setIpaddr | void | 设置IP地址的方法。 |
| setLoginLocation | void | 设置用户登录位置的方法。 |




