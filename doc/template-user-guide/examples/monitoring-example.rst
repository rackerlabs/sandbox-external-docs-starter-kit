.. _monitoring-example-ug:

====================
Monitoring (example)
====================

AWS CloudWatch is the primary monitoring system used by our Fanatical Support
for AWS support teams. CloudWatch provides a wide variety of metrics that cover
the entire suite of AWS services, from CPU utilization and disk I/O on EC2
instances to network throughput of ELB load balancers.

Although AWS CloudWatch is available to Fanatical Support for AWS accounts at
all service levels, customers using our Aviator service level can opt to have
Rackespace Support respond to unexpected deviations in metrics. Watchman is the
system responsible for receiving CloudWatch alarms and creating tickets on your
Rackspace account.

CloudWatch alarms
~~~~~~~~~~~~~~~~~

CloudWatch alarms are triggered when the value of a CloudWatch metric
deviates from its expected value. For example, if CPU utilization on an EC2
instance exceeds 80 percent for a period of five minutes or longer, the
CloudWatch alarm can be configured to send an alert to a Rackspace-managed
Simple Notification Service (SNS) topic (named rackspace-support) that
generates a ticket for further investigation by a Rackspace.

The rackspace-support SNS topic is configured in each region when your AWS
account is set up for Fanatical Support for AWS. A subscription to the SNS
topic is created for a centralized, region-specific Simple Queue Service (SQS)
queue that resides in our shared management services account. Our shared
management services system continually monitors these queues and generates a
ticket when a valid CloudWatch alarm is received from an Aviator service level
account.

.. note::

   Although the SNS topic is present on every Fanatical Support for AWS
   account, only accounts at the Aviator service level have tickets
   generated. If your account is at the Navigator service level, no action
   is taken for CloudWatch alarm notifications sent to your account’s
   rackspace-support SNS queue.

Custom CloudWatch configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

CloudWatch allows the creation of custom metrics to monitor the things that are
critical to the uptime of your applications. As an Aviator customer, you can
create custom CloudWatch metrics and alarms, and send notifications to the
rackspace-support SNS topic if you want Rackspace to respond to a triggered
alarm. We recommend that you work with Rackspace when creating custom
CloudWatch metrics and alarms to ensure that the configuration is correct
and that the appropriate Rackspace response is clearly documented.
