# 基础信息

|      |      |
|------|------|
| 名称 | ShiroConfig |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-framework/src/main/java/com/ruoyi/framework/config/ShiroConfig.java |
| 包名 | com.ruoyi.framework.config |
| 依赖项 | ['java.io.ByteArrayInputStream', 'java.io.IOException', 'java.io.InputStream', 'java.util.LinkedHashMap', 'java.util.List', 'java.util.Map', 'javax.servlet.Filter', 'org.apache.commons.io.IOUtils', 'org.apache.shiro.cache.ehcache.EhCacheManager', 'org.apache.shiro.codec.Base64', 'org.apache.shiro.config.ConfigurationException', 'org.apache.shiro.io.ResourceUtils', 'org.apache.shiro.mgt.SecurityManager', 'org.apache.shiro.spring.security.interceptor.AuthorizationAttributeSourceAdvisor', 'org.apache.shiro.spring.web.ShiroFilterFactoryBean', 'org.apache.shiro.web.mgt.DefaultWebSecurityManager', 'org.apache.shiro.web.servlet.SimpleCookie', 'org.springframework.beans.factory.annotation.Qualifier', 'org.springframework.beans.factory.annotation.Value', 'org.springframework.context.annotation.Bean', 'org.springframework.context.annotation.Configuration', 'com.ruoyi.common.constant.Constants', 'com.ruoyi.common.utils.StringUtils', 'com.ruoyi.common.utils.security.CipherUtils', 'com.ruoyi.common.utils.spring.SpringUtils', 'com.ruoyi.framework.config.properties.PermitAllUrlProperties', 'com.ruoyi.framework.shiro.realm.UserRealm', 'com.ruoyi.framework.shiro.rememberMe.CustomCookieRememberMeManager', 'com.ruoyi.framework.shiro.session.OnlineSessionDAO', 'com.ruoyi.framework.shiro.session.OnlineSessionFactory', 'com.ruoyi.framework.shiro.web.CustomShiroFilterFactoryBean', 'com.ruoyi.framework.shiro.web.filter.LogoutFilter', 'com.ruoyi.framework.shiro.web.filter.captcha.CaptchaValidateFilter', 'com.ruoyi.framework.shiro.web.filter.kickout.KickoutSessionFilter', 'com.ruoyi.framework.shiro.web.filter.online.OnlineSessionFilter', 'com.ruoyi.framework.shiro.web.filter.sync.SyncOnlineSessionFilter', 'com.ruoyi.framework.shiro.web.session.OnlineWebSessionManager', 'com.ruoyi.framework.shiro.web.session.SpringSessionValidationScheduler', 'at.pollux.thymeleaf.shiro.dialect.ShiroDialect'] |
| 概述说明 | Shiro配置类集成会话、缓存、过滤、权限及验证码功能。 |

# 说明

Shiro配置类是一个综合性的配置模块，主要用于实现会话管理、缓存机制、过滤器设置、权限控制以及验证码功能。它通过集成这些核心功能，确保系统在用户认证、授权、会话维护和安全防护等方面具备高效且可靠的管理能力。该配置类为开发者提供了灵活且可扩展的框架，以适应不同应用场景下的安全需求。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| ShiroConfig | class | Shiro配置类，包含会话管理、缓存、过滤器、权限控制及验证码等功能。 |



## 类 ShiroConfig

|      |      |
|------|------|
| 访问范围 | @Configuration;public |
| 类型 | class |
| 名称 | ShiroConfig |
| 说明 | Shiro配置类，包含会话管理、缓存、过滤器、权限控制及验证码等功能。 |


### UML类图

