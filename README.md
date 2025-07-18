<div align="center">

# 🧪 JSONPlaceholder API Tests

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![JSON](https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white)
![API Testing](https://img.shields.io/badge/API%20Testing-4CAF50?style=for-the-badge&logo=checkmarx&logoColor=white)

*Automated test collection for REST API validation using JSONPlaceholder*

[Get Started](#-installation) • [Documentation](#-main-tests-implemented) • [Usage](#-how-to-use) • [License](#-license)

</div>

---

## 📋 Overview

This project demonstrates expertise in **API contract validation**, **automated test organization**, and **best practices** for versioning and collaboration via GitHub. The test collection was developed for the **JSONPlaceholder** public API, validating all main endpoints with comprehensive test scripts.

## 🎯 Objectives

- Demonstrate proficiency in API testing using Postman
- Implement rigorous contract validation (Schema Validation)
- Organize tests in a structured and reusable way
- Apply test automation best practices
- Properly document tests and processes

## 🌐 API Used

**JSONPlaceholder**: https://jsonplaceholder.typicode.com/

A free REST API for testing and prototyping, which simulates resources such as:
- Posts (100 items)
- Comments (500 items)
- Users (10 items)
- Albums (100 items)
- Photos (5000 items)
- Todos (200 items)

## 📁 Project Structure

```
api-test-JSONPlaceholder/
├── collections/
│   ├── jsonplaceholder-tests.postman_collection.json
│   └── jsonplaceholder-environment.postman_environment.json
├── schemas/
│   ├── post-schema.json
│   ├── user-schema.json
│   └── comment-schema.json
├── docs/
├── screenshots/
└── README.md
```

## 🚀 How to Use

### 1. Import into Postman

1. **Download the files**:
   - `jsonplaceholder-tests.postman_collection.json`
   - `jsonplaceholder-environment.postman_environment.json`

2. **Import into Postman**:
   - Open Postman
   - Click "Import"
   - Select the downloaded files
   - Confirm the import

3. **Configure the environment**:
   - Select the "JSONPlaceholder Environment" environment
   - Verify that the variables are configured correctly

### 2. Run the Tests

#### Individual Execution
- Navigate through the folders organized by resource
- Execute individual requests
- View test results in the "Test Results" tab

#### Batch Execution
- Click on the collection name "JSONPlaceholder Tests"
- Click "Run Collection"
- Configure execution options (delay, iterations)
- Execute and view the complete report

## 🧪 Main Tests Implemented

### 📝 Posts
- **GET All Posts**: Validates structure, quantity, and required fields
- **GET Single Post**: Verifies specific data and integrity
- **POST Create Post**: Tests creation with response validation
- **PUT Update Post**: Validates complete update
- **DELETE Post**: Confirms successful removal

### 💬 Comments
- **GET All Comments**: Validates structure and email format
- **GET Comments by Post**: Tests post-comment relationship

### 👥 Users
- **GET All Users**: Validates complex structure (address, company)
- **GET Single User**: Verifies complete personal data
- **GET User Posts**: Tests user-posts relationship

### 🖼️ Albums & Photos
- **GET All Albums**: Validates basic structure
- **GET Album Photos**: Tests URLs and relationships

### ✅ Todos
- **GET All Todos**: Validates structure and data types
- **GET User Todos**: Tests user-tasks relationship

### ❌ Error Handling
- **404 Errors**: Tests non-existent resources
- **Invalid Endpoints**: Validates error handling

## 🔍 Implemented Validations

### ✅ Basic Validations
- **Status Codes**: 200, 201, 404 as expected
- **Response Time**: Maximum of 1000ms for operations
- **Content-Type**: JSON headers verification
- **Required Fields**: Presence of essential properties

### 🔧 Advanced Validations
- **Schema Validation**: Using integrated `tv4` library
- **Data Types**: Validation of types (string, number, boolean)
- **Format Validation**: Emails, URLs, complex structures
- **Relationship Validation**: Correct relationship IDs

### 📊 Business Validations
- **Array Lengths**: Expected number of items
- **Data Integrity**: Consistency between related resources
- **Field Constraints**: Minimum values, specific formats

## 🎯 Contract Validation (Schema Validation)

### Implementation
Schema validation is implemented directly in Postman test scripts using the `tv4` library (Tiny Validator for JSON Schema v4).

### Defined Schemas
- **Post Schema**: Validates post structure
- **User Schema**: Validates complete user data
- **Comment Schema**: Validates comment structure

### Usage Example
```javascript
const schema = {
    \"type\": \"object\",
    \"properties\": {
        \"id\": {\"type\": \"number\"},
        \"title\": {\"type\": \"string\"},
        \"body\": {\"type\": \"string\"},
        \"userId\": {\"type\": \"number\"}
    },
    \"required\": [\"id\", \"title\", \"body\", \"userId\"]
};

pm.test(\"Schema is valid\", function () {
    const jsonData = pm.response.json();
    pm.expect(tv4.validate(jsonData, schema)).to.be.true;
});
```

## 📋 Environment Variables

| Variable | Value | Description |
|----------|-------|-------------|
| `base_url` | `https://jsonplaceholder.typicode.com` | API base URL |
| `default_user_id` | `1` | Default user ID |
| `default_post_id` | `1` | Default post ID |
| `default_album_id` | `1` | Default album ID |
| `test_timeout` | `1000` | Test timeout (ms) |

## 📚 Embedded Documentation

The collection includes embedded documentation in Postman with:
- **Folder descriptions**: Purpose and context of tests
- **Request descriptions**: Details about each endpoint
- **Usage examples**: How to execute and interpret results
- **Documented variables**: Explanation of all variables used

### Accessing Documentation
1. In Postman, click on the "JSONPlaceholder Tests" collection
2. Click on the "Documentation" tab
3. Navigate through the structured documentation

## 🏆 Key Highlights

### ✨ Organization
- **Hierarchical structure**: Folders organized by resource
- **Clear naming**: Descriptive and standardized names
- **Separation of concerns**: Each folder with specific purpose

### 🔬 Test Quality
- **Comprehensive coverage**: All main endpoints covered
- **Multiple validations**: Multiple checks per request
- **Error cases**: Tests for failure scenarios

### 🔧 Automation
- **Reusable scripts**: Consistent test logic
- **Dynamic variables**: Data shared between tests
- **Batch execution**: Ability to run the entire suite

### 📈 Reports
- **Detailed results**: Complete information about each test
- **Performance metrics**: Response time and statistics
- **Data export**: Exportable results for analysis

## 🛠️ Technologies and Tools

- **Postman**: Main tool for API testing
- **tv4**: Library for JSON schema validation
- **JSONPlaceholder**: Public API for testing
- **JSON Schema**: Standard for contract validation

## 📊 Project Statistics

- **Total Requests**: 20+ tested endpoints
- **Validations per Request**: 5-10 tests per endpoint
- **Resource Coverage**: 6 different resources (Posts, Comments, Users, Albums, Photos, Todos)
- **Operation Types**: GET, POST, PUT, DELETE
- **Error Scenarios**: Validation of 404 cases and invalid endpoints

## 🎓 Learnings and Best Practices

### ✅ Implemented
- **Structured organization** of tests by resource
- **Rigorous validation** of API contracts
- **Complete automation** with JavaScript scripts
- **Integrated documentation** within Postman itself
- **Code reusability** with environment variables
- **Error scenario handling**

### 🔄 Development Process
1. **API Analysis**: Study of JSONPlaceholder documentation
2. **Planning**: Definition of test structure
3. **Implementation**: Creation of requests and scripts
4. **Validation**: Testing and refinement of validations
5. **Documentation**: Creation of complete documentation
6. **Versioning**: Organization for collaboration

## 🤝 Contribution

This project was developed as a demonstration of skills in:
- **Automated API testing**
- **Contract validation**
- **Test project organization**
- **Technical documentation**
- **Development best practices**

## 📄 License

This project is under the MIT license. See the [LICENSE](LICENSE) file for more details.

## 👤 Author

<div align="center">

**Anthony Coelho**

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/anthonycdp)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anthonycoelhoqae/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:anthonycoelho.dp@hotmail.com)

*QA Engineer specialized in performance testing and automation*

</div>

---

<div align="center">

### ⭐ If this project was helpful to you, consider giving it a star!

### 🤝 Contributions are welcome!

**Version**: 1.0.0

</div>