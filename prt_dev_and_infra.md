# Developer Tools & Infrastructure Management Services

## Developer Tools

- **Cloud9:** is an IDE within your browser that allows you to write and debug code in several popular programming languages.

- **CodeCommit:** is the AWS Source Control System for private Git repos. Like all other SCSs, you can commit, create branches, and merge your code. These options allow you to collaborate with other Developers. This service is free for five active users per month, after that, you pay per additional active user per month.

- **CodeBuild:** allows you to compile/build your application source code, run tests, and generate artifacts ready to be deployed, enabling *continuous integration* (CI). It is compatible with external Source Control Management (SCM) like GitHub or Bitbucket, and it's billed by minutes of execution when compiling/building. This service offers 100 free minutes per month.

- **CodeDeploy:** is a service that automates application deployments in the cloud or on-premises. With this service, you guarantee zero downtime in the applications when they are deployed.

- **CodePipeline:** is the service that automates the software release process that can integrate with CodeBuild to run builds and unit tests, with CodeCommit to retrieve the source code, and with CodeDeploy to deploy the changes.

- **X-Ray:** helps you **debug** and **analyze** applications in production, **maps** applications components, and view the **request** end to end.

- **CodeStar:** helps developers connect their environment to work collaboratively. This service integrates services like CodeCommit, CodeBuild, and CodeDeploy, and CodeStar contains an Issues tracking dashboard.

## Infrastructure Services

These services help you quickly deploy new applications, automate the management of your infrastructure, and provide real-time visibility into system health.

With *Infrastructure as Code* (IaC), you can write scripts to provision AWS resources, allowing you to supply resources in a reproducible manner saving time. AWS is compatible with *JSON* and *YAML* script languages.

- **CloudFormation:** is the service that allows you to provision AWS resources using IaC. **CloudFormation** lets you provide a repeatable process for provisioning resources. It is compatible with most AWS services and enables you to create templates for the resources you want to provision.

- **Elastic Beanstalk:** is an orchestration service used to deploy and scale your web applications. It automatically handles the deployment and monitors the health of the applications via **Health Dashboard**.

- **OpsWorks:** is a fully managed service you can use with *Chef* or *Puppet* to automate your server configuration and code deployment. This service allows you to manage On-premises servers or EC2 instances in AWS.
