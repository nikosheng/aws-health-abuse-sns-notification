## AWS Abuse Report Notification

由于当前很多用户在海外发布媒体内容并没有注意到内容涉嫌违反知识产权的风险（例如比较常见的数字千年法案DMCA），因此会受到维权用户提起的投诉，由此客户会受到AWS官方发出的警告通知。但是由于警告通知通常会通过邮件发送到用户的账号注册邮箱，但是并没有时常去留言具体的内容。因此如果错过了在24小时内的违规内容下架并澄清，就会导致AWS官方进行封网的操作。

为了方便用户实施对于知识产权侵权风险的告警通知，可以使用本仓库的AWS CloudFormation 模版构建一个自动化的监控流程


## 步骤

#### CloudFormation 配置

点击 **Launch Stack** 启动AWS CloudFormation控制台，打开后需要选择对应的配置区域，本次实验在US-EAST-1 美国弗吉尼亚区域实施:
 
<a href="https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=AWSAbuseNotifier&templateURL=https://aws-nikofeng-sample-bucket.s3.amazonaws.com/github/AWS_Abuse_Notification.json" title="Launch Stack"><img src="images/cloudformation-launch-stack.png" alt="Launch Stack" /></a>

#### 填写配置项

- 打开**AWS CloudFormation**控制台后，保持默认选项点击下一步
- 在**参数**栏目下输入 

	```
	SNSTopicName: 可以自定义我们需要的SNS主题名字
	EmailAddress: 需要指定发送的邮箱地址
	MobilePhone: 需要指定发送的手机号码（带国家号）
	
	```
	点击下一步

- 在**配置堆栈选项**栏目下保持默认配置，点击下一步
- 勾选**我确认，AWS CloudFormation 可能创建 IAM 资源。**的单选框后，点击**创建堆栈**，等待CloudFormation堆栈创建完成

#### 确认AWS SNS 主题下的邮箱订阅

- 切换到AWS SNS 控制台，点击创建的主题**AWSAbuseNotifier**，可以看到当前邮箱终端节点在**等待确认**状态，需要登录邮箱确认订阅该SNS主题方可完成确认

