# Very basic package created to learn 2GP packaging by adding a new feature to Order Management

## Package Features

Current:
 - Add rating and review on customer expereince on Order Delivery
 - Validation to check if Order Summary Status is Fulfilled before the review can be added/updated

Future:
 - Trigger email to customer when the Order Summary Status changes to Fulfilled
 - Landing page for customer on clicking the link in email to provide the rating and review for the order delivery experience


## Install Package
 - Tested package install using 2GP install command: example: sfdx force:package:install --package "OM Ratings@0.3.0-1" --targetusername mbomtrial -w 10
 - Further added the related list to record page: Setup -> Object Manager -> Order Summary Object -> Page Layout -> Drag OM Ratings related list
 - Add Rating and Review for an Order: Navigate to Order Management App -> Order Summary -> Related -> Order Ratings

<img width="1911" alt="image" src="https://user-images.githubusercontent.com/33846806/229158766-823a34d7-389c-4d1a-b9ac-6d6902acc9f2.png">


   
