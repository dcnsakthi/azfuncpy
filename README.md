# Azure Function on Visual Studio Code (VSCode)
Note: Creating first Azure Function on Windows and Visual Studio Code with GitHub Repository.   

## 1. Create GitHub Repo
Prerequisite: [Sign up](https://github.com/join) for new GitHub account if you don't have already.

<img src=".images\CreateRepoGitHub.png" height=500 width=650 border=1>

## 2. Clone GitHub Repo to Local

Prerequisite: Install Windows Git and VSCode if you don't have already.

<img src=".images\CloneRepoGitHub.png" height=250 width=650 border=1>

## 3. Launch cloned repo in VSCode and create a new folder `http`

Prerequisite: Install VSCode if you don't have already.

<img src=".images\CreateWorkingDirectories.png" height=120 width=650 border=1>

## 4. Create Azure Function project from Command Palette (Ctrl+Shift+P)

Prerequisite: New directory (e.g., http) if you want to place generated code into separate directory.

<img src=".images\CreateFunctionProject.png" height=200 width=650 border=1>

1. Press `Ctrl+Shift+P` for Command Palette and type `Azure Functions: Create New Project..`
2. Select working directory `http` where the code should be generated
3. Select the Language as `Python` (Select your language of choice and following configurations.) <br>
<img src=".images\SelectLanguageAsPython.png" height=150 width=600 border=1> <br>
4. Create a Virtual Environment `Python` Version.<br>
<img src=".images\SelectPythonEnvironment.png" height=150 width=600 border=1> <br>
5. Enter function name as `nscsa` (as per your requirements). <br>
6. Select Access Rights as `Anonymous` if you want to make this API as public. <br>
<img src=".images\SelectAccessRights.png" height=150 width=600 border=1> <br>

## 5. Review the code under `http` directory and changes as required

Prerequisite: Python code should be generated (`__init__.py`) under `http` directory.

<img src=".images\GeneratedCodeSnippet.png" height=220 width=650 border=1>

## 6. Run `Start Debugging` or Press `F5` to attach to Python Process (.venv)

Prerequisite: Auto Generated `host.json`, `function.json` and `local.settings.json` should exists under `http` directory.
```
host.json

{
  "version": "2.0",
  "logging": {
    "applicationInsights": {
      "samplingSettings": {
        "isEnabled": true,
        "excludedTypes": "Request"
      }
    }
  },
  "extensionBundle": {
    "id": "Microsoft.Azure.Functions.ExtensionBundle",
    "version": "[2.*, 3.0.0)"
  }
}

```

```
local.settings.json

{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "",
    "FUNCTIONS_WORKER_RUNTIME": "python"
  }
}
```

```
function.json

{
  "scriptFile": "__init__.py",
  "bindings": [
    {
      "authLevel": "anonymous",
      "type": "httpTrigger",
      "direction": "in",
      "name": "req",
      "methods": [
        "get",
        "post"
      ]
    },
    {
      "type": "http",
      "direction": "out",
      "name": "$return"
    }
  ]
}

```
<img src=".images\AttachToPythonFunction.png" height=280 width=650 border=1>

## 7. Test the function with http request and Query Parameter using Browser

Prerequisite: Attach to Python Functions by `Start Debugging or Press F5` and Web Browser.

1. http URL request (`http://localhost:7071/api/nscsa`) using web browser <br>
<img src=".images\HttpFunctionResponse.png" height=80 width=600 border=1> <br>
2. http URL request with Query Parameter (`http://localhost:7071/api/nscsa?name=World`) using web browser <br>
<img src=".images\HttpFunctionResponseWithParam.png" height=80 width=600 border=1><br>

## 8. Test the function with http request and Query Parameter using Postman

Prerequisite: Attach to Python Functions by `Start Debugging or Press F5` and Postman.

1. http URL requset (`http://localhost:7071/api/nscsa`) using Postman <br>
<img src=".images\PostmanHttpRequest.png" height=200 width=600 border=1> <br>
2. http URL requset with Query Parameter (`http://localhost:7071/api/nscsa?name=World`) using Postman <br>
<img src=".images\PostmanHttpRequestParam.png" height=200 width=600 border=1>

## 9. Deploy to Azure Function using VSCode

Prerequisite: Successfully Build project (`http.csproj`) and Azure Subscription. <br> 

<img src=".images\DeployToAzureFunction.png" height=450 width=650 border=1>

1. Create Azure Fucntion manually or use VSCode to Deploy directly with required inputs to Azure. <br>
<img src=".images\CreateAzureFunction.png" height=400 width=600 border=1> <br>

2. Sign-in to Azure using VSCode and Select the Azure Function target.<br>
<img src=".images\DeployToFunctionNSCSA.png" height=150 width=600 border=1> <br>

## 10. Test the function with http request and Query Parameter using Postman & Browser

Prerequisite: Successful deployment to Azure Function.

1. http URL requset with Query Parameter (`https://nscsa.azurewebsites.net/api/nscsa?name=Azure`) using Browser <br>
<img src=".images\HttpAzureFunctionResponse.png" height=80 width=600 border=1><br>
2. http URL requset with Query Parameter (`https://nscsa.azurewebsites.net/api/nscsa?name=Azure`) using Postman <br>
<img src=".images\PostmanHttpAzureRequestParam.png" height=200 width=600 border=1><br>

## 11. Commit and Push to GitHub

Prerequisite: GitHub Repo and Windows Git.

<img src=".images\CommitAndPushToRepo.png" height=650 width=650 border=1>

## 12. Continuous Deployment to Azure Function using GitHub Action

Prerequisite: GitHub Repo with updated code base.

Setup GitHub Action Workflow for Azire Function Deployment or Connect to GitHub from Azure Function.

---
Technology Used

- VSCode
- VSCode Azure Function Extension
- Postman
- Browser
- Azure Subscription
- Azure Function
- GitHub
- Python 3.9

Happy Learning !