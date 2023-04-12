## Overview

In this section, you will see how to complete three main tasks:

1. Use the low-code editor to design your first flow and run it locally.
2. Deploy the flow to the Postman cloud.
3. Use Postman to trigger the flow in the cloud.

## Prerequisites

1. Find and fork both collections and the environment in the Connected car workspace: https://www.postman.com/postman-academy-team-v10/workspace/connected-drive-postman-flows-workspace/overview

2. Create a vehicle for testing by running the "Create vehicle" request in your "Utility Services" collection fork. In the request body, you can initialize the engine status and the interior temperature of the new vehicle. In the response, you will find the VIN of the newly initialized vehicle. You will use this VIN to test your flow later, so save it somewhere to find it again easily. You can also come back anytime to create as many test vehicles as you need. Note: Select the Test Server environment when you run the request.

## Send and authorize a request

learn how to create a flow that climatizes a vehicle’s cabin and ultimately send your first request from that flow.

- URL: https://customer-education.postmanlabs.com/workshops/flows
- API Key: 1234

## Send, receive and process data

Design your flow to dynamically take the input parameters to find the correct vehicle to climatize.

## Work with Logic and Task blocks

Learn how to check if the vehicle is running, how to turn it on if it’s stopped, how to climatize the vehicle for a certain amount of time and then turn off the vehicle.

## Deploy your flow to the Postman Cloud

Learn how to deploy your Flow to the Cloud and make it available to the vehicle owners who are connected to your database. This way, they can use your website or app to interact with the Flow to remotely climatize their vehicles. You’ll use Postman to simulate a remote execution of your Flow.
