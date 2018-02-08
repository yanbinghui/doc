

# AWS的产品分析

1. [CloudWatch](https://aws.amazon.com/cn/cloudwatch/details/)

 Amazon CloudWatch 是一项针对 AWS 云资源和在 AWS 上运行的应用程序进行监控的服务。您可以使用 Amazon CloudWatch 收集和跟踪各项指标、收集和监控日志文件、设置警报以及自动应对 AWS 资源的更改。Amazon CloudWatch 可以监控各种 AWS 资源，例如 Amazon EC2 实例、Amazon DynamoDB 表、Amazon RDS 数据库实例、应用程序和服务生成的自定义指标以及应用程序生成的所有日志文件。您可通过使用 Amazon CloudWatch 全面地了解资源使用率、应用程序性能和运行状况。使用这些分析结果，您可以及时做出反应，保证应用程序顺畅运行。
 
 CloudWatch有点像阿里云的云监控
 
2. [AWS X-Ray](https://aws.amazon.com/cn/xray/)

 AWS X-Ray 可以帮助开发人员分析与调试分布式生产应用程序，例如使用微服务架构构建的应用程序。借助 X-Ray，您可以了解应用程序及其底层服务的执行方式，从而识别导致性能问题和错误的根本原因并将其排除。X-Ray 可在请求通过应用程序时提供请求的端到端视图，并展示应用程序底层组件的映射。您可以使用 X-Ray 分析开发和生产中的应用程序，从简单的三层应用程序到包含上千种服务的复杂微服务应用程序。
 
 类似集团内部的EagleEye
 
3. [AWS CloudTrail](https://aws.amazon.com/cloudtrail/?nc2=h_m1)

 跟踪用户活动和 API 使用情况

 AWS CloudTrail 是一项服务，支持对您 AWS 账户进行监管、合规性检查、操作审核和风险审核。借助 CloudTrail，您可以记录日志、持续监控并保留与整个 AWS 基础设施中的操作相关的账户活动。CloudTrail 提供 AWS 账户活动的事件历史记录，这些活动包括通过 AWS 管理控制台、AWS 开发工具包、命令行工具和其他 AWS 服务执行的操作。这一事件历史记录可以简化安全性分析、资源更改跟踪和故障排除工作。
