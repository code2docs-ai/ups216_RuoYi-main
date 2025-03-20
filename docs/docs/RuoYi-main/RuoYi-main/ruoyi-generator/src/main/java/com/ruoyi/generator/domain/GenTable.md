# 基础信息

|      |      |
|------|------|
| 名称 | GenTable |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-generator/src/main/java/com/ruoyi/generator/domain/GenTable.java |
| 包名 | com.ruoyi.generator.domain |
| 依赖项 | ['java.util.List', 'javax.validation.Valid', 'javax.validation.constraints.NotBlank', 'org.apache.commons.lang3.ArrayUtils', 'com.ruoyi.common.constant.GenConstants', 'com.ruoyi.common.core.domain.BaseEntity', 'com.ruoyi.common.utils.StringUtils'] |
| 概述说明 | GenTable类用于生成代码，包含表、列、路径、模板等属性。 |

# 说明

GenTable类是一个用于生成代码的工具类，其主要功能包括管理表信息、列信息、生成路径以及模板类型等属性。通过该类，用户可以定义和配置生成代码所需的关键参数，如表结构、字段属性、代码输出路径以及使用的模板类型，从而实现自动化代码生成。该类旨在简化代码生成过程，提高开发效率。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| GenTable | class | GenTable类用于生成代码，包含表信息、列信息、生成路径、模板类型等属性。 |



## 类 GenTable

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | GenTable |
| 说明 | GenTable类用于生成代码，包含表信息、列信息、生成路径、模板类型等属性。 |


### UML类图

```mermaid
classDiagram
    class BaseEntity {
        <<Interface>>
    }

    class GenTable {
        -Long tableId
        -String tableName
        -String tableComment
        -String subTableName
        -String subTableFkName
        -String className
        -String tplCategory
        -String packageName
        -String moduleName
        -String businessName
        -String functionName
        -String functionAuthor
        -int formColNum
        -String genType
        -String genPath
        -GenTableColumn pkColumn
        -GenTable subTable
        -List~GenTableColumn~ columns
        -String options
        -String treeCode
        -String treeParentCode
        -String treeName
        -String parentMenuId
        -String parentMenuName
        +Long getTableId()
        +void setTableId(Long tableId)
        +String getTableName()
        +void setTableName(String tableName)
        +String getTableComment()
        +void setTableComment(String tableComment)
        +String getSubTableName()
        +void setSubTableName(String subTableName)
        +String getSubTableFkName()
        +void setSubTableFkName(String subTableFkName)
        +String getClassName()
        +void setClassName(String className)
        +String getTplCategory()
        +void setTplCategory(String tplCategory)
        +String getPackageName()
        +void setPackageName(String packageName)
        +String getModuleName()
        +void setModuleName(String moduleName)
        +String getBusinessName()
        +void setBusinessName(String businessName)
        +String getFunctionName()
        +void setFunctionName(String functionName)
        +String getFunctionAuthor()
        +void setFunctionAuthor(String functionAuthor)
        +int getFormColNum()
        +void setFormColNum(int formColNum)
        +String getGenType()
        +void setGenType(String genType)
        +String getGenPath()
        +void setGenPath(String genPath)
        +GenTableColumn getPkColumn()
        +void setPkColumn(GenTableColumn pkColumn)
        +GenTable getSubTable()
        +void setSubTable(GenTable subTable)
        +List~GenTableColumn~ getColumns()
        +void setColumns(List~GenTableColumn~ columns)
        +String getOptions()
        +void setOptions(String options)
        +String getTreeCode()
        +void setTreeCode(String treeCode)
        +String getTreeParentCode()
        +void setTreeParentCode(String treeParentCode)
        +String getTreeName()
        +void setTreeName(String treeName)
        +String getParentMenuId()
        +void setParentMenuId(String parentMenuId)
        +String getParentMenuName()
        +void setParentMenuName(String parentMenuName)
        +boolean isSub()
        +static boolean isSub(String tplCategory)
        +boolean isTree()
        +static boolean isTree(String tplCategory)
        +boolean isCrud()
        +static boolean isCrud(String tplCategory)
        +boolean isSuperColumn(String javaField)
        +static boolean isSuperColumn(String tplCategory, String javaField)
    }

    class GenTableColumn {
        // 假设GenTableColumn类的定义在其他地方
    }

    BaseEntity <|-- GenTable
    GenTable --> GenTableColumn : 包含
    GenTable --> GenTable : 包含
```

