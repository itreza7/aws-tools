# CI/CD
```yaml
version: 0.2
phases:
  install:
    runtime-versions:
      python: 3.10
    commands:
      - echo "Installing dependencies..."
      - pip install -r requirements.txt -t lib
  build:
    commands:
      - echo "Zipping deployment package..."
      - cd lib
      - zip -r9 ../deployment_package.zip .
      - cd ..
      - zip -gr deployment_package.zip application
      - zip -g deployment_package.zip main.py .env
  post_build:
    commands:
      - echo "Updating lambda Function..."
      - aws lambda update-function-code --function-name dt-users --zip-file fileb://deployment_package.zip
      - echo "DONE!!"
```
