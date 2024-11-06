Rest Assured API Testing Framework
This repository contains a Rest Assured API testing framework designed to test RESTful web services. The framework uses TestNG for test management and Maven for dependency management. Allure Reports is integrated for visual reporting, and the framework supports Data-Driven Testing using external data sources such as Excel and CSV.

Key Features:
Rest Assured for API testing
TestNG for test execution and reporting
Allure Reports for interactive, visual test reports
Data-Driven Testing with TestNG DataProvider or external data files (Excel, CSV)
Maven for dependency management and build automation
Page Object Model (POM) structure for better maintainability and scalability
Prerequisites
Before you begin, ensure the following tools and libraries are installed:

Java JDK 8+
Maven (for managing dependencies and building the project)
IntelliJ IDEA (or your preferred Java IDE)
Allure Commandline (for generating Allure reports)
Rest Assured libraries
TestNG and Allure TestNG Adapter dependencies
Project Setup
Clone the Repository:
Clone the repository to your local machine using Git:

bash
نسخ الكود
git clone <repository_url>
cd <project_directory>
Import the Project into IntelliJ IDEA:
Open IntelliJ IDEA.
Go to File > Open and select the project directory.
IntelliJ IDEA will automatically import the project if Maven is used.
Install Dependencies:
The project uses Maven to manage dependencies. To install the required libraries (like Rest Assured, TestNG, and Allure), run the following command:

bash
نسخ الكود
mvn clean install
Configuration Files:
You can configure environment-specific details (e.g., base URL, authentication details) in the src/main/resources/config.properties file.

Example Configuration (config.properties):
properties
نسخ الكود
baseUrl = https://api.example.com
authToken = <your_api_token>
Project Structure
bash
نسخ الكود
├── pom.xml                    # Maven project file with dependencies
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── yourcompany
│   │               └── apitesting
│   │                   ├── tests        # Test classes (TestNG)
│   │                   ├── utils        # Utility classes
│   │                   └── config       # Config classes (Base Class, etc.)
│   └── resources
│       ├── testdata            # Data files (Excel, CSV)
│       └── config.properties   # Configuration file for environment setup
├── target                     # Allure and test output will be stored here
└── README.md                  # Project documentation
Framework Components
Rest Assured
Rest Assured is used to perform API tests, handle HTTP requests (GET, POST, PUT, DELETE), and validate responses. Here's an example of a simple GET request test:

java
نسخ الكود
@Test
public void getUserDetailsTest() {
    given()
        .baseUri("https://api.example.com")
        .header("Authorization", "Bearer " + authToken)
    .when()
        .get("/user/12345")
    .then()
        .statusCode(200)
        .body("data.id", equalTo(12345))
        .body("data.name", equalTo("John Doe"));
}
TestNG
TestNG is used for test execution and reporting. Each test is defined as a TestNG test method, and you can use annotations like @BeforeMethod, @AfterMethod, @Test, etc., for setting up and cleaning up before/after tests.

Example TestNG Setup:
java
نسخ الكود
@BeforeClass
public void setUp() {
    // Setup code (e.g., create authentication tokens, set up base URL)
}

@Test
public void getUserDetails() {
    // API testing code using Rest Assured
}

@AfterClass
public void tearDown() {
    // Cleanup code (e.g., clear tokens, reset configurations)
}
Data-Driven Testing
The framework supports Data-Driven Testing using TestNG's DataProvider annotation. You can feed different sets of input data to your tests from external files (e.g., CSV, Excel).

Example using TestNG DataProvider:
java
نسخ الكود
@DataProvider(name = "userData")
public Object[][] userData() {
    return new Object[][] {
        { "user1", "password1" },
        { "user2", "password2" }
    };
}

@Test(dataProvider = "userData")
public void loginTest(String username, String password) {
    given()
        .param("username", username)
        .param("password", password)
    .when()
        .post("/login")
    .then()
        .statusCode(200);
}
Allure Reports
Allure is integrated to provide detailed and visually appealing test reports. You can generate the Allure report after test execution using the following steps:

After running tests, generate the Allure report with:
bash
نسخ الكود
allure serve target/allure-results
This command will open the report in your default browser, where you can view the results, including test status, logs, and screenshots.
Running the Tests
Run from IntelliJ IDEA:
Right-click on the Test class or TestNG.xml file.
Select Run.
Run from Command Line:
To run the tests via Maven, use the following command:

bash
نسخ الكود
mvn test
This will execute all the tests in the project and generate the test reports in the target directory.

Allure Reporting
After running the tests, you can generate and view the Allure report by executing the following:

bash
نسخ الكود
allure serve target/allure-results
This will open the Allure report in the browser, allowing you to explore detailed test results, logs, and screenshots.

Dependencies in pom.xml
Here are some of the key dependencies included in the pom.xml:

xml
نسخ الكود
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>rest-assured</artifactId>
    <version>4.4.0</version>
    <scope>test</scope>
</dependency>

<!-- TestNG -->
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.4.0</version>
    <scope>test</scope>
</dependency>

<!-- Allure TestNG Adapter -->
<dependency>
    <groupId>io.qameta.allure</groupId>
    <artifactId>allure-testng</artifactId>
    <version>2.16.1</version>
    <scope>test</scope>
</dependency>

<!-- Apache POI (for Data-Driven Testing) -->
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi</artifactId>
    <version>5.2.3</version>
</dependency>
Conclusion
This Rest Assured API testing framework is a powerful and flexible solution for automating API tests. By leveraging TestNG for test execution and Allure Reports for interactive reporting, it provides a comprehensive and maintainable testing solution for RESTful web services. The framework supports Data-Driven Testing for running tests with multiple data sets and integrates easily with popular tools like Maven and IntelliJ IDEA.
