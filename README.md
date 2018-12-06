# CognitoService
This service is creating using AWS API Gateway as well as AWS Lambdas and AWS Cognito. I would love to get it all working using CloudFormation but until then I will just doucment what I have working.

## Endpoints
  The context for the api currently is: https://t4o3pxu8dj.execute-api.us-west-2.amazonaws.com/dev

**Authenticate Token**

* **URL**

 `/cognito/auth`

* **Method:**
  `GET`

* **Success Response:**
  * **Code:** 200  
    **Content:** `{ id : 12 }`
 
* **Error Response:**

  <_Most endpoints will have many ways they can fail. From unauthorized access, to wrongful parameters etc. All of those should be liste d here. It might seem repetitive, but it helps prevent assumptions from being made where they should be._>

  * **Code:** 200 SUCCESS <br />
    **Content:** ``

  OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{
    "message": "The incoming token has expired"
    }`
 
 OR 
 
 * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{
    "message": "Unauthorized"
    }`  
    Occurs if there is no token attached

* **Sample Call:**

  <_Just a sample call to your endpoint in a runnable format ($.ajax call or a curl request) - this makes life easier and more predictable._> 

* **Notes:**

  <_This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself when leaving comments here._> 




* **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{
      "User": {
          "Username": "01e05880-930d-4150-a9e0-6c515b546416",
          "Attributes": [
              {
                  "Name": "sub",
                  "Value": "01e05880-930d-4150-a9e0-6c515b546416"
              },
              {
                  "Name": "email",
                  "Value": "btkruppa513@gmail.com"
              }
          ],
          "UserCreateDate": "2018-12-05T21:16:41.771Z",
          "UserLastModifiedDate": "2018-12-05T21:16:41.771Z",
          "Enabled": true,
          "UserStatus": "FORCE_CHANGE_PASSWORD"
      }
  }`
  
