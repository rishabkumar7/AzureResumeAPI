# ResumeAPI w/ Azure Functions
Resume API challenge with Azure Functions

## Introduction 📑
I've been inspired by the Cloud Resume Challenge by Forest Brazeal to build more stuff in the cloud. I wanted to build something simple to continue my Cloud journey. I decided to build an open-source REST API for my JSON-based standard format resume. I'm using JavaScript and Azure Functions.

## Technologies ⚙
- Azure Functions

## Languages
- Python
- JavaScript

## Let's get going 🚀
As part of the #ServerlessSeptember, I submited my project as an article for the event and you can reference to my article here in order to get started with the Resume API.
I used this [Resume JSON Schema](https://jsonresume.org/schema/) to create my resume in JSON format.

<a href="https://blog.rishabkumar.com/how-i-built-a-resume-api-with-javascript-and-azure-functions-ckesofyvt00grkls17pir3qd9"><img src ="https://img.shields.io/badge/Blog-Blog-blue"></a>
## Submit your API endpoint
 - Please fork this repo
 - Edit the ResumeEndpoints.md
 - Submit a PR
 - Show it off on your resume.


## How to create a function using Azure Functions CLI
- [Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash%2Ckeda)

In Azure Functions, a function project is a container for one or more individual functions that each responds to a specific trigger. All functions in a project share the same local and hosting configurations. In this section, you create a function project that contains a single function.

Run the func init command, as follows, to create a functions project in a folder named LocalFunctionProj with the specified runtime:
`func init LocalFunctionProj --javascript`

Let's navigate into the project folder:
`cd LocalFunctionProj`

This folder contains various files for the project, including configurations files named local.settings.json and host.json. Because local.settings.json can contain secrets downloaded from Azure, the file is excluded from source control by default in the .gitignore file.

Add a function to your project by using the following command, where the --name argument is the unique name of your function (resume) and the --template argument specifies the function's trigger (HTTP).
`func new --name resume --template "HTTP trigger"`

`func new` creates a subfolder matching the function name that contains a code file appropriate to the project's chosen language and a configuration file named function.json.

- index.js
`index.js` exports a function that's triggered according to the configuration in `function.json.`

```
module.exports = async function (context, req) {
    context.log('JavaScript HTTP trigger function processed a request.');

    const name = (req.query.name || (req.body && req.body.name));
    const responseMessage = name
        ? "Hello, " + name + ". This HTTP triggered function executed successfully."
        : "This HTTP triggered function executed successfully. Pass a name in the query string or in the request body for a personalized response.";

    context.res = {
        // status: 200, /* Defaults to 200 */
        body: responseMessage
    };
}
```
