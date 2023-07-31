# Very basic package created to learn 2GP packaging by adding a new feature to Order Management

## Pre-requisite

-  Ensure you have Partner Business Org and your org is provisioned with Order Management
     - https://partners.salesforce.com/0694V00000KAZwJQAX

## Package Features

 - Add Rating and Review for Order on the customer's expereince about delivery experience of the order
 - Validation to check if Order Summary Status is Fulfilled before the review can be added/updated

## Create 2GP Package

   1. Register Namespace
      - Make PBO org as DevHub
          - Setup >> Dev Hub, and enable Dev Hub and Second-generation packaging
      - Create a unique namespace in a developer edition org from your Environment Hub
          - App Launcher >> Environment Hub and create a developer edition org
          - In developer edition org and go to Setup >> Package Manager >> Namespace Settings >> Edit and create a unique namespace
      - Register that namespace to your DevHub
          - Dev Hub org, go to App Launcher >> Namespace Registries >> Link Namespace
   
   2. Dev+Test in Scratch Org 
      - Create a scratch org to develop and test your app
          - Auth CLI to Dev Hub Org sf org login web -d -a myDevHubAlias
          - Make sure your project-scratch-def.json file has the org shape
          - Replace namespace in sfdx-project.json with one created above
          - Create a scratch org with sf org create scratch -f config/project-scratch-def.json -a MyScratchOrg --set-default
      - Develop and test your app in Scratch org and pull changes once done with sf retrieve metadata (or clone this repo)
      - Stage and Commit changes to git, then push to your branch in the remote repo (n/a if cloning this repo)
   
   3. Package the App
      - Create your package with sf package create -n "My Package Name" -r force-app -t Managed
      - Create a version of your package with sf package version create -p "My Package Name" -w 10 -x -c -f config/project-scratch-def.json
      - Test installing the package in a test scratch org with sf package install --package "My Package Name@0.1.0-1" --target-org MyNoNamespaceScratchOrg -w 10
      - Promote the package version to be listed in App Exchange sf package version promote -p "My Package Name@0.1.0-1"
      - Make sure Dev Hub org is connected under the Technologies tab of the Partner Console


## Install Package

 - Package install using 2GP install command to your org, example: sfdx force:package:install --package "OM Ratings@0.3.0-1" --targetusername mbomtrial -w 10
 - Ensure to add the related list to record page: Setup -> Object Manager -> Order Summary Object -> Page Layout -> Drag OM Ratings related list
 - Add Rating and Review for an Order: Navigate to Order Management App -> Order Summary -> Related -> Order Ratings

<img width="1911" alt="image" src="https://user-images.githubusercontent.com/33846806/229158766-823a34d7-389c-4d1a-b9ac-6d6902acc9f2.png">

## Test the Package

 - Add the Rating and Review for the Order by using Salesforce Postman Collection (below) OR directly add in Org at App Launcher -> Order Management -> Order Summaries -> Select Order Summary -> Related -> Order Ratings
     - https://github.com/jbachelet/sf-som-postman-collection
     - https://github.com/forcedotcom/postman-salesforce-apis
   
   ![image](https://github.com/mbhola/om-ratings/assets/33846806/c2870926-52ac-4317-830e-3db82aaac238)

  


   
