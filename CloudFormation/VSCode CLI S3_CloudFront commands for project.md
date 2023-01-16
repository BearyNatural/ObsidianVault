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