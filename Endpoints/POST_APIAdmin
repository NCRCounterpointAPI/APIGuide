POST /APIAdmin

Description

Adds a new api admin to the repository

Requires API Key: No
Requires System Administrator: Yes
Requires Counterpoint Registration option: No
Sample Request

URI

POST https://localhost:81/User/Admin

Headers

Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx
Accept : application/json
Content-Type : application/json

Request Body

{
    "Password":{newPassword},
    "UserId":{newUserId}
}
Request Body

Name	Parameter Type	Data Type	Required	Description
AdminUsers	body	string list	true	The API admin user to add.
Response Codes

201 Created The request was successful, the customer was added to the Counterpoint database.
401 Unauthorized The request could not be fulfilled. Likely due to a missing or invalid authorization header.
403 Forbidden The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini
404 Not Found The requested resource could not be found but may be available again in the future. Subsequent requests by the client are permissible.
500 Internal Server Error The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
Error Codes

The following error codes may be returned from requests to this endpoint:

SUCCESS: User added successfully.

Response Body

This endpoint returns data related the customer just added:

Sample Response Body

{
  "ErrorCode": "SUCCESS",
  "Message": "User added successfully"
}
