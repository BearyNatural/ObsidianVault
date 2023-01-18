aws cloudformation validate-template --template-body <file://name.yaml>
aws cloudformation deploy --stack-name <> --region us-east-1 --template-file <name.yaml> %% --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM  %%
aws s3 cp index.html s3://bucketname/
aws cloudformation update-stack --stack-name <> --region <> --template-file <name.yaml>
aws cloudformation delete-stack --stack-name <> --region <>

options:
project1
project2
S3_CloudFront.yaml
S3_bucket.yaml
us-east-1
ap-southeast-2


Content of DNS Record is: {Name: _f3196250f80641d3937593c6da1dd3ef.daydreaminginthecloud.bearynatural.dev.,Type: CNAME,Value: _4bd0a7199308725cf341898aa8a400e6.pmgvbzmzyk.acm-validations.aws.}

aws s3 cp W:\My Documents\AWS - Docs\Projects\WebsiteDocs\index.html s3://daydreaminginthecloud/
W:\My Documents\AWS - Docs\Projects\WebsiteDocs


Lazy:
aws cloudformation validate-template --template-body file://S3_CloudFront.yaml 
aws cloudformation deploy --stack-name project2 --region us-east-1 --template-file S3_CloudFront.yaml
aws cloudformation delete-stack --stack-name project2 --region us-east-1

20230118_6
Incremental changes to view
Changes listed:
websiteCFD:
- Aliases
	- DomainName - added
	- DomainNameJoin
- CNAMEs
	- DomainNameJoin

issues still with ssl certificate error:
AWS::CloudFront::Distribution: The specified SSL certificate doesn't exist, isn't in us-east-1 region, isn't valid, or doesn't include a valid certificate chain.
hardcoded ssl certificate back in and validated it manually

```
18.       AliasTarget:
19.         HostedZoneId: !GetAtt 'myELB.CanonicalHostedZoneNameID'
20.         DNSName: !GetAtt 'myELB.DNSName'
```
Documentation found in aws docs github examples
https://github.com/awsdocs/aws-cloudformation-user-guide/blob/main/doc_source/quickref-route53.md



