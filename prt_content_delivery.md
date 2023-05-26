# Content Delivery Services (CDN)

A CDN is a geographically distributed group of servers that caches content close to end users to deliver this content quickly and efficiently with low latency.

## CloudFront

CloudFront is a CDN that delivers data and applications *globally*. Content can be made *available* or *restricted* based on location. This service *speeds up* the delivery of static and dynamic web content, and for that, it uses *edge location* to *cache* the content.

With *Edge Location*, CloudFront delivers the content immediately if it's there; otherwise, CloudFront retrieves the content from the origin and serves it to the client. You can think as origin, the original source of the content (S3 Bucket, EC2 Instance, etc..)

In the real world, you can use CloudFront with S3 most of time to deploy content globally, it is possible to use CloudFront to *stop* certain web *attacks*, like DDoS, and you can prevent users from certain countries from accessing content with something called *Geo-restriction*.

## Global Accelerator

Global Accelerator is a service that helps you improve the availability, performance, and security of your applications by providing global static public IPs that act as a fixed entry point to your application endpoints.

Global Accelerator is a single starting point for your app that routes your users through the AWS global network infrastructure when they access your content, regardless of what AZ distribution exists. It is able to re-route the traffic automatically to healthy available regional endpoints, improving the latency and availability of Single-Region apps that increase performance by 60%.

## S3 Transfer Acceleration

S3 Transfer Acceleration improves content uploads and downloads to and from S3 buckets using CloudFront's globally distributed edge locations, which increase file transfer over long distances.

With this service, customers around the world can upload to a central bucket.
