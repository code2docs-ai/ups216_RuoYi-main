# 基础信息

|      |      |
|------|------|
| 名称 | quartz |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-quartz/src/main/java/com/ruoyi/quartz |
| 包名 | RuoYi-main.ruoyi-quartz.src.main.java.com.ruoyi.quartz |
| 概述说明 | Quartz任务调度模块，支持任务执行、Cron处理、日志记录和并发控制。 |

# 说明

## 概述
该代码模块基于RuoYi框架，围绕Quartz任务调度框架的实现和扩展，提供了任务执行、Cron表达式处理、任务管理、日志记录、异常处理等功能。模块通过多个工具类、抽象类、控制器和服务类，确保任务能够准确、安全地调度和执行，同时提供了对Cron表达式的验证和时间计算功能，帮助开发者更好地管理和监控任务。模块的核心功能包括定时任务的配置、调度、执行状态跟踪以及执行日志的记录，适用于需要定时执行任务的业务场景，如数据同步、报表生成、定时通知等。

## 主要业务场景
1. **任务执行**：通过`JobInvokeUtil`类解析目标字符串并调用相应的方法，确保任务能够准确地被执行。`QuartzJobExecution`类继承自`AbstractQuartzJob`，并通过`JobInvokeUtil`执行具体的任务逻辑。
2. **Cron表达式处理**：`CronUtils`类提供了Cron表达式的验证、下次执行时间的计算以及近10次执行时间的列举功能，确保任务调度的准确性和可预测性。
3. **任务管理**：`ScheduleUtils`类提供了任务创建、触发策略配置以及白名单检查等功能，帮助用户高效地创建和管理Quartz任务，确保任务执行的安全性和可靠性。`SysJobController`和`SysJobServiceImpl`类实现了定时任务的初始化、状态查询、暂停与恢复、删除、状态修改、立即运行、新增与更新等功能。
4. **日志记录与异常处理**：`AbstractQuartzJob`抽象类在执行任务前后自动记录日志，并集成了异常处理机制，确保系统的稳定性和可追踪性。`SysJobLogController`和`SysJobLogServiceImpl`类提供了日志查看、列表获取、数据导出、日志删除和清理等功能。
5. **任务并发控制**：`QuartzDisallowConcurrentExecution`类通过配置禁止任务并发执行，确保在同一时间只有一个任务实例在运行，避免数据竞争或资源冲突。
6. **任务定义与日志记录**：通过`SysJob`类定义任务的基本属性，确保任务能够按照预定的策略和条件执行；通过`SysJobLog`类记录任务执行过程中的详细信息，便于后续的查询和分析。
7. **数据库操作与任务监控**：通过`SysJobMapper`和`SysJobLogMapper`接口，模块实现了对定时任务及其执行日志的数据库操作，确保定时任务的管理和监控功能得以实现。


### 包内部结构视图

```mermaid
graph TD
    quartz --> util
    quartz --> task
    quartz --> controller
    quartz --> service
    quartz --> domain
    quartz --> config
    quartz --> mapper
    util --> JobInvokeUtil.java
    util --> CronUtils.java
    util --> AbstractQuartzJob.java
    util --> QuartzJobExecution.java
    util --> QuartzDisallowConcurrentExecution.java
    util --> ScheduleUtils.java
    task --> RyTask.java
    controller --> SysJobController.java
    controller --> SysJobLogController.java
    service --> impl
    service --> ISysJobService.java
    service --> ISysJobLogService.java
    impl --> SysJobServiceImpl.java
    impl --> SysJobLogServiceImpl.java
    domain --> SysJobLog.java
    domain --> SysJob.java
    config --> ScheduleConfig.java
    mapper --> SysJobLogMapper.java
    mapper --> SysJobMapper.java
```

该流程图展示了RuoYi-main/ruoyi-quartz项目中各个模块及其子模块的层级关系。顶层模块为quartz，其下包含util、task、controller、service、domain、config和mapper等子模块。每个子模块下又包含具体的Java文件，如util模块下有JobInvokeUtil.java、CronUtils.java等文件，service模块下包含impl子模块以及ISysJobService.java和ISysJobLogService.java等接口文件。整个结构清晰地反映了项目的文件组织和依赖关系。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [mapper](mapper/_module.md) | package | 内容为空，无法总结。 |
| [config](config/_module.md) | package | 信息为空，无法生成概要描述。 |
| [domain](domain/_module.md) | package | SysJobLog类记录任务日志，包含ID、名称、组名、目标、信息、状态、异常和时间字段。SysJob类定义任务属性，包括ID、名称、组名、调用目标、执行表达式、计划策略、并发控制和状态。 |
| [service](service/_module.md) | package | 该模块实现定时任务和日志管理，支持任务初始化、状态查询、暂停恢复、删除、修改、立即运行、新增更新、Cron校验，以及日志查询、新增、删除、清空功能。 |
| [controller](controller/_module.md) | package | SysJobController管理定时任务，SysJobLogController处理日志数据，均需权限控制。 |
| [task](task/_module.md) | package | RyTask类包含三个方法：ryMultipleParams、ryParams和ryNoParams。 |
| [util](util/_module.md) | package | JobInvokeUtil执行系统任务，CronUtils处理Cron表达式，AbstractQuartzJob定义任务流程，QuartzJobExecution调度任务，QuartzDisallowConcurrentExecution禁止并发，ScheduleUtils管理任务。 |


