# AWS CouldWatch

## Practice

- 创建cloudwatch event rules，每分钟自动触发Lambda（Lambda功能需要自己实现，向cloudwatch metrics里push自定义的metrics），设置alarm检测task中定义的metric，自定义并监控条件使alarm触发阈值，alarm出发SNS，SNS发告警到邮箱。

- 创建cloudwatch event rules，每分钟自动触发Lambda（输出固定格式的log message）。为lambda log创建metric filter，匹配log message，创建新的metric，自定义并监控条件使alarm触发阈值，alarm出发SNS，SNS发告警到邮箱。

## Output

- 两个cloudformation文件
- 部署cloudformation后，功能完整，邮箱可以收到报警
