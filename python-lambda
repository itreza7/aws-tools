# Deploy Python scripts as a lambda function

```bash
echo "Installing dependencies..."
pip install -r requirements.txt -t lib
echo "Zipping deployment package..."
cd lib
zip -r9 ../deployment_package.zip .
cd ..
zip -gr deployment_package.zip application
zip -g deployment_package.zip main.py .env
```