```mermaid
classDiagram
    class ShiroConfig {
        -int expireTime
        -int validationInterval
        -int maxSession
        -boolean kickoutAfter
        -boolean captchaEnabled
        -String captchaType
        -String domain
        -String path
        -boolean httpOnly
        -int maxAge
        -String cipherKey
        -String loginUrl
        -String unauthorizedUrl
        -boolean rememberMe
        +EhCacheManager getEhCacheManager()
        +InputStream getCacheManagerConfigFileInputStream()
        +UserRealm userRealm(EhCacheManager cacheManager)
        +OnlineSessionDAO sessionDAO()
        +OnlineSessionFactory sessionFactory()
        +OnlineWebSessionManager sessionManager()
        +SecurityManager securityManager(UserRealm userRealm)
        +LogoutFilter logoutFilter()
        +ShiroFilterFactoryBean shiroFilterFactoryBean(SecurityManager securityManager)
        +OnlineSessionFilter onlineSessionFilter()
        +SyncOnlineSessionFilter syncOnlineSessionFilter()
        +CaptchaValidateFilter captchaValidateFilter()
        +SimpleCookie rememberMeCookie()
        +CustomCookieRememberMeManager rememberMeManager()
        +KickoutSessionFilter kickoutSessionFilter()
        +ShiroDialect shiroDialect()
        +AuthorizationAttributeSourceAdvisor authorizationAttributeSourceAdvisor(SecurityManager securityManager)
    }

    class EhCacheManager {
        +void setCacheManager(net.sf.ehcache.CacheManager cacheManager)
    }

    class UserRealm {
        +void setAuthorizationCacheName(String cacheName)
        +void setCacheManager(EhCacheManager cacheManager)
    }

    class OnlineSessionDAO {
    }

    class OnlineSessionFactory {
    }

    class OnlineWebSessionManager {
        +void setCacheManager(EhCacheManager cacheManager)
        +void setDeleteInvalidSessions(boolean deleteInvalidSessions)
        +void setGlobalSessionTimeout(int globalSessionTimeout)
        +void setSessionIdUrlRewritingEnabled(boolean sessionIdUrlRewritingEnabled)
        +void setSessionValidationScheduler(SessionValidationScheduler sessionValidationScheduler)
        +void setSessionValidationSchedulerEnabled(boolean sessionValidationSchedulerEnabled)
        +void setSessionDAO(OnlineSessionDAO sessionDAO)
        +void setSessionFactory(OnlineSessionFactory sessionFactory)
    }

    class DefaultWebSecurityManager {
        +void setRealm(UserRealm userRealm)
        +void setRememberMeManager(RememberMeManager rememberMeManager)
        +void setCacheManager(EhCacheManager cacheManager)
        +void setSessionManager(OnlineWebSessionManager sessionManager)
    }

    class LogoutFilter {
        +void setLoginUrl(String loginUrl)
    }

    class CustomShiroFilterFactoryBean {
        +void setSecurityManager(SecurityManager securityManager)
        +void setLoginUrl(String loginUrl)
        +void setUnauthorizedUrl(String unauthorizedUrl)
        +void setFilters(Map<String, Filter> filters)
        +void setFilterChainDefinitionMap(LinkedHashMap<String, String> filterChainDefinitionMap)
    }

    class OnlineSessionFilter {
        +void setLoginUrl(String loginUrl)
        +void setOnlineSessionDAO(OnlineSessionDAO onlineSessionDAO)
    }

    class SyncOnlineSessionFilter {
        +void setOnlineSessionDAO(OnlineSessionDAO onlineSessionDAO)
    }

    class CaptchaValidateFilter {
        +void setCaptchaEnabled(boolean captchaEnabled)
        +void setCaptchaType(String captchaType)
    }

    class SimpleCookie {
        +void setDomain(String domain)
        +void setPath(String path)
        +void setHttpOnly(boolean httpOnly)
        +void setMaxAge(int maxAge)
    }

    class CustomCookieRememberMeManager {
        +void setCookie(SimpleCookie cookie)
        +void setCipherKey(byte[] cipherKey)
    }

    class KickoutSessionFilter {
        +void setCacheManager(EhCacheManager cacheManager)
        +void setSessionManager(OnlineWebSessionManager sessionManager)
        +void setMaxSession(int maxSession)
        +void setKickoutAfter(boolean kickoutAfter)
        +void setKickoutUrl(String kickoutUrl)
    }

    class ShiroDialect {
    }

    class AuthorizationAttributeSourceAdvisor {
        +void setSecurityManager(SecurityManager securityManager)
    }

    ShiroConfig --> EhCacheManager : 依赖
    ShiroConfig --> UserRealm : 依赖
    ShiroConfig --> OnlineSessionDAO : 依赖
    ShiroConfig --> OnlineSessionFactory : 依赖
    ShiroConfig --> OnlineWebSessionManager : 依赖
    ShiroConfig --> DefaultWebSecurityManager : 依赖
    ShiroConfig --> LogoutFilter : 依赖
    ShiroConfig --> CustomShiroFilterFactoryBean : 依赖
    ShiroConfig --> OnlineSessionFilter : 依赖
    ShiroConfig --> SyncOnlineSessionFilter : 依赖
    ShiroConfig --> CaptchaValidateFilter : 依赖
    ShiroConfig --> SimpleCookie : 依赖
    ShiroConfig --> CustomCookieRememberMeManager : 依赖
    ShiroConfig --> KickoutSessionFilter : 依赖
    ShiroConfig --> ShiroDialect : 依赖
    ShiroConfig --> AuthorizationAttributeSourceAdvisor : 依赖
```

这段代码定义了一个名为 `ShiroConfig` 的配置类，用于配置 Apache Shiro 安全框架的各个组件。该类通过注解和 Bean 定义来初始化和管理 Shiro 的核心组件，如缓存管理器、会话管理器、安全管理器、过滤器等。每个组件都有其特定的配置和依赖关系，通过这些配置，Shiro 可以实现用户认证、会话管理、权限控制等功能。


### 内部方法调用关系图

