#### SQS guide
  * When a customer receives and processes a message from a queue, the message remains in the queue. AWS SQS doesn't automatically delete the message.
  * SQS is a distributed system, there's no gurantee that the customer actually receives the message( for ex, due to connectivity issue, or due to an issue in the consumer application). Thus, the customer must delete the message from the queue after receiving and processing it. 
  * Immediately after a message is received, it remains in the queue. To prevent other consumers from processing the message again, AWS SQS sets a visibility timeout, a period of time during which AWS SQS prevents other consumers from receiving and processing the message. 
  * The default visibility timeout for a message is 30 seconds. The minimum is 0 seconds. The maximum is 12 hours.
#### AWS SQS Long Polling
  * long polling helps reduce the cost of SQS by eliminating the number of empty responses (when there are no message available for a ReceiveMessage request) and false empty responses (when messages are available but aren't included in a response). 
  * You can enable long polling for a new or existing queue using the AWS Management Console or AWS SDK for Java
```console
Benefits of Long Polling
    - Eliminate empty responses by allowing Amazon SQS to wait until a message is available in a queue before sending a response
    - Eliminate false empty responses by quering all
    - Return message as soon as they become available
```
#### Note: You can confirm that a queue is empty when you perform a long poll and the ApproximateNumberOfMessagesDelayed, ApproximateNumberOfMessagesNotVisible, and ApproximateNumberOfMessagesVisible metrics are equal to 0 at least 1 minute after the producers stop sending messages (when the queue metadata reaches eventual consistency). For more information, see Available CloudWatch Metrics for Amazon SQS.
#### AWS SQS Batch Actions
  * To reduce costs or manipulate up to 10 messages with a single action, you can use the following actions:
    * SendMessageBatch
    * DeleteMessageBatch
    * ChangeMessageVisibilityBatch
  * You can take advantage of batch functionality using the Query API, or an AWS SDK that supports the AWS SQS batch actions.
#### SQS facts
  * To select the message to delete, use the ReceiptHandle of the message (not the MessageID which you receive when you send the message)
  * You can use dead letter queues to isolate messages that can't be processed for later analysis.
  * SQS doesn't encrypt messages by default.
#### STS facts
  * STS enables you to request temporary, limited-privilege credentials.
  * STS enables users to assume role
  * STS generates Federated Credentials for IAM users
  * IAM user used to generate Federal User credentials does not have access on S3 bucket
  * AWS allows federated user's request only when both the attached policy and the IAM user policy explicitly allow the federated user to perform the requested action. 
#### STS AssumeRoleWithSAML
  * Returns a set of temporary security credentials for users who have been authenticated via a SAML authentication response. 
  * The temporary security credentials returned by this operation consist of an access key ID, a secret access key, and a security token.
  * By default, the temporary security credentials created by AssumeRoleWithSAML last for one hour. However, you can use the optional DurationSeconds parameter to specify the duration of your session.
#### Protocols for AWS SNS
  * HTTP
  * HTTPS
  * Email
  * Email-JSON
  * Amazon SQS
  * Application
  * AWS Lambda
  * SMS
#### SNS Message Filtering
  * to exclude message for someone in group
#### SNS Message Attribute Items and Validation
  * Name: A-Z, a-z, 0-9,underscore(_),hyphen(-), and periods(.). The name must not start or end with period. It can be 256 character long
  * Type: Data types are String, String.Array, Number, and Binary. the data is case-sensative and can be 256 bytes long
  * Value
  * message size restriction: 256 KB
  * Name, type, and value can't be empty or null. 
  