**描述：**
`GenTable` 类继承自 `BaseEntity`，主要用于表示数据库表的元数据信息。它包含表的编号、名称、描述、关联的子表信息、实体类名称、生成路径等属性。类中还定义了多个方法用于判断表的类型（如子表、树表、CRUD表）以及是否为超级列。`GenTable` 类与 `GenTableColumn` 类之间存在关联关系，表示表包含多个列信息。


### 内部方法调用关系图

```mermaid
graph TD
    A["类GenTable"]
    B["继承: BaseEntity"]
    C["属性: Long tableId"]
    D["属性: String tableName"]
    E["属性: String tableComment"]
    F["属性: String subTableName"]
    G["属性: String subTableFkName"]
    H["属性: String className"]
    I["属性: String tplCategory"]
    J["属性: String packageName"]
    K["属性: String moduleName"]
    L["属性: String businessName"]
    M["属性: String functionName"]
    N["属性: String functionAuthor"]
    O["属性: int formColNum"]
    P["属性: String genType"]
    Q["属性: String genPath"]
    R["属性: GenTableColumn pkColumn"]
    S["属性: GenTable subTable"]
    T["属性: List<GenTableColumn> columns"]
    U["属性: String options"]
    V["属性: String treeCode"]
    W["属性: String treeParentCode"]
    X["属性: String treeName"]
    Y["属性: String parentMenuId"]
    Z["属性: String parentMenuName"]
    AA["方法: Long getTableId()"]
    AB["方法: void setTableId(Long tableId)"]
    AC["方法: String getTableName()"]
    AD["方法: void setTableName(String tableName)"]
    AE["方法: String getTableComment()"]
    AF["方法: void setTableComment(String tableComment)"]
    AG["方法: String getSubTableName()"]
    AH["方法: void setSubTableName(String subTableName)"]
    AI["方法: String getSubTableFkName()"]
    AJ["方法: void setSubTableFkName(String subTableFkName)"]
    AK["方法: String getClassName()"]
    AL["方法: void setClassName(String className)"]
    AM["方法: String getTplCategory()"]
    AN["方法: void setTplCategory(String tplCategory)"]
    AO["方法: String getPackageName()"]
    AP["方法: void setPackageName(String packageName)"]
    AQ["方法: String getModuleName()"]
    AR["方法: void setModuleName(String moduleName)"]
    AS["方法: String getBusinessName()"]
    AT["方法: void setBusinessName(String businessName)"]
    AU["方法: String getFunctionName()"]
    AV["方法: void setFunctionName(String functionName)"]
    AW["方法: String getFunctionAuthor()"]
    AX["方法: void setFunctionAuthor(String functionAuthor)"]
    AY["方法: int getFormColNum()"]
    AZ["方法: void setFormColNum(int formColNum)"]
    BA["方法: String getGenType()"]
    BB["方法: void setGenType(String genType)"]
    BC["方法: String getGenPath()"]
    BD["方法: void setGenPath(String genPath)"]
    BE["方法: GenTableColumn getPkColumn()"]
    BF["方法: void setPkColumn(GenTableColumn pkColumn)"]
    BG["方法: GenTable getSubTable()"]
    BH["方法: void setSubTable(GenTable subTable)"]
    BI["方法: List<GenTableColumn> getColumns()"]
    BJ["方法: void setColumns(List<GenTableColumn> columns)"]
    BK["方法: String getOptions()"]
    BL["方法: void setOptions(String options)"]
    BM["方法: String getTreeCode()"]
    BN["方法: void setTreeCode(String treeCode)"]
    BO["方法: String getTreeParentCode()"]
    BP["方法: void setTreeParentCode(String treeParentCode)"]
    BQ["方法: String getTreeName()"]
    BR["方法: void setTreeName(String treeName)"]
    BS["方法: String getParentMenuId()"]
    BT["方法: void setParentMenuId(String parentMenuId)"]
    BU["方法: String getParentMenuName()"]
    BV["方法: void setParentMenuName(String parentMenuName)"]
    BW["方法: boolean isSub()"]
    BX["方法: static boolean isSub(String tplCategory)"]
    BY["方法: boolean isTree()"]
    BZ["方法: static boolean isTree(String tplCategory)"]
    CA["方法: boolean isCrud()"]
    CB["方法: static boolean isCrud(String tplCategory)"]
    CC["方法: boolean isSuperColumn(String javaField)"]
    CD["方法: static boolean isSuperColumn(String tplCategory, String javaField)"]

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
    A --> AD
    A --> AE
    A --> AF
    A --> AG
    A --> AH
    A --> AI
    A --> AJ
    A --> AK
    A --> AL
    A --> AM
    A --> AN
    A --> AO
    A --> AP
    A --> AQ
    A --> AR
    A --> AS
    A --> AT
    A --> AU
    A --> AV
    A --> AW
    A --> AX
    A --> AY
    A --> AZ
    A --> BA
    A --> BB
    A --> BC
    A --> BD
    A --> BE
    A --> BF
    A --> BG
    A --> BH
    A --> BI
    A --> BJ
    A --> BK
    A --> BL
    A --> BM
    A --> BN
    A --> BO
    A --> BP
    A --> BQ
    A --> BR
    A --> BS
    A --> BT
    A --> BU
    A --> BV
    A --> BW
    A --> BX
    A --> BY
    A --> BZ
    A --> CA
    A --> CB
    A --> CC
    A --> CD
```

