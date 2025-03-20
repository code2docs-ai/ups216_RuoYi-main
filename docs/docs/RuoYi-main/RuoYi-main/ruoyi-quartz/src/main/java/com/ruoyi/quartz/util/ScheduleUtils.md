# 基础信息

|      |      |
|------|------|
| 名称 | ScheduleUtils |
| 编码语言 | .java |
| 代码路径 | RuoYi-main/ruoyi-quartz/src/main/java/com/ruoyi/quartz/util/ScheduleUtils.java |
| 包名 | com.ruoyi.quartz.util |
| 依赖项 | ['org.quartz.CronScheduleBuilder', 'org.quartz.CronTrigger', 'org.quartz.Job', 'org.quartz.JobBuilder', 'org.quartz.JobDetail', 'org.quartz.JobKey', 'org.quartz.Scheduler', 'org.quartz.SchedulerException', 'org.quartz.TriggerBuilder', 'org.quartz.TriggerKey', 'com.ruoyi.common.constant.Constants', 'com.ruoyi.common.constant.ScheduleConstants', 'com.ruoyi.common.exception.job.TaskException', 'com.ruoyi.common.exception.job.TaskException.Code', 'com.ruoyi.common.utils.StringUtils', 'com.ruoyi.common.utils.spring.SpringUtils', 'com.ruoyi.quartz.domain.SysJob'] |
| 概述说明 | ScheduleUtils类实现Quartz任务管理，涵盖任务创建、触发策略及白名单检查。 |

# 说明

ScheduleUtils类是一个提供Quartz任务管理功能的工具类，主要包含任务创建、触发策略配置以及白名单检查等核心功能。通过该类，用户可以高效地创建和管理Quartz任务，灵活设置任务的触发策略，并确保任务执行前通过白名单检查，从而提升任务管理的安全性和可靠性。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| ScheduleUtils | class | ScheduleUtils类提供Quartz任务管理功能，包括任务创建、触发策略及白名单检查。 |



## 类 ScheduleUtils

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | ScheduleUtils |
| 说明 | ScheduleUtils类提供Quartz任务管理功能，包括任务创建、触发策略及白名单检查。 |


### UML类图

```mermaid
classDiagram
    class ScheduleUtils {
        +static Class~? extends Job~ getQuartzJobClass(SysJob sysJob)
        +static TriggerKey getTriggerKey(Long jobId, String jobGroup)
        +static JobKey getJobKey(Long jobId, String jobGroup)
        +static void createScheduleJob(Scheduler scheduler, SysJob job) throws SchedulerException, TaskException
        +static CronScheduleBuilder handleCronScheduleMisfirePolicy(SysJob job, CronScheduleBuilder cb) throws TaskException
        +static boolean whiteList(String invokeTarget)
    }

    class Scheduler {
        <<Interface>>
    }

    class SysJob {
    }

    class Job {
        <<Interface>>
    }

    class TriggerKey {
    }

    class JobKey {
    }

    class JobDetail {
    }

    class CronScheduleBuilder {
    }

    class CronTrigger {
    }

    class TaskException {
    }

    class StringUtils {
    }

    class Constants {
    }

    class SpringUtils {
    }

    class QuartzJobExecution {
    }

    class QuartzDisallowConcurrentExecution {
    }

    ScheduleUtils --> Scheduler : 依赖
    ScheduleUtils --> SysJob : 依赖
    ScheduleUtils --> Job : 依赖
    ScheduleUtils --> TriggerKey : 依赖
    ScheduleUtils --> JobKey : 依赖
    ScheduleUtils --> JobDetail : 依赖
    ScheduleUtils --> CronScheduleBuilder : 依赖
    ScheduleUtils --> CronTrigger : 依赖
    ScheduleUtils --> TaskException : 依赖
    ScheduleUtils --> StringUtils : 依赖
    ScheduleUtils --> Constants : 依赖
    ScheduleUtils --> SpringUtils : 依赖
    ScheduleUtils --> QuartzJobExecution : 依赖
    ScheduleUtils --> QuartzDisallowConcurrentExecution : 依赖
```

这段代码定义了一个`ScheduleUtils`工具类，用于处理与Quartz调度相关的任务。它包含了获取Quartz任务类、构建任务触发对象、创建定时任务、处理定时任务策略以及检查包名是否为白名单配置等方法。`ScheduleUtils`类依赖于多个其他类，如`Scheduler`、`SysJob`、`Job`、`TriggerKey`、`JobKey`等，以实现其功能。通过这些方法，可以方便地管理和调度定时任务，并确保任务的正确执行。


### 内部方法调用关系图

