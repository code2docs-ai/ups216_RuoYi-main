# 基础信息

|      |      |
|------|------|
| 名称 | SysUserServiceImpl |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-system/src/main/java/com/ruoyi/system/service/impl/SysUserServiceImpl.java |
| 包名 | com.ruoyi.system.service.impl |
| 依赖项 | ['java.util.ArrayList', 'java.util.List', 'java.util.stream.Collectors', 'javax.validation.ConstraintViolationException', 'javax.validation.Validator', 'org.slf4j.Logger', 'org.slf4j.LoggerFactory', 'org.springframework.beans.factory.annotation.Autowired', 'org.springframework.stereotype.Service', 'org.springframework.transaction.annotation.Transactional', 'org.springframework.util.CollectionUtils', 'com.ruoyi.common.annotation.DataScope', 'com.ruoyi.common.constant.UserConstants', 'com.ruoyi.common.core.domain.entity.SysRole', 'com.ruoyi.common.core.domain.entity.SysUser', 'com.ruoyi.common.core.text.Convert', 'com.ruoyi.common.exception.ServiceException', 'com.ruoyi.common.utils.ExceptionUtil', 'com.ruoyi.common.utils.ShiroUtils', 'com.ruoyi.common.utils.StringUtils', 'com.ruoyi.common.utils.bean.BeanValidators', 'com.ruoyi.common.utils.html.EscapeUtil', 'com.ruoyi.common.utils.security.Md5Utils', 'com.ruoyi.common.utils.spring.SpringUtils', 'com.ruoyi.system.domain.SysPost', 'com.ruoyi.system.domain.SysUserPost', 'com.ruoyi.system.domain.SysUserRole', 'com.ruoyi.system.mapper.SysPostMapper', 'com.ruoyi.system.mapper.SysRoleMapper', 'com.ruoyi.system.mapper.SysUserMapper', 'com.ruoyi.system.mapper.SysUserPostMapper', 'com.ruoyi.system.mapper.SysUserRoleMapper', 'com.ruoyi.system.service.ISysConfigService', 'com.ruoyi.system.service.ISysDeptService', 'com.ruoyi.system.service.ISysUserService'] |
| 概述说明 | SysUserServiceImpl实现用户管理功能，涵盖查询、新增、修改、删除、授权及密码重置操作。 |

# 说明

SysUserServiceImpl是一个实现用户管理功能的类，提供了全面的用户操作功能。该类支持查询用户信息，新增用户记录，修改用户数据，删除用户账户，以及为用户授权和重置密码等操作。通过这些功能，SysUserServiceImpl能够有效地管理和维护系统中的用户信息，确保用户数据的安全性和完整性。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| SysUserServiceImpl | class | SysUserServiceImpl实现用户管理功能，包括查询、新增、修改、删除、授权、密码重置等操作。 |



## 类 SysUserServiceImpl

|      |      |
|------|------|
| 访问范围 | @Service;public |
| 类型 | class |
| 名称 | SysUserServiceImpl |
| 说明 | SysUserServiceImpl实现用户管理功能，包括查询、新增、修改、删除、授权、密码重置等操作。 |


### UML类图

