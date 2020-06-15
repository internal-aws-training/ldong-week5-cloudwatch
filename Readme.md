# AWS CouldWatch

## Practice

- 创建cloudwatch event rules，每分钟自动触发Lambda（Lambda功能需要自己实现，向cloudwatch metrics里push自定义的metrics），设置alarm检测task中定义的metric，自定义并监控条件使alarm触发阈值，alarm出发SNS，SNS发告警到邮箱。

- 创建cloudwatch event rules，每分钟自动触发Lambda（输出固定格式的log message）。为lambda log创建metric filter，匹配log message，创建新的metric，自定义并监控条件使alarm触发阈值，alarm出发SNS，SNS发告警到邮箱。

## Output

- 两个cloudformation文件
- 部署cloudformation后，功能完整，邮箱可以收到报警

-----

## Basic

- CloudWatch 是什么？

> Amazon CloudWatch 是一项针对 AWS 云资源和在 AWS 上运行的应用程序的监控服务。使用 Amazon CloudWatch 可以收集和跟踪指标、收集和监控日志文件以及设置警报。Amazon CloudWatch 可以监控各种 AWS 资源，例如 Amazon EC2 实例、Amazon DynamoDB 表、Amazon RDS 数据库实例、应用程序和服务生成的自定义指标以及应用程序生成的所有日志文件。

- 我们为什么要使用CloudWatch？

> 通过使用 Amazon CloudWatch 能够全面地了解系统的资源使用率、应用程序性能和运行状况。通过这些分析结果，我们可以及时做出反应，保证应用程序顺畅运行。

- CloudWatch中的metrics是什么？包括哪些种类？我们可以如何使用metrics？

> Metics 是 CloudWatch 中的基本概念。Metics 表示一个发布到 CloudWatch 并且按时间排序的数据点集。可以把 Metics 视为要监控的变量，而数据点代表该变量随时间变化的值。例如，特定 EC2 实例的 CPU 使用率是 Amazon EC2 提供的一个Metics（指标）。数据点本身可来自于您从中收集数据的任何应用程序或业务活动。

- CloudWatch Events是什么？可以应用在哪些场景？

> Amazon CloudWatch Events (CWE) 是一个描述 AWS 资源更改的系统事件流。该事件流扩充了现有的 CloudWatch 指标和日志流，以提供更为完整的应用程序运行状况和状态概况。可以编写声明式规则，将我们关注的事件与要执行的自动化操作关联起来。
> 目前支持 Amazon EC2、Auto Scaling 和 AWS CloudTrail。通过 AWS CloudTrail，可在 CloudWatch Events 中查看所有服务的更改类API调用。
> 当某个事件与系统中创建的某条规则匹配时，我们可以自动调用一个 AWS Lambda 函数、将事件中继到 Amazon Kinesis 流、发送 Amazon SNS 主题通知，或调用一个内置工作流。

相关概念理解：metrics，periods，namespace，count，dimensions，statistics

- Metics: Metics（指标），表示一个发布到 CloudWatch 并且按时间排序的数据点集。

- Periods： Periods (时间段), 是与特定 Amazon CloudWatch 统计信息关联的时间的长度。每项统计信息代表在指定时间段内对收集的指标数据的聚合。时间段以秒为单位定义，时间段的有效值为 1、5、10、30 或 60 的任意倍数。

- namesapce  Namespaces(命名空间), 是CloudWatch Metrics(指标)的容器。不同命名空间中的指标彼此独立，因此来自不同应用程序的指标不会被错误地聚合到相同的统计信息中。

- Dimensions: Dimension(维度), 是一个名称/值对，它是指标标识的一部分。您可以为一个指标分配最多10个维度。

每个指标包含用于描述该指标的特定特征，您可以将维度理解为这些特征的类别。

- Statistics: Statistics(统计数据)是指定时间段内的指标数据聚合。CloudWatch 所提供的统计数据基于您的自定义数据或者其他 AWS 服务提供给 CloudWatch 的指标数据点。聚合通过使用命名空间、指标名称、维度以及数据点度量单位在您指定的时间段内完成。
