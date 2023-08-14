##### [REFERENCE](https://www.apisecuniversity.com/courses/api-security-fundamentals)
### What are APIs ?? 
   1) An API is essentially a set of rules and protocols that define how two software applications should interact with each other. It allows one application to access the functionality or data of another application in a controlled and standardized way.

   2) In simple lanuage, An API is a way for two applications to talk to each other. It's like a waiter who takes requests from one application (the customer) and passes them on to another application (the kitchen).

   - Example, let's say you have a website that needs to display the weather forecast. Instead of creating a weather forecasting system from scratch, you can use an API provided by a weather service. Your website sends a request to the weather service API asking for the weather forecast for a particular location, and the API sends back the relevant information.

### Why should organizations focus on API security?
  
   1) Majority of Internet traffic is API driven.
   
   2) APIs have historically been excluded from security testing.
   
   3) APIs are primary targets for attacks.
   
   4) Privacy and security regulations require API security.

### Why are attackers targeting APIs? 

   1) API kill-chain is much simpler than classic attacks  
   
   2) APIs deal with data that is valuable to adversaries
   
   3) APIs are used in most applications 
   
   4) APIs frequently have limited security testing

### Which channels are sensitive to API attacks?

   1) Private APIs(used for company internal network)

   2) Public APIs(used for public/users data)

   3) Mobile APIs(Mobile app allow users to order online food)

   4) Web APIs(web application that provides real-time stock market information.)
---
---
## Real-World Breaches due to API Misconfigurations   
   
#### 1) COINBASE : coinbase is a crypto market trading platform.
##### Case : [_Broken Object Level Authorization_] 

   - A security researcher discovered a security flaw in coinbase where as an attacker he could sell crypto that he did not own. he rewarded with 250,000 USD

   - So he simply see the API-call b/w frontend and backend by sniff and reverse-engineering, where he see 4 parameters passing in the request and he manipulated one of the parameter.
			   
    ` product_id: "ETH-EUR"
	  side: "SELL"
	  source_account_id: "some-random-id"
	  target_account_id: "some-random-id"`

   - He manipulated `source_account_id` to someone else and able to sell crypto that he did not own.
	    
   - Company quickly shut-down for some time and fix the flaw.

#### 2) USPS : United States Postal Services.
##### Case: [_Broken Object Level Authorization_]

   - An attacker could setting up an account and authenticating, once the attacker is in, then

   - He is able to see any users *_`60 million`_* info. in the system

   - The bug is pretty simple that the application did not verify user authorization.

#### 3) PELOTON : American Exercise equipment company.
##### Case: [_Broken Object Level Authorization_] [_Broken Authentication_]

   - The API is exposed to public, API give users details with no authentication
   
   - *_`4 Million`_* accounts details exposed(including Joe Biden), Also including private accounts
   
   - By adding Authentication the bug was fixed but 
   
   - Hackers could still access all records and data by just need to authenticate.

#### 4) VENMO : Payment platform 
##### Case: [_Broken Object Level Authorization_] [_Broken Object property level authorization_] [_Unrestricted resource consumption_]

   - The application presented live feed of transactions[like 20-30] on the main page.

   - Researcher sniff the traffic and identified API calls

   - Then he wrote 20-line of script, using 2 IP, and able to pull *_`115,000`_* transactions/day even with rate limiting in place

   - API returned all transactions details, *_`207 Million`_* transactions were Harvested

#### 5) INSTAGRAM : Social-Media Platform    

   - Account has `reset-password` functionality that require 6 digit code. 

   - Researcher found API to submit reset code.

   - Rate-limit to guess code is 200 per IP

   - Researcher demonstrate that he could rotate through 5000 IPs in seconds and able to takeover anyone's account.

#### 6) BUMBLE : Dating application 
##### Case: [_Broken Object Level Authorization_] [_Broken Authentication_] [_Broken Function Level Authorization_] 

   - API permitted access to *_`95 Million`_* users account details without authentication

   - Incremental user IDs are easy to guess that's why it allowed easy scraping of entire database.

   - It also give more details and functionality to attacker, like an attacker could know exact location and also get paid features without proper privileges also able to delete anyone's account...etc.

#### 7) T-MOBILE : American Tele-Communication Company 
##### Case : [_Broken Authentication_]    

   - Exact case is not disclosed yet.

   - But an attacker was able to obtain data through a single API without Authorization.

#### 8) OPTUS : Australian Tele-Communication company 
##### Case: [_Broken Object Level Authorization_] [_Broken Object Property Level Authorization_] [_Unrestricted Resource consumption_]

   - API endpoint access with no authentication required

   - Attacker harvested *_`9.8 Million`_* users details including driver-license,medicare-ID,name,phone-no.,emails ..etc

   - Then they ransom the data and ask company for 1 Million USD , they also put some sort of sample on Dark-Web.

 #### 9) EXPERIAN : Credit reporting agency 
 ##### Case: [_Broken Object Level Authorization_] [_Broken Object Parameter Authorization_] [_Improper Inventory Management_]

   - Experian Partner site offered loan eligibility feature

   - and this feature used API to automate credit score lookup, 

   - so researcher sniff the API calls and try to direclty call the API and he found that

   - API accessible with no authentication required

   - So the attacker just need the name,address & any value of DOB to get anyone's credit records. attacker can also put 0 in DOB to retreive same data.
---
##### What are examples of exposures due to API vulnerabilities?

   1) Reputational Damage
   2) Loss of sensitive data.
   3) Financial Ransom
   4) Fraudulent Transactions

##### What types of vulnerabilities are common in these breach examples?

   1) Unauthorized access to users data
   2) Lack of authentication to sensitive API endpoints
   3) High Volume data Harvesting

##### How can attackers target web/mobile application APIs?


   1) Attackers can watch (“sniff”) API traffic between UIs and backend
   2) Attackers can attempt to obtain resources of other users
   3) Attackers can guess API endpoints and find undocumented capabilities
   4) Attackers can gain access via brute-forcing credentials
