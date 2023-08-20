# llama2_lamdda_ggml
Deploying Llama2 (GGML) on AWS Lambda

Description ::
```
Most Cost Effective, Just In Time way to use Llama2 on AWS Lambda for Serverless Computing
```

Technologies Used ::
```
Cloud 9 | AWS ECR | AWS LAMBDA | LLAMA2 | GGMl | CTRANSFORMERS
```

Steps ::
```
  aws ecr create-repository --repository-name llama2_ggml_lambda --image-scanning-configuration scanOnPush=true --image-tag-mutability MUTABLE

  aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 99149806775309.dkr.ecr.us-east-1.amazonaws.com

  docker build -t llama2_ggml_lambda .

  docker tag llama2_ggml_lambda:latest 99149806775309.dkr.ecr.us-east-1.amazonaws.com/llama2_ggml_lambda:latest

  docker push 99149806775309.dkr.ecr.us-east-1.amazonaws.com/llama2_ggml_lambda:latest


  llama2_ggml_lambda is the name of image
  99149806775309 is account number (Masked for Security Reasons)
  us-east-1 is region
```


Examples ::
```
{"context": "RIL Q1 Results: Net profit falls 10% to ₹16,011 cr as O2C biz offsets overall growth; retail, telecom arms thrive",
"question" : "What is Net Profit "}
```
```
{
	"context": "RIL Q1 Results: Net profit falls 10% to ₹16,011 cr as O2C biz offsets overall growth; retail, telecom arms thrive",
	"question" : "Did profit fell "
}
```
```
{
	"context": "RIL Q1 Results: Net profit falls 10% to ₹16,011 cr as O2C biz offsets overall growth; retail, telecom arms thrive",
	"question" : "What grew"
}
```

Reference ::
```
https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/deploy-lambda-functions-with-container-images.html
https://docs.aws.amazon.com/lambda/latest/dg/python-image.html
```
