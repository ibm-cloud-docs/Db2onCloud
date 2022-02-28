---

copyright:
  years: 2014, 2019
lastupdated: "2022-02-24"

keywords:

subcollection: Db2whc

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Connectivity options on Amazon Web Services
{: #connect_options_aws}

{{site.data.keyword.dashdblong}} offers secure connectivity options for your application connection requirements.  
{: shortdesc}

For application connections, do not use IP addresses to connect to the {{site.data.keyword.dashdbshort_notm}} instance, as the IP addresses resolved from the hostname may change. Use hostnames to reference your connection properties where it is available.
{: important}

## Connecting to Db2 Warehouse on Cloud with Amazon Web Services PrivateLink
{: #PrivateLink}

[Amazon Web Services (AWS) PrivateLink](https://aws.amazon.com/privatelink/){: external} gives you the ability to securely and privately connect to a {{site.data.keyword.dashdbshort_notm}} instance that is deployed on AWS from your own AWS VPCs, services, and applications. With AWS PrivateLink, traffic between {{site.data.keyword.dashdbshort_notm}} and your AWS VPCs, services, and applications does not traverse the public internet.

If you'd like to use AWS PrivateLink with {{site.data.keyword.dashdbshort_notm}}, complete the following steps:

1. Create an AWS principal to access {{site.data.keyword.dashdbshort_notm}}. The AWS principal can be AWS accounts, IAM users, or IAM roles.

2. Open a support ticket with {{site.data.keyword.cloud_notm}} to enable AWS PrivateLink, and provide the Amazon Resource Name (ARN) of the AWS principal that was created in the previous step. The principal is granted permission to access your {{site.data.keyword.dashdbshort_notm}} instance.
    
3. After the principal is granted permission, create an interface endpoint on your VPC to connect to the {{site.data.keyword.dashdbshort_notm}} service. See [Creating an Interface Endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#create-interface-endpoint){: external}. Ensure that TCP traffic is allowed through ports 50001, 443, and 8443 on the VPC, and set rules to allow traffic from the CIDR range associated with the VPC.
    
4. After the interface endpoint is created, provide the host names assigned to the endpoints so that they can be allowlisted in the {{site.data.keyword.dashdbshort_notm}} web console. After these host names are allowlisted, you can access your {{site.data.keyword.dashdbshort_notm}} instance by using the interface endpoint host names.

### Considerations and limitations

- AWS PrivateLink currently supports only TCP traffic. Tools that rely on UDP traffic, such as [IBM Lift CLI](https://www.lift-cli.cloud.ibm.com/){: external}, are not supported by PrivateLink. To load data, load directly from Amazon S3 into {{site.data.keyword.dashdbshort_notm}}. See [Loading data from Amazon S3](/docs/Db2whc?topic=Db2whc-load_s3).

  Extra charges might apply when you transfer data by using the public endpoint.
  {: note}

- You must create the Endpoint Service for accessing {{site.data.keyword.dashdbshort_notm}} in the same AWS region where the {{site.data.keyword.dashdbshort_notm}} instance is deployed. To access your instance from other AWS regions, you can use VPC Peering. See [Example: Services Using AWS PrivateLink and VPC Peering](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-peer-region-example.html){: external}.

For more information about AWS PrivateLink, see [Interface VPC Endpoints (AWS PrivateLink)](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html){: external}.
