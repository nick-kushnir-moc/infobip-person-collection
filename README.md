# Infobip People Postman Collection

This repository provides a Postman Collection for managing contacts (people) in **Infobip’s Customer Engagement** platform using the **Infobip People API**. With this collection, you can **create**, **retrieve**, **update**, and **delete** person records, as well as manage custom list attributes.

---

## Table of Contents

1. [Prerequisites](#prerequisites)  
2. [Importing the Collection](#importing-the-collection)  
3. [Environment Setup](#environment-setup)  
4. [Available Requests](#available-requests)  
5. [Usage and Workflow](#usage-and-workflow)  
6. [Error Handling](#error-handling)  
7. [Further Reading](#further-reading)

---

## Prerequisites

### Infobip Account
- You need valid Infobip credentials (`API key`) and a base URL, typically in the format:
https://{YOUR_DOMAIN}.api.infobip.com

### Postman
- Ensure you have the [Postman](https://www.postman.com/downloads/) API testing tool installed.

### Infobip People Placeholders Setup (if using custom attributes)
- If you plan to use custom attributes or list placeholders (e.g., `ShoppingCartList`), make sure these are defined in your **Infobip People workspace**—either via the Infobip web portal or via placeholder management APIs—before using them in the requests.

---

## Importing the Collection

1. **Clone or Download this Repository**  
 - Locate the file named `Infobip People - Full Collection.json` (or a similar filename).

2. **Open Postman**  
 - Click the **Import** button (usually in the top-left corner).

3. **Choose the Collection File**  
 - Drag and drop the JSON file into Postman **or** use **File → Upload Files**.

4. **Click “Import”**  
 - The collection should now appear in your Postman sidebar.

---

## Environment Setup

To avoid hardcoding repeated values (like your authorization key) in each request, use **Postman Environments**:

1. **Manage Environments**  
 - In Postman, click the gear icon in the top-right corner.

2. **Create a New Environment**  
 - Give it a name (e.g., `Infobip Environment`).

3. **Add Variables**  
For example:
baseUrl → https://YOUR_DOMAIN.api.infobip.com authorization → App YOUR_API_KEY limit → 10 (optional) offset → 0 (optional) personId → <ID or placeholder for an existing person>
- `limit` and `offset` are common pagination parameters.
- `personId` is useful for single-person GET or DELETE requests.

4. **Select This Environment**  
- In the top-right corner of Postman, pick your new environment from the dropdown.
- Now all requests in the collection that reference `{{baseUrl}}` or `{{authorization}}` will use these variables.

---

## Available Requests

Below is an overview of the requests included in the collection (assuming version `v2` for the People API):

1. **Get All Persons**  
GET {{baseUrl}}/people/2/persons?limit={{limit}}&offset={{offset}}
- Retrieves a paginated list of persons.

2. **Get Single Person**
GET {{baseUrl}}/people/2/persons/{{personId}}
- Fetches details for a specific person by internal ID.

3. **Create Single Person**  
POST {{baseUrl}}/people/2/persons
- Creates a new person record.

4. **Patch Single Person**  
PATCH {{baseUrl}}/people/2/persons
- Partially updates a person using a **query object** (by ID, PHONE, EMAIL, or EXTERNAL_ID).

5. **Delete Single Person**  
DELETE {{baseUrl}}/people/2/persons
- Removes a single person using a **query** in the request body.

6. **Batch People Create**  
POST {{baseUrl}}/people/2/persons/batch

- Creates multiple people in one request.

7. **Batch People Update**  
PATCH {{baseUrl}}/people/2/persons/batch
- Partially updates multiple people in a single request.

8. **Batch People Delete**  
DELETE {{baseUrl}}/people/2/persons/batch
- Deletes multiple people in one request.

9. **Get Lists**  
POST {{baseUrl}}/people/2/lists
- Retrieves items from specified list attributes (e.g., `ShoppingCartList`, `Tags`).

10. **Patch Lists**  
 ```
 PATCH {{baseUrl}}/people/2/lists
 ```
 - Adds or updates list items for your defined list placeholders.

11. **Delete List Items**  
 ```
 DELETE {{baseUrl}}/people/2/lists
 ```
 - Removes specified items from a list attribute.

---

## Usage and Workflow

1. **Select Environment**  
- Ensure your environment (e.g., `Infobip Environment`) is active in the top-right dropdown.

2. **Edit Variables**  
- Double-check the values for `{{baseUrl}}` and `{{authorization}}` to match your Infobip account details.

3. **Open a Request**  
- Expand the collection in the Postman sidebar and select a request.

4. **Review or Edit the Request Body (if applicable)**  
- For create or update requests, adjust `firstName`, `lastName`, and any custom attributes.

5. **Send the Request**  
- Click **Send** and observe the response in the **Body** tab at the bottom.

6. **Check Status**  
- A `2xx` status code indicates success.
- A `4xx` or `5xx` code indicates an error—check the response JSON for more details.

---

## Error Handling

- **400 Bad Request**: Malformed request body or query parameters. Validate your JSON.
- **401 Unauthorized**: Invalid or missing API key. Check your `{{authorization}}`.
- **404 Not Found**: The requested person or resource doesn’t exist.
- **409 Conflict**: Occurs when placeholders aren’t defined (e.g., `ShoppingCartList`) or phone numbers violate formatting rules.
- **429 Too Many Requests**: Rate limit exceeded; wait before sending more requests.

Always check the response JSON for detailed Infobip error messages.

---

## Further Reading

- **Official Infobip People API Documentation**  
[Customer Engagement: People](https://www.infobip.com/docs#people)

- **Infobip Developer Hub**  
[https://www.infobip.com/docs](https://www.infobip.com/docs)

- **Troubleshooting & Community**  
- [Infobip Support](https://www.infobip.com/contact)  
- [Infobip Developer Community](https://community.infobip.com/)

---

> **Note:** This collection and guide help you quickly test and integrate with the Infobip People API. For the most up-to-date information, always refer to the [official Infobip documentation](https://www.infobip.com/docs).






