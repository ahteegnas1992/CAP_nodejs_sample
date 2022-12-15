# Hello World Getting Started Sample

## Next Steps

- To run the JavaScript implementation, open a new terminal and run `cds watch`.
- To run the TypeScript implementation, open a new terminal and run `cds-ts watch`.

Then call the service at: http://localhost:4004/say/hello(to='world')

## Learn More

Learn more about:

- [Hello World!](https://cap.cloud.sap/docs/get-started/hello-world)
- [Using TypeScript](https://cap.cloud.sap/docs/get-started/using-typescript)

## cicd script try 1
 # Project configuration
general:
  buildTool: "npm"                                  # "mta", "npm", or "maven" (default: "mta")
service:
  buildToolVersion: "Node 14"                     # depends on buildTool value, see table below
# Stage configuration
stages:
  Build:
    mavenExecuteStaticCodeChecks: true    # true, if you want to execute static code checks (default: false)
    npmExecuteLint: true                  # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
   Release:
    cloudFoundryDeploy: true                                                # true, if you want to deploy to Cloud Foundry. If you set this parameter to true, the CloudFoundryDeploy step is mandatory
    cfApiEndpoint: "https://api.cf.us10-001.hana.ondemand.com" # for example, "https://api.cf.eu10.hana.ondemand.com"
    cfOrg:  "7b45cd19trial"
    cfSpace: "dev"                           # the Cloud Foundry space, to which you want to deploy your application
    cfAppName: "hello"    
    cfCredentialsId: "deploy-cf"
    tmsUpload: false

# Step configuration
steps:
  npmExecuteLint:
    failOnError: true
  npmExecuteScripts:                                                        # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
    runScripts:
        - "test"         
        


