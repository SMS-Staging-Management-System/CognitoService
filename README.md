# CognitoService
This service is creating using AWS API Gateway as well as AWS Lambdas and AWS Cognito. I would love to get it all working using CloudFormation but until then I will just doucment what I have working.

## Endpoints
  The context for the api currently is: https://t4o3pxu8dj.execute-api.us-west-2.amazonaws.com/dev

**Authenticate Token**

* **URL**

 `/cognito/auth`  
 Changed from `/auth` - currently both work but `/auth` will be removed in the future

* **Method:**
  `GET`

* **Success Response:**
  * **Code:** 200  
    **Content:** 
    ```json
    {  
      "sub": "a993f745-d063-4321-ac6e-fd9a18f8b931",  
      "aud": "49f1foekljhlqn185fme63hi0s",  
      "cognito:groups": "admin,staging-manager",  
      "email_verified": "true",  
      "event_id": "280fba4a-f971-11e8-9419-c77846ddcac6",  
      "token_use": "id",  
      "auth_time": "1544112503",  
      "iss": "https://cognito-idp.us-west-2.amazonaws.com/us-west-2_8b6WpHm1z",  
      "cognito:username": "a993f745-d063-4321-ac6e-fd9a18f8b931",  
      "exp": "Thu Dec 06 17:08:23 UTC 2018",  
      "iat": "Thu Dec 06 16:08:23 UTC 2018",  
      "email": "blake.kruppa@revature.com"  
    }
    ```  
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "message": "The incoming token has expired"
    }
    ```

  OR 
 
  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "message": "Unauthorized"
    }
    ```    
    Occurs if there is no token attached


* **Headers:**  
   `Authentication`: The access token provided by cognito.


**Register New User**

* **URL**

 `/cognito/users`

* **Method:**
  `POST`

* **Success Response:**
  * **Code:** 200  
    **Content:** 
    ```json
    {
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
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "message": "The incoming token has expired"
    }
    ```

  OR 
 
  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "message": "Unauthorized"
    }
    ```    
    Occurs if there is no token attached


* **Headers:**  
   `Authentication`: The access token provided by cognito.
