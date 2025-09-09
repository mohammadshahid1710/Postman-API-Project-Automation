## 📌 Overview
This repository contains an automated API testing framework built with **Postman** and executed via **Newman** in a GitHub Actions CI/CD pipeline.  
It is designed to:
- Keep the Postman collection and environment in sync with the workspace
- Run automated API tests on every push, schedule, or manual trigger
- Generate a detailed **HTMLExtra** report
- Publish the latest report to **GitHub Pages** for easy access

**🔗 [View Latest Test Report](https://mohammadshahid1710.github.io/Postman-API-Project-Automation/)**

## ⚙️ How It Works
1. **Collection & Environment Sync**  
   - The workflow fetches the latest Postman collection and environment using the Postman API.
   - Any changes are committed back to the `main` branch automatically.

2. **Automated Test Execution**  
   - Tests are executed using [Newman](https://www.npmjs.com/package/newman) with the [HTMLExtra reporter](https://www.npmjs.com/package/newman-reporter-htmlextra).
   - The HTMLExtra report includes request/response details, assertion results, and visual charts.

3. **Report Publishing**  
   - The generated report is deployed to the `gh-pages` branch.
   - GitHub Pages serves the latest report at the link above.

## 📂 Repository Structure
.github/workflows/   # GitHub Actions workflow files
reqres_collection.postman_collection.json
reqres_environment.postman_environment.json

## 🚀 Running Locally
If you want to run the tests locally:

1. Install Newman & HTMLExtra:
   ```bash
   npm install -g newman newman-reporter-htmlextra
   ```

2. Run the collection:
   ```bash
   newman run reqres_collection.postman_collection.json \
     -e reqres_environment.postman_environment.json \
     -r htmlextra \
     --reporter-htmlextra-export reports/index.html

3. Open `reports/index.html` in your browser.

## 🛠️ CI/CD Workflow
The GitHub Actions workflow:
- Runs on push to `main`, scheduled daily, or manual trigger
- Fetches latest Postman files
- Runs Newman tests
- Publishes the HTMLExtra report to GitHub Pages