```mermaid
graph TD
    A["类ShiroConfig"]
    B["属性: int expireTime"]
    C["属性: int validationInterval"]
    D["属性: int maxSession"]
    E["属性: boolean kickoutAfter"]
    F["属性: boolean captchaEnabled"]
    G["属性: String captchaType"]
    H["属性: String domain"]
    I["属性: String path"]
    J["属性: boolean httpOnly"]
    K["属性: int maxAge"]
    L["属性: String cipherKey"]
    M["属性: String loginUrl"]
    N["属性: String unauthorizedUrl"]
    O["属性: boolean rememberMe"]
    P["方法: EhCacheManager getEhCacheManager()"]
    Q["方法: InputStream getCacheManagerConfigFileInputStream()"]
    R["方法: UserRealm userRealm(EhCacheManager cacheManager)"]
    S["方法: OnlineSessionDAO sessionDAO()"]
    T["方法: OnlineSessionFactory sessionFactory()"]
    U["方法: OnlineWebSessionManager sessionManager()"]
    V["方法: SecurityManager securityManager(UserRealm userRealm)"]
    W["方法: LogoutFilter logoutFilter()"]
    X["方法: ShiroFilterFactoryBean shiroFilterFactoryBean(SecurityManager securityManager)"]
    Y["方法: OnlineSessionFilter onlineSessionFilter()"]
    Z["方法: SyncOnlineSessionFilter syncOnlineSessionFilter()"]
    AA["方法: CaptchaValidateFilter captchaValidateFilter()"]
    AB["方法: SimpleCookie rememberMeCookie()"]
    AC["方法: CustomCookieRememberMeManager rememberMeManager()"]
    AD["方法: KickoutSessionFilter kickoutSessionFilter()"]
    AE["方法: ShiroDialect shiroDialect()"]
    AF["方法: AuthorizationAttributeSourceAdvisor authorizationAttributeSourceAdvisor(SecurityManager securityManager)"]

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
```

这段代码是一个Shiro配置类，用于配置Spring Boot项目中与Shiro安全框架相关的各种设置。它定义了多个属性，如会话超时时间、验证码开关、Cookie设置等，并通过多个Bean方法配置了缓存管理器、会话管理器、安全管理器等组件。这些配置确保了Shiro框架能够正确地处理用户认证、会话管理和权限控制等功能。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| validationInterval | int | Shiro会话验证间隔时间配置项。 |
| maxSession | int | Shiro配置中设置最大会话数为maxSession。 |
| path | String | Shiro配置中定义了cookie路径。 |
| captchaType | String | Shiro配置中用户验证码类型变量captchaType。 |
| expireTime | int | Shiro会话过期时间配置为expireTime变量。 |
| domain | String | Shiro配置中定义Cookie域名的私有字符串变量。 |
| httpOnly | boolean | Shiro配置中Cookie的HttpOnly属性设置。 |
| loginUrl | String | Shiro配置中定义了用户登录URL路径。 |
| unauthorizedUrl | String | Shiro配置中未授权访问的URL路径。 |
| cipherKey | String | Shiro配置中定义cookie加密密钥的私有字符串变量。 |
| captchaEnabled | boolean | Shiro配置中用户验证码功能启用状态。 |
| kickoutAfter | boolean | Shiro配置：会话踢出后是否继续处理。 |
| maxAge | int | Shiro配置中设置Cookie最大存活时间的变量。 |
| rememberMe | boolean | Shiro配置中记住我功能默认关闭。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| rememberMeCookie | SimpleCookie | 创建并配置名为“rememberMe”的SimpleCookie对象。 |
| userRealm | UserRealm | 创建UserRealm实例，设置授权缓存名称和缓存管理器后返回。 |
| sessionFactory | OnlineSessionFactory | 创建并返回一个OnlineSessionFactory实例。 |
| captchaValidateFilter | CaptchaValidateFilter | 创建并配置验证码过滤器实例。 |
| shiroDialect | ShiroDialect | 定义ShiroDialect Bean并返回其实例。 |
| sessionDAO | OnlineSessionDAO | 创建并返回一个OnlineSessionDAO实例。 |
| getEhCacheManager | EhCacheManager | 该方法创建并配置EhCacheManager，根据缓存管理器是否存在进行初始化。 |
| rememberMeManager | CustomCookieRememberMeManager | 创建并配置自定义Cookie记住我管理器，设置Cookie和加密密钥。 |
| securityManager | SecurityManager | 配置安全管理器，设置Realm、记住我、缓存和会话管理。 |
| sessionManager | OnlineWebSessionManager | 配置在线会话管理器，设置缓存、超时、验证调度器等。 |
| getCacheManagerConfigFileInputStream | InputStream | 从类路径读取ehcache-shiro.xml文件并返回输入流，处理异常并确保资源关闭。 |
| onlineSessionFilter | OnlineSessionFilter | 创建并配置在线会话过滤器，设置登录URL和会话DAO后返回。 |
| shiroFilterFactoryBean | ShiroFilterFactoryBean | Shiro过滤器配置，设置登录、权限、静态资源访问及自定义过滤器链。 |
| authorizationAttributeSourceAdvisor | AuthorizationAttributeSourceAdvisor | 创建并配置AuthorizationAttributeSourceAdvisor，设置SecurityManager后返回实例。 |
| logoutFilter | LogoutFilter | 创建并配置LogoutFilter实例，设置登录URL后返回。 |
| syncOnlineSessionFilter | SyncOnlineSessionFilter | 创建并配置同步在线会话过滤器实例，返回配置后的对象。 |
| kickoutSessionFilter | KickoutSessionFilter | 创建并配置KickoutSessionFilter，设置缓存管理器、会话管理器、最大会话数、踢出顺序及重定向地址。 |