```mermaid
graph TD
    A["类ScheduleUtils"]
    B["方法: getQuartzJobClass(SysJob sysJob)"]
    C["方法: getTriggerKey(Long jobId, String jobGroup)"]
    D["方法: getJobKey(Long jobId, String jobGroup)"]
    E["方法: createScheduleJob(Scheduler scheduler, SysJob job)"]
    F["方法: handleCronScheduleMisfirePolicy(SysJob job, CronScheduleBuilder cb)"]
    G["方法: whiteList(String invokeTarget)"]
    H["判断: isConcurrent = '0'.equals(sysJob.getConcurrent())"]
    I["返回: QuartzJobExecution.class 或 QuartzDisallowConcurrentExecution.class"]
    J["返回: TriggerKey.triggerKey(ScheduleConstants.TASK_CLASS_NAME + jobId, jobGroup)"]
    K["返回: JobKey.jobKey(ScheduleConstants.TASK_CLASS_NAME + jobId, jobGroup)"]
    L["构建: JobDetail jobDetail = JobBuilder.newJob(jobClass).withIdentity(getJobKey(jobId, jobGroup)).build()"]
    M["构建: CronScheduleBuilder cronScheduleBuilder = CronScheduleBuilder.cronSchedule(job.getCronExpression())"]
    N["处理: handleCronScheduleMisfirePolicy(job, cronScheduleBuilder)"]
    O["构建: CronTrigger trigger = TriggerBuilder.newTrigger().withIdentity(getTriggerKey(jobId, jobGroup)).withSchedule(cronScheduleBuilder).build()"]
    P["放入参数: jobDetail.getJobDataMap().put(ScheduleConstants.TASK_PROPERTIES, job)"]
    Q["判断: scheduler.checkExists(getJobKey(jobId, jobGroup))"]
    R["删除: scheduler.deleteJob(getJobKey(jobId, jobGroup))"]
    S["判断: StringUtils.isNotNull(CronUtils.getNextExecution(job.getCronExpression()))"]
    T["调度: scheduler.scheduleJob(jobDetail, trigger)"]
    U["判断: job.getStatus().equals(ScheduleConstants.Status.PAUSE.getValue())"]
    V["暂停: scheduler.pauseJob(getJobKey(jobId, jobGroup))"]
    W["判断: job.getMisfirePolicy()"]
    X["返回: cb.withMisfireHandlingInstructionIgnoreMisfires()"]
    Y["返回: cb.withMisfireHandlingInstructionFireAndProceed()"]
    Z["返回: cb.withMisfireHandlingInstructionDoNothing()"]
    AA["抛出异常: TaskException('The task misfire policy ' + job.getMisfirePolicy() + ' cannot be used in cron schedule tasks', Code.CONFIG_ERROR)"]
    AB["获取: packageName = StringUtils.substringBefore(invokeTarget, '(')"]
    AC["计算: count = StringUtils.countMatches(packageName, '.')"]
    AD["判断: count > 1"]
    AE["返回: StringUtils.containsAnyIgnoreCase(invokeTarget, Constants.JOB_WHITELIST_STR)"]
    AF["获取: obj = SpringUtils.getBean(StringUtils.split(invokeTarget, '.')[0])"]
    AG["获取: beanPackageName = obj.getClass().getPackage().getName()"]
    AH["返回: StringUtils.containsAnyIgnoreCase(beanPackageName, Constants.JOB_WHITELIST_STR) && !StringUtils.containsAnyIgnoreCase(beanPackageName, Constants.JOB_ERROR_STR)"]

    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    A --> G
    B --> H
    H --> I
    C --> J
    D --> K
    E --> L
    E --> M
    M --> N
    N --> O
    O --> P
    P --> Q
    Q --> R
    Q --> S
    S --> T
    S --> U
    U --> V
    F --> W
    W --> X
    W --> Y
    W --> Z
    W --> AA
    G --> AB
    AB --> AC
    AC --> AD
    AD --> AE
    AD --> AF
    AF --> AG
    AG --> AH
```

这段代码是一个用于管理定时任务的工具类 `ScheduleUtils`，主要功能包括获取任务类、构建任务触发对象、创建定时任务、处理任务策略以及检查包名是否在白名单中。代码通过多个方法实现了定时任务的创建、调度、暂停和策略处理，并且提供了白名单检查功能以确保任务的安全性。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| handleCronScheduleMisfirePolicy | CronScheduleBuilder | 根据任务策略处理Cron调度器的未触发行为。 |
| getJobKey | JobKey | 根据jobId和jobGroup生成JobKey对象。 |
| getQuartzJobClass | Class<? extends Job> | 根据任务并发性返回相应的Quartz作业类。 |
| createScheduleJob | void | 创建调度任务，检查存在性，处理过期，执行或暂停任务。 |
| whiteList | boolean | 检查调用目标是否在白名单中，通过包名和常量匹配进行验证。 |
| getTriggerKey | TriggerKey | 静态方法返回基于任务ID和组名的触发器键。 |




