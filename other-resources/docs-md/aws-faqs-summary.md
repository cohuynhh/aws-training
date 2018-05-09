<a id="top" />

# AWS FAQs

## Content
* [FAQs ACM (Amazon Certificate Manager)](#acm)
* [FAQs Cognito](#cognito)
* [FAQs WorkSpaces](#workspaces)
* [FAQs DynamoDB](#dynamodb)
* [FAQs IAM](#iam)
* [FAQs API GW](#api-gw)
* [FAQs SES](#ses)
* [FAQs CloudFormation](#cfn)

<a id="acm" />

## FAQs ACM (Amazon Certificate Manager)
<p align="right"><a href="#top">Top</a></p>

* To use an ACM certificate with Amazon CloudFront, you must request the certificate in the US East (N. Virginia) region. ACM certificates in this region that are associated with a CloudFront distribution are distributed to all the geographic locations configured for that distribution.
* **Can I use certificates on Amazon EC2 instances or on my own servers?**  
  No.
* **Does ACM support checking of DNS Certificate Authority Authorization (CAA) records?**  
  Yes. DNS Certificate Authority Authorization (CAA) records allow domain owners to specify which certificate authorities are authorized to issue certificates for their domain. When you request an ACM Certificate, AWS Certificate Manager looks for a CAA record in the DNS zone configuration for your domain. If a CAA record is not present, then Amazon can issue a certificate for your domain. Most customers fall into this category. If your DNS configuration contains a CAA record, that record must specify one of the following CAs before Amazon can issue a certificate for your domain: amazon.com, amazontrust.com,
* **Q: Does ACM support checking of DNS Certificate Authority Authorization (CAA) records?**  
  Yes. DNS Certificate Authority Authorization (CAA) records allow domain owners to specify which certificate authorities are authorized to issue certificates for their domain. When you request an ACM Certificate, AWS Certificate Manager looks for a CAA record in the DNS zone configuration for your domain. If a CAA record is not present, then Amazon can issue a certificate for your domain. Most customers fall into this category. If your DNS configuration contains a CAA record, that record must specify one of the following CAs before Amazon can issue a certificate for your domain: amazon.com, amazontrust.com, awstrust.com, or amazonaws.com.
* **Q. Why does ACM use CNAME records for DNS validation instead of TXT records?**  
  Using a CNAME record allows ACM to renew certificates for as long as the CNAME record exists. The CNAME record directs to a TXT record in an AWS domain (acm-validations.aws) that ACM can update as needed to validate or re-validate a domain name, without any action from you.
* **Q: Does ACM provide Organizational Validation (OV) or Extended Validation (EV) certificates?**  
  Not at this time. Q: Does ACM provide certificates for anything other than SSL/TLS for websites? Not at this time. Q: Can I use certificates provided by ACM for code signing or email encryption? No.
* **Q: How do I revoke a certificate?**  
  You can request ACM to revoke a certificate by visiting the AWS Support Center and creating a case.
* ACM certificates are only copied across Regions if the certificate is associated with a CloudFront distribution. In that case, CloudFront distributes the ACM certificate to the geographic locations configured for your distribution.
* **Q: Can I audit the use of certificate private keys?**  
  Yes. Using AWS CloudTrail you can review logs that tell you when the private key for the certificate was used.
* **Q: What is the validity period for certificates provided by ACM?**  
  Certificates provided by ACM are currently valid for 13 months.
* **Q: Does ACM allow local language characters in domain names, otherwise known as Internationalized Domain Names (IDNs)?**  
  ACM does not allow Unicode encoded local language characters; however, ACM allows ASCII-encoded local language characters for domain names.
* **Q: Will I be notified before my certificate is renewed and the new certificate is deployed?**  
  No. ACM may renew or rekey the certificate and replace the old one without prior notice.
* **Q: Does my site drop existing connections when ACM deploys the renewed certificate?**  
  No, connections established after the new certificate is deployed use the new certificate, and existing connections are not affected.

<a id="cognito" />

## FAQs Cognito
<p align="right"><a href="#top">Top</a></p>

* Cognito Identity also enables you to customize workflows by, for example, adding app-specific logic to user registration for fraud detection and user validation through AWS Lambda.
* **Q: Can I have my own identity provider to support user sign-up and sign-in?**  
  Yes, you can easily and securely add sign-up and sign-in functionality to your apps with Cognito Identity. Your users can sign-up and sign-in using email, phone number, or user name. You can also implement enhanced security features, such as email verification, phone number verification, and multi-factor authentication. Cognito Identity also enables you to customize workflows by, for example, adding app-specific logic to user registration for fraud detection and user validation through AWS Lambda. To learn more, visit our docs.
* **Q: Do I still need my own backend authentication systems with Cognito Identity?**  
  No. Cognito Identity supports login through Amazon, Facebook, Twitter, Digits, and Google, as well as providing support for unauthenticated users. With Cognito Identity you can support federated authentication, profile data sync store and AWS access token distribution without writing any backend code.
* **Q: Does Cognito Identity support separate identities for different users on the same device?**  
  Yes. Cognito Identity supports separate identities on a single device, such as a family iPad. Each identity is treated separately and you have complete control over how your app logs users in and out and how local and remote app data is stored.
* **Q: How much does Cognito Identity cost?**  
  With Amazon Cognito, you pay only for what you use. There are no minimum fees and no upfront commitments. If you are using the Cognito Identity to create a User Pool, you pay based on your monthly active users (MAUs) only. A user is counted as a MAU if within a calendar month there is an identity operation related to that user, such as sign-up, sign-in, token refresh, and password change. You are not charged for subsequent sessions or for inactive users with in that calendar month. Separate charges apply for optional use of SMS messaging as described below. The Your User Pool feature has a free tier of 50,000 MAUs each month. The Cognito Identity free tier does not expire at the end of your 12 month AWS Free Tier term, and it is available to both existing and new AWS customers indefinitely Federated Identities and secure access control for AWS resources are always free with Cognito Identity.
* **Q: Does every write or read from the app count as a sync operation?**  
  No. You decide when to call the synchronize() method. Every write or read from the device is to the local SQlite store. This way you are in complete control of your costs.
* **Q: Is data saved directly to the Amazon Cognito sync store?**  
  No. The optional AWS Mobile SDK saves your data to an SQLite database on the local device, this way the data is always accessible to your app. The data is pushed to the Amazon Cognito sync store by calling the synchronize() method and, if push synchronization is enabled, all other devices linked to an identity are notified of the data change in the sync store via Amazon SNS.

<a id="workspaces" />

## FAQs WorkSpaces
<p align="right"><a href="#top">Top</a></p>

* **Q: Can I migrate users from an Amazon WorkSpaces Windows 7 bundle to a Windows 10 bundle?**  
  No. To offer existing users a Windows 10 desktop experience, you need to delete their existing Amazon WorkSpace and create a new one using a Windows 10 WorkSpaces bundle. To migrate data and documents, we recommend that you use the sync feature available with Amazon WorkDocs. Note that Amazon WorkDocs comes with 50GB of free storage for every Amazon WorkSpace.
* **Q: What does a user need to use an Amazon Workspace?**  
  A user needs to have an Amazon WorkSpace provisioned for them, and a broadband Internet connection. To use an Amazon WorkSpaces client application to access their WorkSpace, they will need a supported client device (PC, Mac, iPad, Kindle Fire, or Android tablet), and an Internet connection with TCP ports 443 & 4172, and UDP port 4172 open.
* **Q: If I am located a significant distance from the region where my Amazon WorkSpace is located, will I have a good user experience?**  
  If you are located more than 2000 miles from the regions where Amazon WorkSpaces is currently available, you can still use the service, but your experience may be less responsive. The easiest way to check performance is to use the Amazon WorkSpaces Connection Health Check Website. You can also refer to the Regional Products and Services page for details of Amazon WorkSpaces service availability by region.
* **Q: Will encryption impact the launch time of an Amazon WorkSpace?**  
  The launch time of a WorkSpace that only requires user volume encryption are similar to those of an unencrypted WorkSpace. The launch time of a WorkSpace that requires root volume encrypt will take several more minutes.
* **Q: What is the Amazon WorkDocs sync client?**  
  The Amazon WorkDocs sync client is a client application that you can install on your Amazon WorkSpace, which continuously, automatically, and securely syncs documents from your Amazon WorkSpace to your Amazon WorkDocs location. You can also install the Amazon WorkDocs sync client on a Mac or PC to sync documents across all desktops they may be using. When an Amazon WorkSpace is launched, users will have a link on their desktop so that they can install the Amazon WorkDocs sync client. The client can be downloaded here
* **Q: How do I upload my applications to Amazon WAM?**  
  You can package your applications using the Amazon WAM Studio, validate using the Amazon WAM Player, and then upload your applications to Amazon WAM. For more information, see the Amazon WAM User Guide on packaging and validating.
* **Q: Can I use any other client (e.g., an RDP client) with Amazon WorkSpaces?**  
  No. You can use any of the free clients provided by AWS,
* **Q: Can I use PCoIP Zero Clients with Amazon WorkSpaces?**  
  Yes, Amazon WorkSpaces supports PCoIP Zero Client devices that have the Teradici Tera2 chipset. For a complete list of Zero Clients that are compatible with Amazon WorkSpaces please visit the device finder here (site hosted by Teradici).
* **Q: Can I use the built in microphone and speakers for making audio calls?**  
  Yes.
* **Q: Which web browsers can I use to access Amazon WorkSpaces Web Access?**  
  Amazon WorkSpaces Web Access works with Google Chrome version 53 and higher, and Firefox version 49 and higher, running on Windows, Mac, or Linux. Mobile versions of Chrome and Firefox are not currently supported.
* **Q: What languages are supported by Amazon WorkSpaces?**  
  Amazon WorkSpaces bundles that provide the Windows 7 and Windows 10 desktop experience currently support English (US) and Japanese. You can also download and install language packs for Windows directly from Microsoft. For more information, visit this page. Amazon WorkSpaces client applications currently support English (US), German, Chinese (Simplified), Japanese, French Canadian, Korean, and Portuguese.
* **Q: Can I provide more than one Amazon Workspace per user?**  
  No. You can currently only provide one WorkSpace for each user.
* **Q: What is the network bandwidth that I need to use my Amazon WorkSpace?**  
  The bandwidth needed to use your WorkSpace depends on what you're doing on your WorkSpace. For general office productivity use, we recommend that a bandwidth download speed of between 300Kbps up and 1Mbps. For graphics intensive work we recommend bandwidth download speeds of 3Mbps.
* **Q: What is the maximum network latency recommended while accessing a Workspace?**  
  While the remoting protocol has a maximum round trip latency recommendation of 250 ms, the best user experience will be achieved at less than 100 ms.
* **Q: What does the Amazon WorkSpaces Application Manager (Amazon WAM) cost?**  
  Amazon WAM is available in two versions - lite or standard. The Amazon WAM lite subscription is available at no charge, and the Amazon WAM standard subscription costs $5/user/month. You can learn more about Amazon WAM here.
* **Q: What is included with the Amazon WorkSpaces Free Tier?**  
  The WorkSpaces Free Tier includes two Standard bundle Amazon WorkSpaces, for 40 hours of combined use per month, for two calendar months. As with all bundles, your WorkSpace comes with Internet Explorer 11, Mozilla Firefox, and 7-Zip pre-installed, and access to Amazon WorkDocs with 50 GB included storage.
* Understanding Your Usage with Billing Reports.
* **Q: Can I connect Amazon WorkSpaces to my VPC?**  
  Yes. The first time you connect to the WorkSpaces Management Console, you can choose an easy ‘getting started’ link that will create a new VPC and two associated subnets for you as well as an Internet Gateway and a directory to contain your users. If you choose to access the console directly, you can choose which of your VPCs your WorkSpaces will connect to. If you have a VPC with a VPN connection back to your on-premises network, then your WorkSpaces will be able to communicate with your on-premises network (you retain the usual control you have over network access within your VPC using all of the normal configuration options such as security groups, network ACLS, and routing tables).
* **Q: Will I be able to monitor how many hours my Amazon WorkSpaces have been running?**  
  Yes, you will be able to monitor the total number hours your Amazon WorkSpaces has been running in a given period of time through Amazon CloudWatch “UserConnected” metric.
* **Q: Can I print from my tablet or Chromebook?**  
  The Amazon WorkSpaces clients for tablets and Chromebook support cloud printing services including, but not limited to, Cortado ThinPrint® and Google Cloud Print. Local and network printing are not currently supported.

<a id="dynamodb" />

## FAQs DynamoDB
<p align="right"><a href="#top">Top</a></p>

* Based on what we see in typical database workloads, we believe that the total bill for using SSD-based DynamoDB will usually be lower than the cost of using a typical spinning media-based relational or nonrelational database. If you need to store a large amount of data that you rarely access, DynamoDB may not be right for you. We recommend that you use Amazon S3 for such use cases. You also should note that the storage cost reflects the cost of storing multiple copies of each data item across multiple facilities in an AWS Region.
* **Q: How does Amazon DynamoDB differ from Amazon SimpleDB?**  
  Which should I use? Both services are non-relational databases that remove the work of database administration. Amazon DynamoDB focuses on providing seamless scalability and fast, predictable performance. It runs on solid state disks (SSDs) for low-latency response times, and there are no limits on the request capacity or storage size for a given table. This is because Amazon DynamoDB automatically partitions your data and workload over a sufficient number of servers to meet the scale requirements you provide. In contrast, a table in Amazon SimpleDB has a strict storage limitation of 10 GB and is limited in the request capacity it can achieve (typically under 25 writes/second); it is up to you to manage the partitioning and re-partitioning of your data over additional SimpleDB tables if you need additional scale. While SimpleDB has scaling limitations, it may be a good fit for smaller workloads that require query flexibility. Amazon SimpleDB automatically indexes all item attributes and thus supports query flexibility at the cost of performance and scale. Amazon CTO Werner Vogels' DynamoDB blog post provides additional context on the evolution of non-relational database technology at Amazon.
* **Q: How does Amazon DynamoDB differ from Amazon SimpleDB?**  
  Which should I use? Both services are non-relational databases that remove the work of database administration. Amazon DynamoDB focuses on providing seamless scalability and fast, predictable performance. It runs on solid state disks (SSDs) for low-latency response times, and there are no limits on the request capacity or storage size for a given table. This is because Amazon DynamoDB automatically partitions your data and workload over a sufficient number of servers to meet the scale requirements you provide. In contrast, a table in Amazon SimpleDB has a strict storage limitation of 10 GB and is limited in the request capacity it can achieve (typically under 25 writes/second); it is up to you to manage the partitioning and re-partitioning of your data over additional SimpleDB tables if you need additional scale. While SimpleDB has scaling limitations, it may be a good fit for smaller workloads that require query flexibility. Amazon SimpleDB automatically indexes all item attributes and thus supports query flexibility at the cost of performance and scale. Amazon CTO Werner Vogels' DynamoDB blog post provides additional context on the evolution of non-relational database technology at Amazon.
* **Q: Is there a limit on the number of attributes an item can have?**  
  There is no limit to the number of attributes that an item can have. However, the total size of an item, including attribute names and attribute values, cannot exceed 400KB.
* If you wish to exceed throughput rates of 10,000 writes/second or 10,000 reads/second, you must first contact Amazon through this online form
* **Q. Can I force an Auto Scaling policy to scale up to maximum capacity or scale down to minimum capacity instantly?**  
  No, scaling up instantly to maximum capacity or scaling down to minimum capacity is not supported. Instead, you can temporarily disable Auto Scaling, set desired capacity you need manually for required duration, and re-enable Auto Scaling later.
* **Q. Where can I monitor the scaling actions triggered by Auto Scaling?**  
  You can monitor status of scaling actions triggered by Auto Scaling under the 'Capacity' tab in the management console and from CloudWatch graphs under the 'Metrics' tab.
* **Q: What are global secondary indexes?**  
  Global secondary indexes are indexes that contain a partition or partition-and-sort keys that can be different from the table's primary key. For efficient access to data in a table, Amazon DynamoDB creates and maintains indexes for the primary key attributes. This allows applications to quickly retrieve data by specifying primary key values. However, many applications might benefit from having one or more secondary (or alternate) keys available to allow efficient access to data with attributes other than the primary key. To address this, you can create one or more secondary indexes on a table, and issue Query requests against these indexes. Amazon DynamoDB supports two types of secondary indexes: Local secondary index — an index that has the same partition key as the table, but a different sort key. A local secondary index is "local" in the sense that every partition of a local secondary index is scoped to a table partition that has the same partition key. Global secondary index — an index with a partition or a partition-and-sort key that can be different from those on the table. A global secondary index is considered "global" because queries on the index can span all items in a table, across all partitions. Secondary indexes are automatically maintained by Amazon DynamoDB as sparse objects. Items will only appear in an index if they exist in the table on which the index is defined. This makes queries against an index very efficient, because the number of items in the index will often be significantly less than the number of items in the table. Global secondary indexes support non-unique attributes, which increases query flexibility by enabling queries against any non-key attribute in the table. Consider a gaming application that stores the information of its players in a DynamoDB table whose primary key consists of UserId (partition) and GameTitle (sort). Items have attributes named TopScore, Timestamp, ZipCode, and others. Upon table creation, DynamoDB provides an implicit index (primary index) on the primary key that can support efficient queries that return a specific user’s top scores for all games. However, if the application requires top scores of users for a particular game, using this primary index would be inefficient, and would require scanning through the entire table. Instead, a global secondary index with GameTitle as the partition key element and TopScore as the sort key element would enable the application to rapidly retrieve top scores for a game. A GSI does not need to have a sort key element. For instance, you could have a GSI with a key that only has a partition element GameTitle. In the example below, the GSI has no projected attributes, so it will just return all items (identified by primary key) that have an attribute matching the GameTitle you are querying on.
* **Q: Does the local version of DynamoDB support global secondary indexes?**  
  Yes. The local version of DynamoDB is useful for developing and testing DynamoDB-backed applications. You can download the local version of DynamoDB here
* **Q: How does adding a global secondary index impact provisioned throughput and storage for a table?**  
  Similar to a DynamoDB table, a GSI consumes provisioned throughput when reads or writes are performed to it. A write that adds or updates a GSI item will consume write capacity units based on the size of the update. The capacity consumed by the GSI write is in addition to that needed for updating the item in the table. Note that if you add, delete, or update an item in a DynamoDB table, and if this does not result in a change to a GSI, then the GSI will not consume any write capacity units. This happens when an item without any GSI key attributes is added to the DynamoDB table, or an item is updated without changing any GSI key or projected attributes. A query to a GSI consumes read capacity units, based on the size of the items examined by the query. Storage costs for a GSI are based on the total number of bytes stored in that GSI. This includes the GSI key and projected attributes and values, and an overhead of 100 bytes for indexing purposes. Q: Can DynamoDB throttle my application writes to a table because of a GSI’s provisioned throughput? Because some or all writes to a DynamoDB table result in writes to related GSIs, it is possible that a GSI’s provisioned throughput can be exhausted. In such a scenario, subsequent writes to the table will be throttled. This can occur even if the table has available write capacity units. Q: How often can I change provisioned throughput at the index level?
* **Q: Can DynamoDB throttle my application writes to a table because of a GSI’s provisioned throughput?**  
  Because some or all writes to a DynamoDB table result in writes to related GSIs, it is possible that a GSI’s provisioned throughput can be exhausted. In such a scenario, subsequent writes to the table will be throttled. This can occur even if the table has available write capacity units.
* **Q: How does adding a global secondary index impact provisioned throughput and storage for a table?**  
   Similar to a DynamoDB table, a GSI consumes provisioned throughput when reads or writes are performed to it. A write that adds or updates a GSI item will consume write capacity units based on the size of the update. The capacity consumed by the GSI write is in addition to that needed for updating the item in the table. Note that if you add, delete, or update an item in a DynamoDB table, and if this does not result in a change to a GSI, then the GSI will not consume any write capacity units. This happens when an item without any GSI key attributes is added to the DynamoDB table, or an item is updated without changing any GSI key or projected attributes. A query to a GSI consumes read capacity units, based on the size of the items examined by the query. Storage costs for a GSI are based on the total number of bytes stored in that GSI. This includes the GSI key and projected attributes and values, and an overhead of 100 bytes for indexing purposes.
* **Q: How do I query local secondary indexes?**  
  Local secondary indexes can only be queried via the Query API. To query a local secondary index, explicitly reference the index in addition to the name of the table you’d like to query. You must specify the index partition attribute name and value. You can optionally specify a condition against the index key sort attribute. Your query can retrieve non-projected attributes stored in the primary index by performing a table fetch operation, with a cost of additional read capacity units. Both strongly consistent and eventually consistent reads are supported for query using local secondary index.
* **Q: Are there limits on the size of an item collection?**  
  Every item collection in Amazon DynamoDB is subject to a maximum size limit of 10 gigabytes. For any distinct partition key value, the sum of the item sizes in the table plus the sum of the item sizes across all of that table's local secondary indexes must not exceed 10 GB. The 10 GB limit for item collections does not apply to tables without local secondary indexes; only tables that have one or more local secondary indexes are affected. Although individual item collections are limited in size, the storage size of an overall table with local secondary indexes is not limited. The total size of an indexed table in Amazon DynamoDB is effectively unlimited, provided the total storage size (table and indexes) for any one partition key value does not exceed the 10 GB threshold.
* **Q: How much does DynamoDB FGAC cost?**  
  There is no additional charge for using FGAC. As always, you only pay for the provisioned throughput and storage associated with the DynamoDB table. Q: How do I get started? Refer to the Fine-Grained Access Control section of the DynamoDB Developer Guide to learn how to create an access policy, create an IAM role for your app (e.g. a role named AcmeFacebookUsers for a Facebook app_id of 34567), and assign your access policy to the role. The trust policy of the role determines which identity providers are accepted (e.g. Login with Amazon, Facebook, or Google), and the access policy describes which AWS resources can be accessed (e.g. a DynamoDB table). Using the role, your app can now to obtain temporary credentials for DynamoDB by calling the AssumeRoleWithIdentityRequest API of the AWS Security Token Service (STS).
* **Q: Can I grant access based on a canonical user id instead of separate ids for the user based on the identity provider they logged in with?**  
  Not without running a “token vending machine”. If a user retrieves federated access to your IAM role directly using Facebook credentials with STS, those temporary credentials only have information about that user’s Facebook login, and not their Amazon login, or Google login. If you want to internally store a mapping of each of these logins to your own stable identifier, you can run a service that the user contacts to log in, and then call STS and provide them with credentials scoped to whatever partition key value you come up with as their canonical user
* **Q: Do your prices include taxes?**  
  For details on taxes, see Amazon Web Services Tax Help
* **Q: What is the maximum throughput I can provision for a single DynamoDB table?**  
  DynamoDB is designed to scale without limits However, if you wish to exceed throughput rates of 10,000 write capacity units or 10,000 read capacity units for an individual table, you must first contact Amazon through this online form. If you wish to provision more than 20,000 write capacity units or 20,000 read capacity units from a single subscriber account you must first contact us using the form described above.
* **Q: How do I know if I am exceeding my provisioned throughput capacity?**  
  DynamoDB publishes your consumed throughput capacity as a CloudWatch metric. You can set an alarm on this metric so that you will be notified if you get close to your provisioned capacity.
* **Q. How can I set up single master cross-region replication for a table?**  
  You can create cross-region replicas using the DynamoDB Cross-region Replication library.
* **Q: Does DynamoDB Streams display all updates made to my DynamoDB table in order?**  
  Changes made to any individual item will appear in the correct order. Changes made to different items may appear in DynamoDB Streams in a different order than they were received.
* **Q: Can I use my Kinesis Client Library to access DynamoDB Streams?**  
  Yes, developers who are familiar with Kinesis APIs will be able to consume DynamoDB Streams easily. You can use the DynamoDB Streams Adapter, which implements the Amazon Kinesis interface, to allow your application to use the Amazon Kinesis Client Libraries (KCL) to access DynamoDB Streams. For more information about using the KCL to access DynamoDB Streams, please see our documentation
* **Q: What is the Amazon DynamoDB Logstash Plugin for Elasticsearch?**  
  Elasticsearch is a popular open source search and analytics engine designed to simplify real-time search and big data analytics. Logstash is an open source data pipeline that works together with Elasticsearch to help you process logs and other event data. The Amazon DynamoDB Logstash Plugin make is easy to integrate DynamoDB tables with Elasticsearch clusters.
* **Q: Is the DynamoDB Storage Backend for Titan a fully managed service?**  
  No. The DynamoDB storage backend for Titan manages the storage layer for your Titan workload. However, the plugin does not do provisioning and managing of the client side. For simple provisioning of Titan we have developed a CloudFormation template that sets up DynamoDB Storage Backend for Titan with Gremlin Server; see the instructions available here
* **Q: How can I use tags for cost allocation?**  
  You can use cost allocation tags to categorize and track your AWS costs. AWS Cost Explorer and detailed billing reports support the ability to break down AWS costs by tag. Typically, customers use business tags such as cost center/business unit, customer, or project to associate AWS costs with traditional cost-allocation dimensions. However, a cost allocation report can include any tag. This enables you to easily associate costs with technical or security dimensions, such as specific applications, environments, or compliance programs.
* **Q: How many tags can I add to single DynamoDB table?**  
  You can add up to 50 tags to a single DynamoDB table. Tags with the prefix “aws:” cannot be manually created and do not count against your tags per resource limit.
* **Q. Can I encrypt DynamoDB Streams?**  
  Currently, you cannot enable encryption at rest for DynamoDB Streams. If encryption at rest is a compliance/regulatory requirement, we recommend turning off DynamoDB Streams for encrypted tables.
* For more information, see How Envelope Encryption Works with Supported AWS Service
* **Q. Can I use different service default keys for different tables?**  
  No, DynamoDB uses a single service default key for encrypting all of your DynamoDB tables.

<a id="iam" />

## FAQs IAM
<p align="right"><a href="#top">Top</a></p>

* **Q: Can IAM users have individual EC2 SSH keys?**  
  Not in the initial release. IAM does not affect EC2 SSH keys or Windows RDP certificates. This means that although each user has separate credentials for accessing web service APIs, they must share SSH keys that are common across the AWS account under which users have been defined.
* **Q: Where can I use my SSH keys?**  
  Currently, IAM users can use their SSH keys only with AWS CodeCommit to access their repositories.
* **Q: How do I assume an IAM role?**  
  You assume an IAM role by calling the AWS Security Token Service (STS) AssumeRole APIs (in other words, AssumeRole, AssumeRoleWithWebIdentity, and AssumeRoleWithSAML). These APIs return a set of temporary security credentials that applications can then use to sign requests to AWS service APIs.
* **Q: How can I easily remove unnecessary permissions?**  
  To help you determine which permissions are needed, the IAM console now displays service last accessed data that shows the hour when an IAM entity (a user, group, or role) last accessed an AWS service. Knowing if and when an IAM entity last exercised a permission can help you remove unnecessary permissions and tighten your IAM policies with less effort.
* You can also use the policy simulator to understand how IAM policies and resource-based policies work together to grant or deny access to AWS resources.
* **Q: How can I request temporary security credentials for federated users?**  
  You can call the GetFederationToken, AssumeRole, AssumeRoleWithSAML, or AssumeRoleWithWebIdentity STS APIs.
* **Q: Can a temporary security credential be revoked prior to its expiration?**  
  No. When requesting temporary credentials, we recommend the following: When creating temporary security credentials, set the expiration to a value that is appropriate for your application. Because root account permissions cannot be restricted, use an IAM user and not the root account for creating temporary security credentials. You can revoke permissions of the IAM user that issued the original call to request it. This action almost immediately revokes privileges for all temporary security credentials issued by that IAM user
* **Q: Can federated users access AWS APIs?**  
  Yes. You can programmatically request temporary security credentials for your federated users to provide them secure and direct access to AWS APIs. We have provided a sample application that demonstrates how you can enable identity federation, providing users maintained by Microsoft Active Directory access to AWS service APIs. For more information, see Using Temporary Security Credentials to Request Access to AWS Resources.
* **Q: Can federated users access the AWS Management Console?**  
  Yes. There are a couple ways to achieve this. One way is by programmatically requesting temporary security credentials (such as GetFederationToken or AssumeRole) for your federated users and including those credentials as part of the sign-in request to the AWS Management Console. After you have authenticated a user and granted them temporary security credentials, you generate a sign-in token that is used by the AWS single sign-on (SSO) endpoint. The user’s actions in the console are limited to the access control policy associated with the temporary security credentials. For more details, see Creating a URL that Enables Federated Users to Access the AWS Management Console (Custom Federation Broker). Alternatively, you can post a SAML assertion directly to AWS sign-in (https://signin.aws.amazon.com/saml). The user’s actions in the console are limited to the access control policy associated with the IAM role that is assumed using the SAML assertion. For more details, see Enabling SAML 2.0 Federated Users to Access the AWS Management Console. Using either approach allows a federated user to access the console without having to sign in with a user name and password. We have provided a sample application that demonstrates how you can enable identity federation, providing users maintained by Microsoft Active Directory access to the AWS Management Console.
* **Q: What is web identity federation?**  
  Web identity federation allows you to create AWS-powered mobile apps that use public identity providers (such as Amazon Cognito, Login with Amazon, Facebook, Google, or any OpenID Connect-compatible provider) for authentication. With web identity federation, you have an easy way to integrate sign-in from public identity providers (IdPs) into your apps without having to write any server-side code and without distributing long-term AWS security credentials with the app. For more information about web identity federation and to get started, see About Web Identity Federation.
* **Q: Are there any default quota limits associated with IAM?**  
  Yes, by default your AWS account has initial quotas set for all IAM-related entities. For details see Limitations on IAM Entities and Objects. These quotas are subject to change. If you require an increase, you can access the Service Limit Increase form via the Contact Us page, and choose IAM Groups and Users from the Limit Type drop-down list.
* if you want to use a physical authentication device then you will need to purchase an authentication device that is compatible with AWS MFA from Gemalto, a third party provider. For more details, please visit Gemalto’s website.
* If your MFA device is lost, damaged, stolen, or not working, you can sign in using alternative factors of authentication, deactivate the MFA device, and activate a new device. As a security best practice, we recommend that you change your root account's password.
* **Q. Which services does MFA-protected API access work with?**  
  MFA-protected API access is supported by all AWS services that support temporary security credentials. For a list of supported services, see AWS Services that Work with IAM and review the column labeled Supports temporary security credentials.
* **Q. Does MFA-protected API access control API access for AWS root accounts?**  
  No, MFA-protected API access only controls access for IAM users. Root accounts are not bound by IAM policies, which is why we recommend that you create IAM users to interact with AWS service APIs rather than
* **Q. Does MFA-protected API access control API access for AWS root accounts?**  
  No, MFA-protected API access only controls access for IAM users. Root accounts are not bound by IAM policies, which is why we recommend that you create IAM users to interact with AWS service APIs rather than use AWS root account credentials.
* **Q. How does MFA-protected API access interact with existing MFA use cases such as S3 MFA Delete?**  
  MFA-protected API access and S3 MFA Delete do not interact with each other. S3 MFA Delete currently does not support temporary security credentials. Instead, calls to the S3 MFA Delete API must be made using long-term access keys.
* **Q. Does MFA-protected API access work for federated users?**  
  Customers cannot use MFA-protected API access to control access for federated users. The GetFederatedSession API does not accept MFA parameters. Since federated users can’t authenticate with AWS MFA devices, they are unable to access resources designated using MFA-protected API access.

<a id="api-gw" />

## FAQs API GW
<p align="right"><a href="#top">Top</a></p>

* **Q: What is an usage plan?**  
  Usage plans help you declare plans for third-party developers that restrict access only to certain APIs, define throttling and request quota limits, and associate them with API keys. You can also extract utilization data on an per-API key basis to analyze API usage and generate billing documents. For example, you can create a basic, professional, and enterprise plans – you can configure the basic usage plan to only allow 1,000 requests per day and a maximum of 5 requests per second (RPS).
* **Q: What if I mistakenly deployed to a stage?**  
  Amazon API Gateway saves the history of your deployments. At any point, using the Amazon API Gateway APIs or the console, you can roll back a stage to a previous deployment.
* **Q: How do I monetize my APIs on API Gateway?**  
  You can monetize your APIs on API Gateway by publishing them as products in AWS Marketplace. You will first need to register as a seller in AWS Marketplace, and submit your usage plans on API Gateway as products. Read here to learn more about API Monetization.
* **Q: How does AWS Signature Version 4 work?**  
  You can use AWS credentials -- access and secret keys – to sign requests to your service and authorize access like other AWS services. The signing of an Amazon API Gateway API request is managed by the custom API Gateway SDK generated for your service. You can retrieve temporary credentials associated with a role in your AWS account using Amazon Cognito.
* **Q: What is a custom authorizer?**  
  Custom authorizers are AWS Lambda functions. With custom request authorizers, you will be able to authorize access to APIs using a bearer token auth strategy such as OAuth. When an API is called, API Gateway checks if a custom authorizer is configured, API Gateway then calls the Lambda function with the incoming authorization token. You can use Lambda to implement various authorization strategies (e.g. JWT verification, OAuth provider callout) that return IAM policies which are used to authorize the request. If the policy returned by the authorizer is valid, API Gateway will cache the policy associated with the incoming token for up to 1 hour.
* **Q: How are throttling rules applied?**  
  First. API Gateway checks against your AWS account limit. If the traffic is below the set account limit, API Gateway checks the limit you have set on a stage or method. If the traffic is below the stage limit, then API Gateway applies the usage plans limits you set on a per-API key basis.
* **Q: How am I charged for using Amazon API Gateway?**  
  Amazon API Gateway rates are $3.50 per million API calls, plus the cost of data transfer out, in gigabytes. If you choose to provision a cache for your API, hourly rates apply. Please see the API Gateway Pricing pages for details on data transfer and caching costs.

<a id="ses" />

## FAQs SES
<p align="right"><a href="#top">Top</a></p>

* **Q: What should I do after I'm finished testing and evaluating Amazon SES?**  
  Once you are ready to use Amazon SES to send email, you can request an Amazon SES sending limit increase. If granted, this increase will move your account out of the sandbox environment so that you can begin sending email to your customers. You will no longer need to verify recipient email addresses or recipient domains, and you will be able to send much larger quantities of email. To request a sending limit increase, please complete the request form in Support Center. We generally respond to these requests within 24 hours.
* **Q: What is the Amazon SES sandbox?**  
  The Amazon SES sandbox is an area in which new users can test the capabilities of Amazon SES. New Amazon SES users are automatically placed in the sandbox. While in the sandbox, you will only be able to send mail to verified email addresses, or to email addresses associated with the Amazon SES mailbox simulator. Additionally, while in the sandbox, you can send no more than 200 messages per 24-hour period, and no more than one message per second. When you are ready to move out of the sandbox, you can submit an SES Sending Limit Increase request.
* **Q: Is there a limit on the size of emails Amazon SES will deliver?**  
  Amazon SES will accept email messages up to 10 MB in size. This includes any images and attachments that are part of the message.
* The total number of email addresses in the To:, CC:, and BCC: field must not exceed 50 recipients.
* Sending limits are based on recipients rather than on messages. You can check your sending limits at any time by using the Amazon SES console.
* For more information about the Amazon SES mailbox simulator, see Testing Amazon SES Email Sending in the Amazon SES Developer Guide.
* **Q. Where does Amazon SES send my bounce, complaint, and delivery notifications?**  
  Delivery notifications are available through Amazon SNS. Bounces and complaints can be sent to you by email, through Amazon SNS, or both. If you choose to receive bounce and complaint notifications by email, Amazon SES will send you your bounce and complaint notifications based on the following logic: If you used the SMTP interface to send the message, then notifications go to the address specified in SMTP's required MAIL FROM command, which overrides any Return-Path header specified in the SMTP DATA. If you used the SendEmail API operation to send the message, then: If you specified SendEmail's optional ReturnPath parameter, then notifications go to the specified address. Otherwise, notifications go to the address specified in SendEmail's required Source parameter, which populates the From: header of the message. If you used the SendRawEmail API operation to send the message, then: If you specified SendRawEmail's optional Source parameter, then notifications go to that address, overriding any Return-Path header specified in the raw message. Otherwise, if the Return-Path header was specified in the raw message, then notifications go to that address. Otherwise, notifications go to the address in the From: header of the raw message.
* **Q: How can I monitor the bounce and complaint rates for the email I send using Amazon SES?**  
  Amazon SES provides three main ways to monitor your bounces, complaints, deliveries, sent emails, and rejected emails. The first method is to use the Amazon SES console, Amazon SES API, or Amazon CloudWatch to access basic email sending metrics across your entire AWS account. The second method is to set up Amazon SES to send you detailed feedback notifications through email or through Amazon SNS. The third method is to use Amazon SES event publishing. With event publishing, you categorize your emails and collect event data for each category of emails separately using either Amazon CloudWatch or Amazon Kinesis Firehose. You can set up Amazon Kinesis Firehose to send the event records to Amazon Redshift, Amazon S3, or Amazon Elasticsearch Service. If you use Amazon Elasticsearch Service, you can visualize your event data using Kibana. For more information about monitoring methods, see Monitoring Your Amazon SES Sending Activity in the Amazon SES Developer Guide.
* **Q: How is Amazon SES different from Amazon SNS?**  
  Amazon SES is for applications that need to send communications via email. Amazon SES supports custom email header fields, and many MIME types. By contrast, Amazon Simple Notification Service (Amazon SNS) is for messaging-oriented applications, with multiple subscribers requesting and receiving "push" notifications of time-critical messages via a choice of transport protocols, including HTTP, Amazon SQS, and email. The body of an Amazon SNS notification is limited to 8192 characters of UTF-8 strings, and is not intended to support multimedia content.
* **Q: How do I make requests to Amazon SES?**  
  Amazon SES accepts Query requests over HTTPS. These requests use verbs such as GET or POST, and a parameter named Action to indicate the action being performed. For security reasons, Amazon SES does not support HTTP requests; you must use HTTPS instead.

<a id="cfn" />

## FAQs CloudFormation
<p align="right"><a href="#top">Top</a></p>

* **Q: Can I install software at stack creation time using AWS CloudFormation?**  
  Yes. AWS CloudFormation provides a set of application bootstrapping scripts that enable you to install packages, files, and services on your EC2 instances by simply describing them in your CloudFormation template. For more details and a how-to see Bootstrapping Applications via AWS CloudFormation.
* **Q: Can I use AWS CloudFormation with Chef?**  
  Yes. AWS CloudFormation can be used to bootstrap both the Chef Server and Chef Client software on your EC2 instances. For more details and a how-to see Integrating AWS CloudFormation with Chef.
* **Q: Can I use AWS CloudFormation with Puppet?**  
  Yes. AWS CloudFormation can be used to bootstrap both the Puppet Master and Puppet Client software on your EC2 instances. For more details and a how-to see Integrating AWS CloudFormation with Puppet
* **Q: Can stack creation wait for my application to start up?**  
  Yes. AWS CloudFormation provides a WaitCondition resource that acts as a barrier, blocking the creation of other resources until a completion signal is received from an external source such as your application, or management system.
* **Q: Are there limits to the size of description fields?**  
  Template, Parameter, Output, and Resource description fields are limited to 4096 characters.
* **Q: Are there limits to the number of parameters or outputs in a template?**  
  You can include up to 60 parameters and 60 outputs in a template.


The End