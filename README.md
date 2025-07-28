PROJECT NAME: Contact List - API Testing (Postman)

DESCRIPTION:
This Postman project automates REST API testing for the “Thinking Tester Contact List” app. 
It covers both positive and negative flows including token generation, contact creation, update, retrieval, and deletion.
It uses environment variables, dynamic scripting, and chained requests.

---------------------------------------------------------------
TOOLS USED:

- Postman (v10 or higher)
- Postman Collection Runner
- Test Scripts with pm.test
- Environment variables
- Pre-request scripts

---------------------------------------------------------------
FOLDER & COLLECTION SETUP:

1. Postman Collection Name: Testers_Contact_Modules

2. Subfolders:
   - Positive Test Flow
       - POST Create Contact
       - GET Contact by ID
       - PUT Update Contact
       - GET Contact by ID (Post update validation)
       - DELETE Contact
       - GET Contact (To confirm deletion)
   - Negative Test Flow
       - POST Create Contact (Missing required fields)
       - GET Contact with invalid ID
       - PUT Update Contact with empty fields
       - POST Token (Invalid login)

3. Postman Environment File:
   - base_url: https://thinking-tester-contact-list.herokuapp.com
   - token: {{automatically generated and stored in login call}}
   - contact_id: {{saved in test script from create call}}

---------------------------------------------------------------
API WORKFLOW:

1. POST /users/login 
   - Body: { email, password }
   - Stores token in environment variable

2. POST /contacts
   - Creates a contact using test data
   - Stores contact ID in environment

3. GET /contacts/:id
   - Validates if contact was created/updated

4. PUT /contacts/:id
   - Updates contact fields

5. DELETE /contacts/:id
   - Deletes the created contact

6. GET /contacts/:id (again)
   - Validates deletion (404 expected)

---------------------------------------------------------------
NEGATIVE TESTS:

1. Create contact with missing fields
2. Invalid email format
3. Update contact with empty JSON
4. Try fetching contact with fake or deleted ID
5. Try generating token with wrong password

---------------------------------------------------------------
RUNNING INSTRUCTIONS:

1. Import the Postman collection
2. Import environment variables JSON
3. Set environment: Testers_Contact_Env
4. Run entire folder using Collection Runner
5. View pass/fail and logs in Test Results

---------------------------------------------------------------
VALIDATION STRATEGIES:

- Check response status code (e.g. 200, 201, 400, 404)
- Check response body fields using `pm.expect`
- Store response data using `pm.environment.set()`
- Reuse tokens and contact IDs across calls

---------------------------------------------------------------
AUTHOR:
Name: Enay Kumar Reddy
Contact: chenchuenay97@gmail.com
Https://ae.linkedin.com/in/enaykumar
