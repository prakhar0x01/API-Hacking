
##### DATE : [27-04-2023]
##### [REFERENCE](https://www.apisecuniversity.com/courses/api-security-fundamentals)


## 3 Pillars of API Security   
#### 1) Governance
   - Governance refers to the policies and procedures that organizations put in place to ensure that APIs are designed, developed, and deployed securely. This can include things like establishing security standards and best practices, conducting security reviews, and enforcing compliance with relevant regulations and industry standards.

   - Consistency : The main goal/benefit of the governance is establish consistency. It's consistency in how your APIs get developed, how they get deployed, how they get tested and everything else.

   - Setting Expectations : Setting expectations for your engineering team - what is required? What are those documentation requirements and authentication policies and, and versioning and so forth.

   - Enforcing Securities : Enforcing security to make sure that nothing moves into production that hasn't gone through the same level of security assessment and vetting.

   ##### Know Your APIs
      
   - Get full inventory APIs
      - Purpose of creation, who is the owner, Documentation

      - Standardize and enforce API deployment process
         - Existence of `shadow/rouge` APIs sign of weak governance
         - APIs only deployed in approved ways, with proper validation
         - Enforce governance at Gateway, Marketplace

      - Mandate API Documentations
         - Make sure APIs are consistent & reusable
         - Define documentation requirements

      - Create API Development Standards
         - Style guides, authentication requirements, versioning, PII tracking.                

   - You want to have a comprehensive view across all your APIs. You want to know your infrastructure, the app architecture, the containers and virtual machines, the databases being connected to the network infrastructure. Have a good understanding of how everything interconnects.

   - Know Your Risks(Threat modeling)

      - Identify : APIs, data, access path --> potential threats

      - Assess : Vulnerabilities, logic flaws, access controls, 3rd party risk

      - Probability : Examine the likelihood of an attack

      - Impact : Understand the damage, loss, consequences of an attack

      - Mitigation : Develop a plan to address the risk

   - Documentation : OpenAPI Specification(aka Swagger)

      - Not optional
      - Industry standard for REST APIs
      - Machine-readable(YAML,JSON)
      - Aids development, 3rd party integration & Security Testing
      - Manually or Auto-genreated
      - Control what's public v/s private
      - Retire old Documentation -> huge threat vector 
      - Defines API capability(contract)
            - Title, description, version
            - Base-URLs, Endpoints, paths 
            - Requests, response & payloads
            - Authentication requirements
            - Parameters, data-types and HTTP methods1

   - It's absolutely crucial to be documenting your APIs properly. It's not only important for security, it's also important for development and for enabling the use of those APIs.  

   - Design Guides: Promote Governance, Consistency   
      - Authentication - Type(Basic,token,certificate), how to implement
      
      - Authorization - Who has access to what, where enforce
      
      - Naming Conventions - URIs as nouns, Menthods as verbs, pluralization, hierarchy, case , language, no jargon/abbriviations
      
      - Error codes - Status-code, reference ID, human readable meaages
      
      - Versioning - When to increment, when not, types of version
      
      - Units, formats, Standards - DAte/time formats, timezones



#### 2) Testing
- Testing refers to the process of evaluating the security of APIs to identify vulnerabilities and weaknesses. This can include things like penetration testing, vulnerability scanning, and code review. Regular testing helps organizations identify and address security issues before they can be exploited by attackers.

   1) Testing refers to the process of evaluating the security of APIs to identify security flaws and weaknesses.
   
   2) Common types of API security testing include penetration testing, vulnerability scanning, and code review.

   3) Historically, application testing has focused on the UI layer itself, whether it's web app or a mobile app. But what attackers are doing is simply going around that, right to the API itself.

   4) The type of testing and coverage that we need are broken into these three categories...

      - API Security
           - Unsecured Endpoints
           - Authentication exploits
           - Enumeration
           - App DOS, Rate Limit
           - Missing TLS, SSL issues
           - Injection, fuzzing, input validation
           - SSRF, server property leaks

      - Data Security
           - Access Control
           - Excessive data exposure
           - Sensitive data exposure
           - File, directory exposed
           - Encryption at rest
           - Data exfiltration

      - Business Logic
           - Cross-account access
           - API function abuse
           - Role-based access control
           - Pen-testing           

#### 3) Monitoring

- Monitoring refers to the ongoing observation and analysis of API activity to detect potential security issues or anomalies. This can include things like tracking access logs, monitoring user behavior, and implementing intrusion detection and prevention systems. Regular monitoring helps organizations identify and respond to security incidents in a timely manner.

-  This includes 3 methods of protection : 
      - Runtime Protection
           - Policy enforcement
           - Authentication
           - Traffic filtering

      - Threat Detection
           - Fraudulent traffic
           - Distributed attacks
           - Incident response

      - Control Validation
           - Verify API controls
           - Uncover anomalies

  - Monitoring approaches
      - Proactive : Blocking
           - API Gateway
           - Web App Firewall

      - Reactive : Alerting
           - Logging, SIEM
           - Runtime API Threat Management

  -  Benefits of API Discovery 
      - Monitoring can aid API inventory efforts
           - Identify API endpoints in use
           - Discover undocumented/unknown APIs

      - Comprehensive discovery requires more source
           - API Gateway, Web-App Firewall
           - Code Repository
           - Application testing, crawling

      - Reliance on traffic based-discovery missed
           - Internal API traffic not observed by traffic analysis tool
           - Pre-production APIs
           - Unexercised endpoints

  - Limitations of API Discovery
      - Difficult to get full visibility
           - REquires sensors on every network segment

      - High false positives on threat detection
           - Live traffic contains limited context
           - Difficult to identify data access violation in real-time
           - API monitoring tools typically used in alert only

      - SaaS-based monitoring requires sharing traffic with 3rd parties
           - Privacy Concerns

           - Bandwidth requirements
      
      - Traffic blocking solutions can add latency
