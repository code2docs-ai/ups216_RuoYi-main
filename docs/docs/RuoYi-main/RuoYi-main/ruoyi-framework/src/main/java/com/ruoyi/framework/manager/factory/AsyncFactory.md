# 基础信息

|      |      |
|------|------|
| 名称 | AsyncFactory |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-framework/src/main/java/com/ruoyi/framework/manager/factory/AsyncFactory.java |
| 包名 | com.ruoyi.framework.manager.factory |
| 依赖项 | ['java.util.TimerTask', 'org.slf4j.Logger', 'org.slf4j.LoggerFactory', 'com.ruoyi.common.constant.Constants', 'com.ruoyi.common.utils.AddressUtils', 'com.ruoyi.common.utils.LogUtils', 'com.ruoyi.common.utils.ServletUtils', 'com.ruoyi.common.utils.ShiroUtils', 'com.ruoyi.common.utils.StringUtils', 'com.ruoyi.common.utils.spring.SpringUtils', 'com.ruoyi.framework.shiro.session.OnlineSession', 'com.ruoyi.system.domain.SysLogininfor', 'com.ruoyi.system.domain.SysOperLog', 'com.ruoyi.system.domain.SysUserOnline', 'com.ruoyi.system.service.ISysOperLogService', 'com.ruoyi.system.service.ISysUserOnlineService', 'com.ruoyi.system.service.impl.SysLogininforServiceImpl', 'eu.bitwalker.useragentutils.UserAgent'] |
| 概述说明 | AsyncFactory类支持同步会话、日志记录和登录管理。 |

# 说明

AsyncFactory类具备三大核心功能：首先，它支持同步会话管理，确保操作的一致性和稳定性；其次，它能够记录操作日志，便于追踪和审计系统行为；最后，它还负责管理登录信息，保障用户身份验证的安全性和有效性。这些功能共同提升了系统的可靠性和可维护性。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| AsyncFactory | class | AsyncFactory类提供同步会话、记录操作日志和登录信息的功能。 |



## 类 AsyncFactory

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | AsyncFactory |
| 说明 | AsyncFactory类提供同步会话、记录操作日志和登录信息的功能。 |


### UML类图

```mermaid
classDiagram
    class AsyncFactory {
        -Logger sys_user_logger
        +TimerTask syncSessionToDb(OnlineSession session)
        +TimerTask recordOper(SysOperLog operLog)
        +TimerTask recordLogininfor(String username, String status, String message, Object... args)
    }

    class OnlineSession {
        +String getId()
        +String getDeptName()
        +String getLoginName()
        +Date getStartTimestamp()
        +Date getLastAccessTime()
        +long getTimeout()
        +String getHost()
        +String getBrowser()
        +String getOs()
        +String getStatus()
    }

    class SysUserOnline {
        +void setSessionId(String sessionId)
        +void setDeptName(String deptName)
        +void setLoginName(String loginName)
        +void setStartTimestamp(Date startTimestamp)
        +void setLastAccessTime(Date lastAccessTime)
        +void setExpireTime(long expireTime)
        +void setIpaddr(String ipaddr)
        +void setLoginLocation(String loginLocation)
        +void setBrowser(String browser)
        +void setOs(String os)
        +void setStatus(String status)
    }

    class SysOperLog {
        +void setOperLocation(String operLocation)
        +void setOperIp(String operIp)
    }

    class SysLogininfor {
        +void setLoginName(String loginName)
        +void setIpaddr(String ipaddr)
        +void setLoginLocation(String loginLocation)
        +void setBrowser(String browser)
        +void setOs(String os)
        +void setMsg(String msg)
        +void setStatus(String status)
    }

    class AddressUtils {
        +String getRealAddressByIP(String ip)
    }

    class SpringUtils {
        +T getBean(Class~T~ clazz)
    }

    class UserAgent {
        +String getOperatingSystem()
        +String getBrowser()
    }

    class ServletUtils {
        +HttpServletRequest getRequest()
    }

    class ShiroUtils {
        +String getIp()
    }

    class LogUtils {
        +String getBlock(String str)
    }

    class Constants {
        <<Interface>>
        +String LOGIN_SUCCESS
        +String LOGOUT
        +String REGISTER
        +String LOGIN_FAIL
        +String SUCCESS
        +String FAIL
    }

    class ISysUserOnlineService {
        <<Interface>>
        +void saveOnline(SysUserOnline online)
    }

    class ISysOperLogService {
        <<Interface>>
        +void insertOperlog(SysOperLog operLog)
    }

    class SysLogininforServiceImpl {
        +void insertLogininfor(SysLogininfor logininfor)
    }

    AsyncFactory --> OnlineSession : 使用
    AsyncFactory --> SysUserOnline : 创建
    AsyncFactory --> SysOperLog : 使用
    AsyncFactory --> SysLogininfor : 创建
    AsyncFactory --> AddressUtils : 调用
    AsyncFactory --> SpringUtils : 调用
    AsyncFactory --> UserAgent : 使用
    AsyncFactory --> ServletUtils : 调用
    AsyncFactory --> ShiroUtils : 调用
    AsyncFactory --> LogUtils : 调用
    AsyncFactory --> Constants : 使用
    AsyncFactory --> ISysUserOnlineService : 调用
    AsyncFactory --> ISysOperLogService : 调用
    AsyncFactory --> SysLogininforServiceImpl : 调用
```

