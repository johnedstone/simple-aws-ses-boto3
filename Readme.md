### References

* https://boto3.amazonaws.com/v1/documentation/api/latest/guide/credentials.html
* https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sesv2.html
* https://docs.aws.amazon.com/ses/latest/DeveloperGuide/sending-email-suppression-list.html

### Example

```
>>> import boto3
>>> from pprint import pprint
>>> session = boto3.Session(profile_name='put your profile in ~/.aws/credentials here')
>>> ses_client = session.client('sesv2')
>>> response = ses_client.list_suppressed_destinations()
>>> pprint(response)
{'ResponseMetadata': {'HTTPHeaders': {'content-length': '147',
                                      'content-type': 'application/x-amz-json-1.1',
                                      'date': 'Sat, 22 Aug 2020 01:40:13 GMT',
                                      'x-amzn-requestid': '1414989d-5d9b-42d1-8b8e-04a01b27d53b'},
                      'HTTPStatusCode': 200,
                      'RequestId': '1414989d-5d9b-42d1-8b8e-04a01b27d53b',
                      'RetryAttempts': 0},
 'SuppressedDestinationSummaries': [{'EmailAddress': 'mail@-----.org',
                                     'LastUpdateTime': datetime.datetime(2020, 7, 8, 13, 16, 31, 308000, tzinfo=tzlocal()),
                                     'Reason': 'BOUNCE'}]}
>>> response = ses_client.delete_suppressed_destination(EmailAddress='mail@-----.org')
>>> response = ses_client.list_suppressed_destinations()
>>> pprint(response)
{'ResponseMetadata': {'HTTPHeaders': {'content-length': '54',
                                      'content-type': 'application/x-amz-json-1.1',
                                      'date': 'Sat, 22 Aug 2020 01:49:23 GMT',
                                      'x-amzn-requestid': '7d18e03e-0136-418d-98b0-41cc6698ecde'},
                      'HTTPStatusCode': 200,
                      'RequestId': '7d18e03e-0136-418d-98b0-41cc6698ecde',
                      'RetryAttempts': 0},
 'SuppressedDestinationSummaries': []}
>>>

```