```mermaid
classDiagram
    class SysUserServiceImpl {
        -Logger log
        -SysUserMapper userMapper
        -SysRoleMapper roleMapper
        -SysPostMapper postMapper
        -SysUserPostMapper userPostMapper
        -SysUserRoleMapper userRoleMapper
        -ISysConfigService configService
        -ISysDeptService deptService
        -Validator validator
        +List~SysUser~ selectUserList(SysUser user)
        +List~SysUser~ selectAllocatedList(SysUser user)
        +List~SysUser~ selectUnallocatedList(SysUser user)
        +SysUser selectUserByLoginName(String userName)
        +SysUser selectUserByPhoneNumber(String phoneNumber)
        +SysUser selectUserByEmail(String email)
        +SysUser selectUserById(Long userId)
        +List~SysUserRole~ selectUserRoleByUserId(Long userId)
        +int deleteUserById(Long userId)
        +int deleteUserByIds(String ids)
        +int insertUser(SysUser user)
        +boolean registerUser(SysUser user)
        +int updateUser(SysUser user)
        +int updateUserInfo(SysUser user)
        +void insertUserAuth(Long userId, Long[] roleIds)
        +int resetUserPwd(SysUser user)
        +void insertUserRole(Long userId, Long[] roleIds)
        +void insertUserPost(SysUser user)
        +boolean checkLoginNameUnique(SysUser user)
        +boolean checkPhoneUnique(SysUser user)
        +boolean checkEmailUnique(SysUser user)
        +void checkUserAllowed(SysUser user)
        +void checkUserDataScope(Long userId)
        +String selectUserRoleGroup(Long userId)
        +String selectUserPostGroup(Long userId)
        +String importUser(List~SysUser~ userList, Boolean isUpdateSupport, String operName)
        +int changeStatus(SysUser user)
    }

    class ISysUserService {
        <<Interface>>
        +List~SysUser~ selectUserList(SysUser user)
        +List~SysUser~ selectAllocatedList(SysUser user)
        +List~SysUser~ selectUnallocatedList(SysUser user)
        +SysUser selectUserByLoginName(String userName)
        +SysUser selectUserByPhoneNumber(String phoneNumber)
        +SysUser selectUserByEmail(String email)
        +SysUser selectUserById(Long userId)
        +List~SysUserRole~ selectUserRoleByUserId(Long userId)
        +int deleteUserById(Long userId)
        +int deleteUserByIds(String ids)
        +int insertUser(SysUser user)
        +boolean registerUser(SysUser user)
        +int updateUser(SysUser user)
        +int updateUserInfo(SysUser user)
        +void insertUserAuth(Long userId, Long[] roleIds)
        +int resetUserPwd(SysUser user)
        +boolean checkLoginNameUnique(SysUser user)
        +boolean checkPhoneUnique(SysUser user)
        +boolean checkEmailUnique(SysUser user)
        +void checkUserAllowed(SysUser user)
        +void checkUserDataScope(Long userId)
        +String selectUserRoleGroup(Long userId)
        +String selectUserPostGroup(Long userId)
        +String importUser(List~SysUser~ userList, Boolean isUpdateSupport, String operName)
        +int changeStatus(SysUser user)
    }

    SysUserServiceImpl --> ISysUserService : 实现
```

### 描述
`SysUserServiceImpl` 类实现了 `ISysUserService` 接口，提供了用户管理相关的业务逻辑，包括用户查询、新增、修改、删除、角色分配、权限校验等功能。该类依赖于多个 Mapper 接口和 Service 接口，通过注入的方式获取数据访问层和业务逻辑层的支持。代码中使用了事务管理、数据权限校验等机制，确保数据操作的安全性和一致性。


### 内部方法调用关系图

```mermaid
graph TD
    A["类SysUserServiceImpl"]
    B["属性: Logger log"]
    C["属性: SysUserMapper userMapper"]
    D["属性: SysRoleMapper roleMapper"]
    E["属性: SysPostMapper postMapper"]
    F["属性: SysUserPostMapper userPostMapper"]
    G["属性: SysUserRoleMapper userRoleMapper"]
    H["属性: ISysConfigService configService"]
    I["属性: ISysDeptService deptService"]
    J["属性: Validator validator"]
    K["方法: List<SysUser> selectUserList(SysUser user)"]
    L["方法: List<SysUser> selectAllocatedList(SysUser user)"]
    M["方法: List<SysUser> selectUnallocatedList(SysUser user)"]
    N["方法: SysUser selectUserByLoginName(String userName)"]
    O["方法: SysUser selectUserByPhoneNumber(String phoneNumber)"]
    P["方法: SysUser selectUserByEmail(String email)"]
    Q["方法: SysUser selectUserById(Long userId)"]
    R["方法: List<SysUserRole> selectUserRoleByUserId(Long userId)"]
    S["方法: int deleteUserById(Long userId)"]
    T["方法: int deleteUserByIds(String ids)"]
    U["方法: int insertUser(SysUser user)"]
    V["方法: boolean registerUser(SysUser user)"]
    W["方法: int updateUser(SysUser user)"]
    X["方法: int updateUserInfo(SysUser user)"]
    Y["方法: void insertUserAuth(Long userId, Long[] roleIds)"]
    Z["方法: int resetUserPwd(SysUser user)"]
    AA["方法: void insertUserRole(Long userId, Long[] roleIds)"]
    AB["方法: void insertUserPost(SysUser user)"]
    AC["方法: boolean checkLoginNameUnique(SysUser user)"]
    AD["方法: boolean checkPhoneUnique(SysUser user)"]
    AE["方法: boolean checkEmailUnique(SysUser user)"]
    AF["方法: void checkUserAllowed(SysUser user)"]
    AG["方法: void checkUserDataScope(Long userId)"]
    AH["方法: String selectUserRoleGroup(Long userId)"]
    AI["方法: String selectUserPostGroup(Long userId)"]
    AJ["方法: String importUser(List<SysUser> userList, Boolean isUpdateSupport, String operName)"]
    AK["方法: int changeStatus(SysUser user)"]

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
```

