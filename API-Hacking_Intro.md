[Reference](https://www.youtube.com/@InsiderPhD)

## API(Application Programming Interface) : 
   - Way to communicate with Backend DataBase or Logic

## Types of API :
#### 1 - SOAP API
   - Less common now days
   - Usually uses XML
   - Has header and body

#### 2 - RESTful  API
   - Most common API
   - Uses JSON
   - Defined Structure in Request

#### 3 - GraphQL API
   - Newcomer on the Scene
   - Uses custom query Language
   - A single endpoint powers all of the API

#### 4 - Others
   - Standalone JSON calls
   - Websockets are also used as API
---
### RESTful API 
   - Really easy to Spot(Defined structure related to CRUD functionality)
   - Can be easily predict new endpoints
   - Some endpoints may be more custom
         `DELETE /api/comment/1/`   --> `POST /api/comment/1/delete`
   - Usually return JSON

    CREATE --> POST /comments/

    READ   --> GET /comments/1
    
    UPDATE --> POST /comments/1
               PUT /comments/1
               POST /commments/1/edit
    
    DELETE --> DELETE /comments/1
           --> POST /comments/1/delete

### GraphQL API
   - More difficult to spot(easier way to spot is to find a reference to query or mutation)
   - Usually endpoints like : `gql?q=`  , `graphql?q=`  , `g?q=` 
   - GraphQL is easy to enumerate
   - Also return JSON, but look weird when compared to REST
   - Practice : Hacker101 GraphQL CTF

    CREATE mutation {createPost(...)}
    
    READ query {post(id:"1"){id,...}

    UPDATE mutation {updatePost(...)}
  
    DELETE mutation {deletePost(...)}

### API Documentation
   - Sometimes Applications have their own API Documentation for devs 
   - Can disclose interesting endpoints/ used as Recon
   - Dorks : "`target.com Developer Docs`" , "`target.com API`"
   - Learn by Tutorials designed for Developers or Stack Overflow
---
## Testing API's
   #### 1) Information Disclosure
   - APIs can return more info. that they need to 
   #### 2) Authorization Issue
   - Sometimes Application might require Authorization but APIs does not..!!
   #### 3) Business Logic
   - Sometimes APIs do not validate the client-side
   #### 4) IDORs
   - API's are great resources of IDORS
   - Resources can be directly accessed via API, even if they shouldn't
   #### 5) XSS & CSRF
   - Can prove more impact with bugs like xss
   - By finding CSRF(where api does not ask for some kind of token)
   - Impact users accounts via API (eg. ATO)
---
### Testing for Information Disclosure
  - Sometimes an API might return ton of info but never display it, Or only display some of it
 #### 1) How to Test ?
   - Call the API
   - Check for hidden endpoints
---
### Testing for Authorization Issues
   - Difficult to test
   - Aim : Bypass an authorization process using API
   ##### 1) How to test ?
   - Understand the authorization process (API called, generated tokens, endpoints etc.)
   - Check to use API to generate tokens without login.
   - Check Another API endpoints to access functionality without needing a token.
---
### Testing for Business Logic Errors
   - Security issues that abuse the normal functionality
   - Very common in API as often the validation is only Client side
  ##### 1) How to Test ?
   - Make the number more larger or make it negative
   - Check to skip the payment process or API let us move on without paying.
   - Increase the quantity of product with same price.
   - Decrease the price to with same quantity
---
### Testing for IDORS
   - More Common and Easiest bugs in API
   ##### 1) How to Test ?
   - Remove cookie, does it still work ?
   - Replace your cookies with lower permission user account, does it still work ?
---
### Testing for XSS and CSRF
   ##### 1) XSS
   - In APIs, Sometimes Xss is filtered only on client side but not Server side
   - Update any public info as xss payload in APIs(so it will stored in backend)
   ##### 2) CSRF
   - Common in APIs, this allows an attacker to perform intended actions to a victim account.
   - Find API endpoint which does not require CSRF token.
---
### Others
   - API's aren't just vulnerable to these bugs, keep an eye out for
   ##### 1) SQL Injection (it's rare)
   - API often access the DB sometimes it may be SQL Injection
   ##### 2) Race Conditions
   - APIs can be excellent sources of Race-Conditions
   ##### 3) Memory Leaks
   - Some times special characters like null bytes to get an API to spit out the memory
---
### Taking Notes
   - Note taking is extremely important
   - Test each and every endpoints and note down weird things you notice
   - Consider a spreadsheet
        - Especially if you are testing a large application for IDORS
--- 
PS:
##### - Get comfortable with APIs
##### - API CTFs :

   ##### 1) For GraphQL
   - Hacker101 GraphQL levels

   ##### 2) For RESTful APIs
   - Build you own application
    
#### RESOURCES
    
- Read medium Articles or Twitter
- Hackerone Hacktivity
- Youtube Videos
