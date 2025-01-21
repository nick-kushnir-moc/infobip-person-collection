Infobip People Postman Collection
This repository provides a Postman Collection for managing contacts (people) in Infobip’s Customer Engagement platform using the Infobip People API. You can create, retrieve, update, and delete person records as well as manage custom list attributes.

Table of Contents
Prerequisites
Importing the Collection
Environment Setup
Available Requests
Usage and Workflow
Error Handling
Further Reading
Prerequisites
Infobip Account
You need valid Infobip credentials (API key) and a base URL (e.g., https://{YOUR_DOMAIN}.api.infobip.com).

Postman
Download and install the Postman API testing tool.

Infobip People Placeholders Setup (if using custom attributes)
If you plan to use custom attributes or list placeholders (e.g., ShoppingCartList), make sure these are defined in your Infobip People workspace—either via Infobip web portal or via placeholder management APIs—before using them in the requests.

Importing the Collection
Clone or Download this Repository

If you have the repo, you’ll see a file named Infobip People - Full Collection.json (or similar).
Open Postman

Click the Import button (top-left corner).
Choose the Collection File

You can drag and drop the JSON file or use the File/Upload Files option.
Click “Import”
The collection will appear in your Postman sidebar.

Environment Setup
To avoid hardcoding repeated values (like your authorization key) in each request:

Manage Environments

In Postman, click the gear icon in the top-right corner.
Create a New Environment

Give it a name, e.g., Infobip Environment.
Add Variables

baseUrl: https://YOUR_DOMAIN.api.infobip.com
authorization: App YOUR_API_KEY
limit (optional): e.g., 10
offset (optional): e.g., 0
personId (optional): ID or placeholder for an existing person—helpful for single-person GET/DELETE requests
Select This Environment

From the dropdown in the top-right corner, choose your new environment.
Once set, the collection requests will automatically use these variables (e.g., {{baseUrl}}).

Available Requests
Below is an overview of the requests included in the collection:

Get All Persons

GET {{baseUrl}}/people/2/persons?limit={{limit}}&offset={{offset}}
Retrieves a paginated list of persons.
Get Single Person

GET {{baseUrl}}/people/2/persons/{{personId}}
Fetches details for a specific person by internal ID.
Create Single Person

POST {{baseUrl}}/people/2/persons
Creates a new person record.
Patch Single Person

PATCH {{baseUrl}}/people/2/persons
Partially updates a person using a query object (e.g., identifier by ID, PHONE, EMAIL, or EXTERNAL_ID).
Delete Single Person

DELETE {{baseUrl}}/people/2/persons
Removes a single person using a query in the request body.
Batch People Create

POST {{baseUrl}}/people/2/persons/batch
Creates multiple people in one request.
Batch People Update

PATCH {{baseUrl}}/people/2/persons/batch
Partially updates multiple people in a single request.
Batch People Delete

DELETE {{baseUrl}}/people/2/persons/batch
Deletes multiple people in one request.
Get Lists

POST {{baseUrl}}/people/2/lists
Retrieves items from specified list attributes (e.g., ShoppingCartList, Tags).
Patch Lists

PATCH {{baseUrl}}/people/2/lists
Adds or updates list items for your defined list placeholders.
Delete List Items

DELETE {{baseUrl}}/people/2/lists
Removes specified items from a list attribute.
Usage and Workflow
Select Environment: Make sure your environment is active in the top-right dropdown in Postman.
Edit Variables: Double-check {{baseUrl}} and {{authorization}} for correctness.
Open a Request: Click a request from the collection in the sidebar.
Review or Edit the Body (if applicable):
For create or update requests, adjust firstName, lastName, custom attributes, etc.
Send: Click Send and observe the response in the Body tab at the bottom.
Check Status: A 2xx status code indicates success. A 4xx or 5xx code indicates an error—check the response JSON for more details.
Error Handling
400 Bad Request: The request body or query parameters might be malformed. Validate your JSON.
401 Unauthorized: Likely an invalid or missing API key. Check your authorization variable and Infobip credentials.
404 Not Found: The requested person or resource doesn’t exist.
409 Conflict: Often occurs when placeholders aren’t defined (e.g., ShoppingCartList) or phone numbers don’t match formatting rules.
429 Too Many Requests: You’ve hit a rate limit; wait or reduce your request frequency.
Always check the response JSON for Infobip’s detailed error messages.

Further Reading
Official Infobip People API Documentation
Customer Engagement: People

Infobip Developer Hub
https://www.infobip.com/docs

Troubleshooting & Community

Infobip Support
Infobip Developer Community