这段代码定义了一个名为 `GenTable` 的类，继承自 `BaseEntity`，主要用于生成数据库表的相关信息。类中包含多个属性，如表ID、表名称、表描述、关联父表信息、生成包路径等，并为每个属性提供了相应的 `getter` 和 `setter` 方法。此外，类中还包含一些用于判断表类型（如子表、树表、CRUD表）以及判断是否为超级列的方法。这些方法通过静态方法实现，便于在类外部调用。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| tableName | String | 表名称字段不能为空。 |
| tableComment | String | 表描述字段不能为空。 |
| treeCode | String | 私有字符串变量treeCode。 |
| serialVersionUID = 1L | long | 定义了一个私有的静态常量序列化版本号。 |
| className | String | 实体类名称字段不能为空。 |
| treeParentCode | String | 定义私有字符串变量treeParentCode。 |
| genPath | String | 私有字符串变量genPath声明。 |
| subTableFkName | String | 私有字符串变量subTableFkName。 |
| options | String | 私有字符串变量options定义。 |
| tableId | Long | 包含一个长整型的表ID字段。 |
| formColNum | int | 私有整型变量formColNum的声明。 |
| subTableName | String | 定义私有字符串变量subTableName。 |
| pkColumn | GenTableColumn | 私有成员变量pkColumn，类型为GenTableColumn。 |
| parentMenuName | String | 私有字符串变量，用于存储父菜单名称。 |
| genType | String | 定义私有字符串变量genType。 |
| parentMenuId | String | 父菜单ID字段为私有字符串类型。 |
| tplCategory | String | 定义了一个私有字符串变量tplCategory。 |
| businessName | String | 业务名不可为空，需确保其非空值。 |
| moduleName | String | 生成模块名不能为空，定义私有字符串变量moduleName。 |
| packageName | String | 生成包路径不能为空，定义私有字符串变量packageName。 |
| subTable | GenTable | 子表变量声明为私有类型GenTable。 |
| treeName | String | 定义了私有字符串变量treeName。 |
| functionName | String | 功能名不能为空，需使用@NotBlank注解验证。 |
| columns | List<GenTableColumn> | Valid注解用于验证私有List类型的columns字段。 |
| functionAuthor | String | 代码片段定义了一个非空字符串变量functionAuthor，用于存储作者信息。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| getTableId | Long | 获取表ID的方法，返回长整型变量tableId。 |
| isTree | boolean | 判断tplCategory是否为树结构模板。 |
| getGenPath | String | 获取genPath路径的公共方法。 |
| setFunctionAuthor | void | 设置函数作者属性的方法。 |
| setParentMenuId | void | 设置父菜单ID的方法。 |
| getParentMenuId | String | 获取父菜单ID的方法。 |
| setPkColumn | void | 设置主键列属性。 |
| getTreeCode | String | 获取treeCode的公共方法。 |
| setBusinessName | void | 设置业务名称的方法。 |
| getSubTableName | String | 该方法返回子表名称。 |
| setFunctionName | void | 设置方法名，将传入参数赋值给类成员变量。 |
| isCrud | boolean | 检查模板类别是否为CRUD操作。 |
| getFunctionName | String | 该方法返回函数名称的字符串值。 |
| setModuleName | void | 设置模块名称的方法。 |
| setTableComment | void | 设置表注释的方法，接受字符串参数并赋值给表注释变量。 |
| setColumns | void | 设置表格列属性方法，接受列列表参数。 |
| getTableName | String | 该方法返回表名。 |
| setClassName | void | 设置类名的公共方法。 |
| setGenPath | void | 设置生成路径的方法。 |
| setSubTableFkName | void | 设置子表外键名称的方法。 |
| getBusinessName | String | 获取业务名称的方法。 |
| getTableComment | String | 获取表注释的Java方法。 |
| getSubTableFkName | String | 获取子表外键名称的方法。 |
| getPackageName | String | 获取包名称的方法。 |
| setTreeCode | void | 设置树形编码的方法。 |
| getTplCategory | String | 获取模板分类的方法。 |
| getParentMenuName | String | 获取父菜单名称的方法。 |
| getModuleName | String | 获取模块名称的方法。 |
| setTableId | void | 该方法用于设置tableId属性。 |
| setPackageName | void | 该方法用于设置包名。 |
| getFunctionAuthor | String | 获取函数作者信息的方法。 |
| setParentMenuName | void | 设置父菜单名称的方法。 |
| getOptions | String | 获取选项字符串的方法。 |
| getClassName | String | 该方法返回类名className的字符串值。 |
| setTreeParentCode | void | 设置树形结构的父节点代码。 |
| getColumns | List<GenTableColumn> | 获取GenTableColumn列表的方法。 |
| isSub | boolean | 该方法检查当前类别是否为子类别。 |
| isTree | boolean | 方法isTree检查当前对象的tplCategory是否为树结构。 |
| isSuperColumn | boolean | 该方法检查指定Java字段是否为超级列。 |
| isCrud | boolean | 判断模板类别是否为CRUD类型。 |
| getPkColumn | GenTableColumn | 获取主键列的方法。 |
| setFormColNum | void | 设置表单列数的方法，接受整数参数并赋值给成员变量。 |
| getFormColNum | int | 获取表单列数的方法，返回值为整数类型。 |
| getTreeParentCode | String | 获取树形结构父节点代码的方法。 |
| setTreeName | void | 设置树名称的方法，将传入的treeName赋值给当前对象的treeName属性。 |
| getTreeName | String | 该方法返回变量treeName的值。 |
| setGenType | void | 设置生成类型的方法，将输入参数赋值给类成员变量。 |
| setOptions | void | 设置选项方法，将传入参数赋值给类成员变量。 |
| isSub | boolean | 该方法检查模板类别是否为子类别，返回布尔值。 |
| setTplCategory | void | 设置模板类别方法，将输入值赋给类变量tplCategory。 |
| setSubTable | void | 设置子表对象。 |
| setTableName | void | 设置表名的方法，将输入值赋给类的表名属性。 |
| getSubTable | GenTable | 获取子表方法返回subTable对象。 |
| getGenType | String | 获取生成类型的方法。 |
| isSuperColumn | boolean | 方法判断字段是否为超级列，根据模板类别和字段名匹配常量数组。 |
| setSubTableName | void | 设置子表名称的方法。 |




