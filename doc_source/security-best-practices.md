# Security Best Practices for Elastic Beanstalk<a name="security-best-practices"></a>

AWS Elastic Beanstalk provides several security features to consider as you develop and implement your own security policies\. The following best practices are general guidelines and don’t represent a complete security solution\. Because these best practices might not be appropriate or sufficient for your environment, treat them as helpful considerations, not prescriptions\.

For other Elastic Beanstalk security topics, see [AWS Elastic Beanstalk Security](security.md)\.

## Preventive Security Best Practices<a name="security-best-practices.preventive"></a>

Preventive security controls attempt to prevent incidents before they occur\.

### Implement least privilege access<a name="security-best-practices.preventive.least-priv"></a>

Elastic Beanstalk provides AWS Identity and Access Management \(IAM\) managed policies for [instance profiles](iam-instanceprofile.md), [service roles](iam-servicerole.md), and [IAM users](AWSHowTo.iam.managed-policies.md)\. These managed policies specify all permissions that might be necessary for the correct operation of your environment and application\.

Your application might not require all the permissions in our managed policies\. You can customize them and grant only the permissions that are required for your environment's instances, the Elastic Beanstalk service, and your users to perform their tasks\. This is particularly relevant to user policies, where different user roles might have different permission needs\. Implementing least privilege access is fundamental in reducing security risk and the impact that could result from errors or malicious intent\.

### Update your platforms regularly<a name="security-best-practices.preventive.update"></a>

Elastic Beanstalk regularly releases new platform versions to update all of its platforms\. New platform versions provide operating system, runtime, application server, and web server updates, and updates to Elastic Beanstalk components\. Many of these platform updates include important security fixes\. Ensure that your Elastic Beanstalk environments are running on a supported platform version \(typically the latest version for your platform\)\. For details, see [Updating Your Elastic Beanstalk Environment's Platform Version](using-features.platform.upgrade.md)\.

The easiest way to keep your environment's platform up to date is to configure the environment to use [managed platform updates](environment-platform-update-managed.md)\.

## Detective Security Best Practices<a name="security-best-practices.detective"></a>

Detective security controls identify security violations after they have occurred\. They can help you detect a potential security threat or incident\.

### Implement monitoring<a name="security-best-practices.detective.monitor"></a>

Monitoring is an important part of maintaining the reliability, security, availability, and performance of your Elastic Beanstalk solutions\. AWS provides several tools and services to help you monitor your AWS services\.

The following are some examples of items to monitor:
+ *Amazon CloudWatch metrics for Elastic Beanstalk* – Set alarms for key Elastic Beanstalk metrics and for your application's custom metrics\. For details, see [Using Elastic Beanstalk with Amazon CloudWatch](AWSHowTo.cloudwatch.md)\.
+ *AWS CloudTrail entries* – Track actions that might impact availability, like `UpdateEnvironment` or `TerminateEnvironment`\. For details, see [Logging Elastic Beanstalk API Calls with AWS CloudTrail](AWSHowTo.cloudtrail.md)\.

### Enable AWS Config<a name="security-best-practices.detective.config"></a>

AWS Config provides a detailed view of the configuration of AWS resources in your account\. You can see how resources are related, get a history of configuration changes, and see how relationships and configurations change over time\.

You can use AWS Config to define rules that evaluate resource configurations for data compliance\. AWS Config rules represent the ideal configuration settings for your Elastic Beanstalk resources\. If a resource violates a rule and is flagged as *noncompliant*, AWS Config can alert you using an Amazon Simple Notification Service \(Amazon SNS\) topic\. For details, see [Finding and Tracking Elastic Beanstalk Resources with AWS Config](AWSHowTo.config.md)\.