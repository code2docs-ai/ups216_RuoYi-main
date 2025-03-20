# 基础信息

|      |      |
|------|------|
| 名称 | ExceptionUtil |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-common/src/main/java/com/ruoyi/common/utils/ExceptionUtil.java |
| 包名 | com.ruoyi.common.utils |
| 依赖项 | ['java.io.PrintWriter', 'java.io.StringWriter', 'org.apache.commons.lang3.exception.ExceptionUtils'] |
| 概述说明 | ExceptionUtil类用于获取异常信息及判断异常原因。 |

# 说明

ExceptionUtil类是一个工具类，主要用于处理异常相关的操作。它提供了两个核心功能：一是获取异常信息，即从异常对象中提取详细的错误描述或堆栈信息；二是判断异常原因，即通过分析异常对象来确定其根本原因或触发条件。这类工具类通常用于简化异常处理流程，帮助开发者更高效地调试和定位问题。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| ExceptionUtil | class | ExceptionUtil类提供获取异常信息和判断异常原因的方法。 |



## 类 ExceptionUtil

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | ExceptionUtil |
| 说明 | ExceptionUtil类提供获取异常信息和判断异常原因的方法。 |


### UML类图

```mermaid
classDiagram
    class ExceptionUtil {
        <<Utility>>
        +String getExceptionMessage(Throwable e)
        +String getRootErrorMessage(Exception e)
        +boolean isCausedBy(Throwable e, Class<? extends Throwable> cause)
    }

    class StringWriter {
        +StringWriter()
        +void write(String str)
        +String toString()
    }

    class PrintWriter {
        +PrintWriter(Writer out, boolean autoFlush)
        +void print(Object obj)
        +void println(Object obj)
    }

    class ExceptionUtils {
        <<Utility>>
        +Throwable getRootCause(Throwable throwable)
    }

    class StringUtils {
        <<Utility>>
        +String defaultString(String str)
    }

    ExceptionUtil --> StringWriter : 使用
    ExceptionUtil --> PrintWriter : 使用
    ExceptionUtil --> ExceptionUtils : 使用
    ExceptionUtil --> StringUtils : 使用
```

这段代码定义了一个名为 `ExceptionUtil` 的工具类，用于处理异常相关的操作。该类包含三个静态方法：`getExceptionMessage` 用于获取异常的详细错误信息，`getRootErrorMessage` 用于获取异常的根错误信息，`isCausedBy` 用于检测异常是否由特定类型的异常触发。`ExceptionUtil` 类依赖于 `StringWriter`、`PrintWriter`、`ExceptionUtils` 和 `StringUtils` 等工具类来完成其功能。这些工具类分别用于字符串处理、异常根原因获取以及字符串默认值处理等操作。


### 内部方法调用关系图

```mermaid
graph TD
    A["类ExceptionUtil"]
    B["方法: getExceptionMessage(Throwable e)"]
    C["创建StringWriter对象: StringWriter sw = new StringWriter()"]
    D["打印异常堆栈信息: e.printStackTrace(new PrintWriter(sw, true))"]
    E["返回异常信息: return sw.toString()"]
    F["方法: getRootErrorMessage(Exception e)"]
    G["获取根异常: Throwable root = ExceptionUtils.getRootCause(e)"]
    H["判断根异常是否为null: root = (root == null ? e : root)"]
    I["判断根异常是否为null: if (root == null)"]
    J["返回空字符串: return ''"]
    K["获取异常信息: String msg = root.getMessage()"]
    L["判断异常信息是否为null: if (msg == null)"]
    M["返回'null': return 'null'"]
    N["返回异常信息: return StringUtils.defaultString(msg)"]
    O["方法: isCausedBy(Throwable e, Class<? extends Throwable> cause)"]
    P["判断异常类型是否匹配: if (cause.isAssignableFrom(e.getClass()))"]
    Q["返回true: return true"]
    R["获取异常原因: Throwable t = e.getCause()"]
    S["循环判断异常原因: while (t != null && t != e)"]
    T["判断异常类型是否匹配: if (cause.isAssignableFrom(t.getClass()))"]
    U["返回true: return true"]
    V["获取下一个异常原因: t = t.getCause()"]
    W["返回false: return false"]

    A --> B
    B --> C
    C --> D
    D --> E
    A --> F
    F --> G
    G --> H
    H --> I
    I --> J
    I --> K
    K --> L
    L --> M
    L --> N
    A --> O
    O --> P
    P --> Q
    P --> R
    R --> S
    S --> T
    T --> U
    S --> V
    V --> S
    S --> W
```

这段代码定义了一个`ExceptionUtil`类，其中包含三个方法：`getExceptionMessage`用于获取异常的详细堆栈信息；`getRootErrorMessage`用于获取异常的根原因信息；`isCausedBy`用于判断异常是否由特定类型的异常触发。通过这些方法，可以更方便地处理和诊断异常信息。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| isCausedBy | boolean | 判断异常是否由指定类型引起，递归检查异常链。 |
| getExceptionMessage | String | 获取异常信息并返回字符串。 |
| getRootErrorMessage | String | 获取异常根错误信息，若无则返回空或null。 |




