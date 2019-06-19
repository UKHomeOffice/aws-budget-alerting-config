# Configuration of AWS Budget alerting

Example config showing how to use [aws-budget-alerting](https://github.com/UKHomeOffice/aws-budget-alerting)

This repo automates the config steps specified in [aws-budget-alerting](https://github.com/UKHomeOffice/aws-budget-alerting) in a Drone pipeline.

To set up AWS Budget monitoring to Slack for your own AWS account, fork this repo and amend the [`parameters.sh`](./parameters.sh) file.

In your Drone pipeline, you will also have to set the following secrets:

* lambda_package_bucket: the name of the bucket in which the Lambda function has to be packaged
* aws_default_region: the AWS region 
* aws_access_key_id: the access key id giving access to the bucket, SNS topics, Lambda and AWS budgets
* aws_secret_access_key: the secret access key giving access to the bucket, SNS topics, Lambda and AWS budgets
* actual_cost_webhook_url: the url of the Slack channel to post actual cost trigger messages
* forecasted_cost_webhook_url: the url of the Slack channel to post forecasted cost trigger messages

To create a role with minimal privileges that allows you to manage budget alerts, you can use [aws_budget_alerting_management_role.py](https://github.com/UKHomeOffice/aws-budget-alerting/blob/master/src/aws_budget_alerting_management_role.py)

The [Setting up a role to allow you to manage the alerting resources](https://github.com/UKHomeOffice/aws-budget-alerting) section in the `aws-budget-alerting` repo's ReadMe has more information about creating that role.
