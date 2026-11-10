# 🛒 API Testing – SmartGrocery (Postman Project)
This project demonstrates a complete API testing workflow for the SmartGrocery REST API using **Postman and Newman CLI**. It includes CRUD operations, automated test 
scripts, assertions, and detailed reports, making it a clean, portfolio-ready QA project.

# 📚 Project Overview

The main goal of this project is to validate the SmartGrocery API, which manages products and related operations. The testing ensures that the API is reliable, 
secure, and meets functional requirements.

### This project covers:

- CRUD validation for grocery products (`GET, POST, PUT, DELETE`)

- API response `verification` (status codes, headers, field values, data types, response body, and schema)

- Writing and running tests using `Postman`

- Automated testing with `Newman`

- Positive and negative test scenarios

- Maintaining a professional QA test case document

- HTML reporting for execution summary

# 🚀 Features Tested <br>
Set the base URL once (in Postman collection or environment) and use this `{{BaseURL}}` prefix before every endpoint.

| Feature               | Method        | Endpoint                 |
|-----------------------|---------------|--------------------------|
| Get All Products      | GET           | /products                |
| Get Single Product    | GET           | /products/:id            |
| Add New Product       | POST          | /products                |
| Update Product        | PUT           | /products/:id            |
| Delete Product        | DELETE        | /products/:id            |
| Error Handling        | GET/POST/DELETE | Invalid/missing inputs |
| Get All Customers     | GET           | /customers               |
| Get Single Customer   | GET           | /customers/:id           |
| Add New Customer      | POST          | /customers               |
| Update Customer       | PUT           | /customers/:id           |
| Delete Customer       | DELETE        | /customers/:id           |
| Get All Orders        | GET           | /orders                  |
| Get Single Order      | GET           | /orders/:id              |
| Add New Order         | POST          | /orders                  |
| Update Order          | PUT           | /orders/:id              |
| Delete Order          | DELETE        | /orders/:id              |
| Error Handling        | GET/POST/DELETE | Invalid/missing inputs |

# 📁 Folder Structure
API_Testing_SmartGrocery_Postman/

├── TestCases/ <br>
│                     └── SmartGrocery_Test_Cases.xlsx                        
├── SmartGrocery_API.postman_collection.json                     
├── newman-report.html                                      
├── grocery_data.json                                            
├── README.md                                               

# 🧰 Tools & Technologies
- ✅ Postman – API testing and automation

- ✅ Newman – CLI execution and reporting

- ✅ Assertions(Postman Tests) – JS validation logic

- ✅ JSON Schema – For validating the structure of responses

- ✅ JSON Server – Local API for testing

- ✅ Excel – Manual test case documentation

- ✅ htmlextra Reporter – Beautiful HTML execution reports

# ✨ Sample Assertions (Postman Tests)
-  `pm.expect(pm.response.code).to.be.oneOf([200, 201]);`
  
-  `pm.expect(pm.response.headers.get("Content-Type")).to.eql("application/json");`

-   `pm.expect(jsonData.name).to.be.a("string");`

-    `pm.expect(product).to.have.property("price");`
  
-  `pm.expect(jsonData.email).to.match(/^[^\s@]+@[^\s@]+\.[^\s@]+$/);`
  
-  `pm.expect(tv4.validate(jsonData, schema)).to.be.true;`

# 📝 Manual Test Case Examples <br>

| TCID        | Request Type | Endpoint                                  | Expected Status | Expected Result                              |
|-------------|--------------|-------------------------------------------|----------------|----------------------------------------------|
| TC_PROD_01  | GET          | /products                                 | 200            | List of all products                         |
| TC_PROD_02  | GET          | /products?category=Vegetables&_limit=3    | 200            | Returns maximum 3 products filtered by category |
| TC_PROD_03  | GET          | /products/10000                           | 404            | Product not found                            |
| TC_PROD_07  | POST         | /products                                 | 400            | Name is required                             |
| TC_ORD_05   | GET          | /orders/3                                 | 200            | Order details are updated successfully       |
| TC_CUST_03  | GET          | /customers/1000                           | 404            | Returns 404 for non-existent customer        |



📌 Full test cases are inside `Test Cases/SmartGrocery_Test_Cases.xlsx` <br>
# 📊 HTML Report Preview

The Newman HTML Report (newman-report.html) includes:

- Pass/fail summary

- Status code breakdown

- Request/response logs

- Assertion counts

- Response time stats

### Generated HTML Report using:
```bash
newman run SmartGrocery_API.postman_collection.json --reporters cli,htmlextra --reporter-htmlextra-export newman-report.html --env-var "BaseURL=http://localhost:3000"
```


# 💻 How to Run
1️⃣ Start the API server

```bash
json-server --watch grocery_data.json --port 3000
```

2️⃣ Run the collection with Newman:<br>
```bash
newman run SmartGrocery_API.postman_collection.json --env-var "BaseURL=http://localhost:3000"
```
 