这段代码展示了一个用户服务实现类 `SysUserServiceImpl`，它实现了 `ISysUserService` 接口。该类主要负责用户信息的增删改查、用户角色和岗位的管理、用户权限校验等功能。代码中使用了多个 Mapper 接口和 Service 接口来处理用户数据，并通过注解如 `@Transactional` 来管理事务。流程图展示了类与各个属性、方法之间的关系，帮助理解代码的结构和功能。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| validator | Validator | 自动注入验证器实例。 |
| log = LoggerFactory.getLogger(SysUserServiceImpl.class) | Logger | SysUserServiceImpl类中定义了一个私有的静态日志记录器log。 |
| roleMapper | SysRoleMapper | 自动注入SysRoleMapper角色映射器实例。 |
| postMapper | SysPostMapper | 自动注入SysPostMapper类型的postMapper实例。 |
| userMapper | SysUserMapper | 自动注入SysUserMapper实例。 |
| userPostMapper | SysUserPostMapper | 自动注入SysUserPostMapper实例。 |
| configService | ISysConfigService | 自动注入系统配置服务实例。 |
| deptService | ISysDeptService | 自动注入部门服务接口实例。 |
| userRoleMapper | SysUserRoleMapper | 自动注入SysUserRoleMapper实例。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| resetUserPwd | int | 重写resetUserPwd方法，调用updateUserInfo更新用户信息。 |
| selectUserByPhoneNumber | SysUser | 通过手机号查询用户信息的方法。 |
| selectUserByLoginName | SysUser | 重写方法，通过用户名查询系统用户。 |
| checkUserAllowed | void | 检查用户权限，禁止操作超级管理员。 |
| registerUser | boolean | 重写registerUser方法，设置用户类型并插入用户记录。 |
| checkLoginNameUnique | boolean | 检查登录名唯一性，返回是否重复。 |
| selectUserById | SysUser | 重写方法，通过用户ID查询用户信息。 |
| deleteUserById | int | 通过事务删除用户，包括角色关联、岗位关联及用户本身。 |
| insertUser | int | 该方法用于插入用户信息，包括用户、岗位和角色关联。 |
| insertUserAuth | void | 覆盖方法，事务处理，先删除用户角色，再插入新角色。 |
| selectUserByEmail | SysUser | 通过邮箱查询用户信息的Java方法。 |
| deleteUserByIds | int | 通过ID批量删除用户，包括关联的角色和岗位数据。 |
| selectUserRoleGroup | String | 根据用户ID查询角色组并返回角色名称拼接字符串。 |
| checkEmailUnique | boolean | 检查邮箱唯一性，若存在且用户ID不同则返回不唯一，否则返回唯一。 |
| checkUserDataScope | void | 检查用户数据权限，非管理员需验证用户列表，无权限则抛出异常。 |
| checkPhoneUnique | boolean | 检查手机号是否唯一，若存在且用户ID不同则返回不唯一。 |
| changeStatus | int | 重写方法changeStatus，调用userMapper更新用户状态。 |
| selectUnallocatedList | List<SysUser> | 方法覆盖，带数据权限注解，查询未分配用户列表。 |
| selectAllocatedList | List<SysUser> | 该方法使用@DataScope注解，通过userMapper查询已分配用户列表。 |
| updateUser | int | 更新用户信息，包括角色和岗位关联，并返回更新结果。 |
| selectUserList | List<SysUser> | 方法`selectUserList`通过`userMapper`查询用户列表，支持部门和数据权限过滤。 |
| insertUserRole | void | 该方法用于批量插入用户角色，遍历角色ID列表并关联用户ID，最后批量提交。 |
| importUser | String | 导入用户数据，验证并更新或插入用户信息，统计成功与失败数量，返回结果。 |
| insertUserPost | void | 插入用户岗位信息，批量处理用户与岗位关联。 |
| selectUserRoleByUserId | List<SysUserRole> | 根据用户ID查询用户角色列表。 |
| selectUserPostGroup | String | 根据用户ID查询岗位名称，结果以逗号分隔。 |
| updateUserInfo | int | 重写updateUserInfo方法，调用userMapper更新用户信息并返回结果。 |




