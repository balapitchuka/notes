# AWS Lambda


### The Serverless Framework
- Serverless framework aims to ease the pain of creating, deploying, managing and debugging lambda functions.

- Install Serverless
    - Install dependencies(node and aws cli)
    - Install serverless framework
        - **npm install -g serverless**
        - **serverless  config credentials --provider aws --key xxx --secret xxx --profile serverless-admin**


### deploy using serverless
1. create lambda function locally
> sls create --template aws-python --path hello-world-python
2. deploy usihg serverless framework
> sls deploy -v
3. invoking lambda function using serverless framework
> sls invoke -f hello -l

4. deploying any changes in existing function
> sls deploy function -f hello

5. fetching function logs (this commands streams log continuously as the function gets invoked)
> sls  logs  -f  hello  -t

6. removing the function
> sls remove


### Advantages of Serverless Framework
All using programming(not manual clicks in the aws console)
Can be integrated with Continuous Integration frameworks
Can be integrated with Continuous Delivery frameworks
