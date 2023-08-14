##### [REFERENCE](https://www.apisecuniversity.com/courses/api-security-fundamentals)


## OWASP [Open Web Application Security Project] API Security Top-10

- API1   : Broken Object level Authoruzation
- API2   : Broken Authentication
- API3   : Broken Object Property
- API4   : Unrestricted Resource consumption
- API5   : Broken Fucntion Level Authorization
- API6   : Sever-Side Request Forgery
- API7   : Security Misconfigurations
- API8   : Lack of PRotection from Automated Threats
- API9   : Improper Assets Management
- API10 : Unsafe Consumption of APIs

#### API1 : Broken Object Level Authorization

   - APIs flaw that do not properly enforce authorization rules, allowing attackers to access or modify data they should not have access to. 

   - Ex. User A can allow to edit User B account without any user interaction

   - Ex. Normal user can CRUD(Create,Read,Update,Delete) admins information.

   - To prevent this, make sure to implement proper access control mechanisms, such as role-based access control and attribute-based access control.

#### API2 : Broken Authentication and Session Management

   - APIs that do not properly authenticate users or manage their sessions, allowing attackers to steal user credentials or take over user sessions

   - Ex. No captcha, No Rate-limit on login pages, Changing password without verification of valid tokens, Insecure Bruteforce IDs

   -  To prevent this, make sure to use strong authentication mechanisms such as multi-factor authentication, and enforce secure session management practices such as using secure cookies and token revocation.

#### API3 : Broken Object Property Level Authorization/Excessive Data Exposure

   - APIs that return more data than necessary, exposing sensitive information that should be kept confidential. 

   - Ex. User is able to set `/account/?account-type=premium`, User search only for name but the API respond with other info. such as email,address,ID etc.

   - To prevent this, API should use proper data minimization techniques, such as only returning the data that is necessary for the API's function.

#### API4 : Unrestricted Resource Consumption & Rate-Limiting.

   - APIs that do not properly limit the number of requests that can be made, allowing attackers to mass data retrieval and overload the system cause DOS attacks.

   - Ex. An attacker could flood an API with requests to slow down or crash the system. 

   - Ex. If application does not verify sessions, An attacker could retrieve huge amount of data by just manipulating the API calls coz there is no Rate-limit

#### API5 : Broken Function Level Authorization 

   - APIs that do not properly enforce authorization rules at the function level, allowing attackers to access or modify data they should not have access to.

   - Ex. Replace GET with PUT,DELETE , Modify parameters such as `?role=admin`, Setting account balance to $0.

   - To prevent this, make sure to implement proper function-level access control mechanisms, such as role-based access control and attribute-based access control.

#### API6 : SSRF(Server Side Request Forgery)/Mass Assignment

   - APIs that allow attackers to read/modify more data than intended by manipulating the API request.

   - Ex. API call have `url` input to make request to 3rd party server, an attacker could manipulate the `url` to `http://169.254.169.254/meta-data/iam/users/user_id/credentials` or `http://localhost:8443/admin/user/?edit=user_id`

   - Ex. API call have change `email` input, so an attacker just add another `user_id` paramter with another `email` and change other user email-id and takever anyone's account.

   - To prevent this, make sure to properly validate and sanitize API input, and only allow modification of the intended data.

#### API7 : Security Misconfigurations 

   - APIs that are not properly configured, leading to security vulnerabilities.

   - Ex. API may be using default or weak passwords, improper configured permissions, missing security patches or out-of date, mssing TLS , CORS policy missing

   - To prevent this, make sure to follow secure configuration practices, such as using strong passwords and encryption, and keeping software up-to-date with security patches.

#### API8 : Lack of Protection from Automated Threats

   - APIs that are not properly identify workflows.

   - Ex. Mass automated ticket pruchasing, High volume referral bonuses

   - To prevent this, API should identify critical business workflow, implement Runtime fraudulent traffic detection & control, setup automated testing of control mechanisms.

#### API9 : Improper Assets Management

   - APIs that do not properly manage assets such as keys, credentials, or tokens, leading to security vulnerabilities

   - API may store sensitive information in plaintext, old versions of APIs, Unpatched Endpoints with weaker security, Unneccessary exposed endpoints, API access via 3rd party sources.

   - To prevent this, Deploy/manage all API in Gateway, Define rules for versioning and retirement, store API keys encrypted.  

#### API10 : Unsafe Consumption of APIS

   - Exposure can occur via use of 3rd party APIs, which are generally trusted. However 3rd parties can be exploited, which can be used to attack APIs that rely upon them and lead to Data theft, breach, account-takeover.

   - Ex. API call input user address for verification, so an attacker inserts malicious address(`" DROP TABLES --`) data to validation site used by application and now when application validate data it get exploited. 

   - Ex. Attacker compromises 3rd party API causing it to repond with redirect to malicious site. application blindly follows redirects without validation this may lead to SSRF.

   - To prevent this, Application should properly validate user input and also Testing/validate 3rd party security controls.
 ---
##### What do "BOLA" attacks (OWASP #1) target?

    Inadequate/missing data access controls

##### What are examples of weak authentication?

    Weak Password Requirements
    Lack of bruteforce attack blocking
    Including token information in url

##### Which OWASP category addresses out-of-date API versions?

    Improper Assets/Inventory Management

##### If you have to share sensitive APIs with trusted 3rd parties:

    Do not trust any user input
    Only permit API traffic from approved IP/sources
    Require authentication for 3rd party access to your API
    Maintain an inventory of all 3rd party APIs used

##### Why is Broken Function Level Authorization so dangerous? 

    It can allow a user to escalate their privileges
    It can allow user to delete records
    It can allow a user to insert malicious data

##### What are examples of Security Misconfiguration?

    Missing Security Patches
    Uneccessary features enabled
    LAck of CORS poilicies implemented

##### What do attackers exploit with Improper Assets Management (OWASP #9)?

    Undocumented APIs
    Non-current API versions
    Retired, but still accessible, endpoints  


