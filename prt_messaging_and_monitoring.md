# Messaging and Monitoring Services

## Messaging and Integration Services

- **Simple Queue Service (SQS):** is a message queue service that allows you to build a **decoupled system**. *SQS* enables **component-to-component** communication using **messages** where the messages are **processed** **asynchronously**. With decoupled systems or applications, all components can send, store, and receive messages, which helps you improve performance and scalability. *SQS* is a **FIFO Queue**.

- **Simple Notification Service (SNS):** is a service that allows you to send emails and text messages from your applications. With *SNS*, you can publish messages on a topic, and subscribers can receive messages. A great example is when CloudWatch detects an anomaly in your infrastructure and sends an email (a plain text email).

- **Simple Email Service (SES):** is an email service that allows you to send richly formatted HTML emails. This service is ideal for marketing campaigns or professional emails. THIS IS THE ONLY MESSAGE SERVICE THAT SENDS RICHLY FORMATTED MESSAGES.

## Monitoring and Logging Services

Monitoring services are essential because they provide insight into system performance and help us proactively find and resolve errors.

- **CloudWatch:** is a collection of services that help us monitor and observe our cloud resources. We may collect **metrics** and **events** and may also **visualize logs**. In addition, we can detect **anomalies** in our environment and set **alarms** that, through *SNS*, send notifications about the problem.

    | CloudWatch Alarms | CloudWatch Logs | CloudWatch Metrics | CloudWatch Events |
    |-------------------|-----------------|--------------------|-------------------|
    | Allows us to set high-resolution **alarms**. For example, Billing alarms. | Allows us to **Monitor** applications logs and performance data for AWS services, like EC2, Lambda, etc. | Allows us to **visualize** time-series data. For example, the CPU usage of an EC2 instance. | Allows us to take automated action and troubleshoot issues. So we can **trigger an event** based on a condition. |

- **CloudTrail:** tracks user activity and API calls within your AWS account. It is possible to log and retain account activity, track activity through the console, SDKs and CLI, identify which user made changes, and detect unusual activity in our account. With CloudTrail, we can track the username, event time and name, IP address, access key, region, and error code, in case we have one.
