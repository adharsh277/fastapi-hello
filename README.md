# 🚀 FastAPI Hello World on Azure

![FastAPI](https://img.shields.io/badge/FastAPI-Async%20Python-green?logo=fastapi)
![Azure](https://img.shields.io/badge/Azure-App%20Service-blue?logo=microsoftazure)
![CI/CD](https://img.shields.io/badge/GitHub-Actions-purple?logo=githubactions)
![Status](https://img.shields.io/badge/Status-Deployed-brightgreen)

---

## 📦 Project Overview

- **Framework**: [FastAPI](https://fastapi.tiangolo.com/)
- **Cloud Platform**: Microsoft Azure
- **Deployment**: Azure App Service
- **CI/CD**: GitHub Actions
- **IaC**: Azure CLI & Publish Profile (No Docker or Bicep)

---

## 🌐 Live Demo

🔗 [View Application](https://fastapi-app-28021.azurewebsites.net)

---

## 📁 Project Structure

```bash
fastapi-hello/
├── main.py             # FastAPI app
├── requirements.txt    # Dependencies
├── .github/
│   └── workflows/
│       └── azure-webapp.yml  # GitHub Actions deploy pipeline
├── .gitignore
└── README.md
🧠 How It Works
1. FastAPI App (main.py)
python
Copy
Edit
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"msg": "Hello from FastAPI on Azure!"}
2. Install Requirements
bash
Copy
Edit
pip install -r requirements.txt
3. Manual Deployment (Optional)
bash
Copy
Edit
az webapp up \
  --runtime "PYTHON:3.10" \
  --name fastapi-app-28021 \
  --resource-group fastapi-rg
4. GitHub Actions Workflow
Automatically deploys on every git push to main:

yaml
Copy
Edit
# .github/workflows/azure-webapp.yml
name: Build and Deploy to Azure Web App

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.10'

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Deploy to Azure Web App
        uses: azure/webapps-deploy@v2
        with:
          app-name: fastapi-app-28021
          publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }}
          package: .
✅ Features
🌐 Live-hosted FastAPI app

⚙️ CI/CD via GitHub Actions

🆓 Runs on Azure Free Tier

💨 Modern and async-ready backend framework

📄 License
This project is licensed under the MIT License.

🙋‍♂️ Author
Made with 💙 by Adharsh U

yaml
Copy
Edit

---

### ✅ How to Use It:
1. Copy the above into a file called `README.md`
2. Add it to your project folder.
3. Commit & push:

```bash
git add README.md
git commit -m "Add README file"
git push
