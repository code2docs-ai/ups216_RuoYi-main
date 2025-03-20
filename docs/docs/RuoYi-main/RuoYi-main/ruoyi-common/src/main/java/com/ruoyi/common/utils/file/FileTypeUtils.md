# 基础信息

|      |      |
|------|------|
| 名称 | FileTypeUtils |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-common/src/main/java/com/ruoyi/common/utils/file/FileTypeUtils.java |
| 包名 | com.ruoyi.common.utils.file |
| 依赖项 | ['java.io.File', 'org.apache.commons.lang3.StringUtils'] |
| 概述说明 | FileTypeUtils类支持通过文件名或字节码获取无点后缀的文件类型。 |

# 说明

FileTypeUtils类是一个用于获取文件类型的工具类，支持通过文件名和字节码作为输入参数。该类的主要功能是识别文件的后缀名，并返回不包含点号的后缀。这种设计使得文件类型判断更加简洁和直接，适用于需要处理文件类型识别的场景。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| FileTypeUtils | class | FileTypeUtils类提供获取文件类型功能，支持文件名和字节码输入，返回不含点的后缀。 |



## 类 FileTypeUtils

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | FileTypeUtils |
| 说明 | FileTypeUtils类提供获取文件类型功能，支持文件名和字节码输入，返回不含点的后缀。 |


### UML类图

```mermaid
classDiagram
    class FileTypeUtils {
        +String getFileType(File file)
        +String getFileType(String fileName)
        +String getFileExtendName(byte[] photoByte)
    }
```

这段代码定义了一个名为 `FileTypeUtils` 的工具类，用于获取文件的类型或扩展名。类中包含了三个静态方法：`getFileType(File file)` 用于从 `File` 对象中提取文件扩展名；`getFileType(String fileName)` 用于从文件名字符串中提取扩展名；`getFileExtendName(byte[] photoByte)` 通过分析文件字节码的前几个字节来判断文件类型。这些方法都返回文件扩展名，且不包含点号。


### 内部方法调用关系图

```mermaid
graph TD
    A["类FileTypeUtils"]
    B["方法: String getFileType(File file)"]
    C["方法: String getFileType(String fileName)"]
    D["方法: String getFileExtendName(byte[] photoByte)"]
    E["判断: file == null"]
    F["返回: StringUtils.EMPTY"]
    G["调用: getFileType(file.getName())"]
    H["查找: fileName.lastIndexOf('.')"]
    I["判断: separatorIndex < 0"]
    J["返回: ''"]
    K["返回: fileName.substring(separatorIndex + 1).toLowerCase()"]
    L["判断: photoByte[0] == 71 && photoByte[1] == 73 && photoByte[2] == 70 && photoByte[3] == 56 && (photoByte[4] == 55 || photoByte[4] == 57) && photoByte[5] == 97"]
    M["设置: strFileExtendName = 'GIF'"]
    N["判断: photoByte[6] == 74 && photoByte[7] == 70 && photoByte[8] == 73 && photoByte[9] == 70"]
    O["设置: strFileExtendName = 'JPG'"]
    P["判断: photoByte[0] == 66 && photoByte[1] == 77"]
    Q["设置: strFileExtendName = 'BMP'"]
    R["判断: photoByte[1] == 80 && photoByte[2] == 78 && photoByte[3] == 71"]
    S["设置: strFileExtendName = 'PNG'"]
    T["返回: strFileExtendName"]

    A --> B
    A --> C
    A --> D
    B --> E
    E -->|是| F
    E -->|否| G
    C --> H
    H --> I
    I -->|是| J
    I -->|否| K
    D --> L
    L -->|是| M
    L -->|否| N
    N -->|是| O
    N -->|否| P
    P -->|是| Q
    P -->|否| R
    R -->|是| S
    R -->|否| T
    M --> T
    O --> T
    Q --> T
    S --> T
```

这段代码展示了`FileTypeUtils`类中的三个方法，分别用于获取文件类型。`getFileType(File file)`方法通过文件名获取文件类型，`getFileType(String fileName)`方法直接通过字符串文件名获取文件类型，`getFileExtendName(byte[] photoByte)`方法通过文件字节码判断文件类型。流程图详细展示了每个方法的逻辑流程，包括条件判断和返回结果。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| getFileType | String | 该方法根据文件名获取文件类型，若文件为空则返回空字符串。 |
| getFileType | String | 该方法通过文件名获取文件类型，返回小写扩展名，若无扩展名则返回空字符串。 |
| getFileExtendName | String | 根据字节数组判断文件扩展名，支持GIF、JPG、BMP、PNG格式。 |