这段代码定义了一个`AsyncFactory`类，用于创建异步任务。它包含三个静态方法，分别用于同步会话到数据库、记录操作日志和记录登录信息。每个方法返回一个`TimerTask`对象，该对象在运行时执行相应的操作。代码中使用了多个辅助类，如`OnlineSession`、`SysUserOnline`、`SysOperLog`、`SysLogininfor`等，来处理不同的业务逻辑。`AsyncFactory`类通过调用`SpringUtils`获取服务实例，并使用`AddressUtils`、`UserAgent`、`ServletUtils`、`ShiroUtils`等工具类来获取必要的信息。


### 内部方法调用关系图

```mermaid
graph TD
    A["类AsyncFactory"]
    B["属性: Logger sys_user_logger"]
    C["方法: TimerTask syncSessionToDb(OnlineSession session)"]
    D["方法: TimerTask recordOper(SysOperLog operLog)"]
    E["方法: TimerTask recordLogininfor(String username, String status, String message, Object... args)"]
    F["创建TimerTask对象"]
    G["重写run方法"]
    H["创建SysUserOnline对象"]
    I["设置Session信息"]
    J["调用SpringUtils.getBean(ISysUserOnlineService.class).saveOnline(online)"]
    K["设置操作日志地点"]
    L["调用SpringUtils.getBean(ISysOperLogService.class).insertOperlog(operLog)"]
    M["获取UserAgent和IP"]
    N["构建日志信息"]
    O["获取客户端操作系统和浏览器"]
    P["创建SysLogininfor对象"]
    Q["设置登录信息"]
    R["判断日志状态"]
    S["调用SpringUtils.getBean(SysLogininforServiceImpl.class).insertLogininfor(logininfor)"]

    A --> B
    A --> C
    A --> D
    A --> E
    C --> F
    F --> G
    G --> H
    H --> I
    I --> J
    D --> F
    F --> G
    G --> K
    K --> L
    E --> M
    M --> N
    N --> O
    O --> P
    P --> Q
    Q --> R
    R --> S
```

这段代码定义了一个名为 `AsyncFactory` 的类，其中包含了三个静态方法，分别用于生成 `TimerTask` 对象来执行异步任务。`syncSessionToDb` 方法用于将在线用户会话同步到数据库；`recordOper` 方法用于记录操作日志；`recordLogininfor` 方法用于记录用户登录信息。每个方法都返回一个 `TimerTask` 对象，并在其 `run` 方法中执行具体的业务逻辑，如创建对象、设置属性、调用服务等。这些任务通过 `SpringUtils.getBean` 方法获取相应的服务类来执行数据库操作。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| sys_user_logger = LoggerFactory.getLogger("sys-user") | Logger | 定义系统用户日志记录器实例。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| syncSessionToDb | TimerTask | 定时任务同步在线会话信息到数据库。 |
| recordOper | TimerTask | 静态方法创建定时任务，记录操作日志并插入数据库。 |
| recordLogininfor | TimerTask | 记录用户登录信息，包括IP、地址、用户名、状态、消息、操作系统和浏览器，并插入数据库。 |




