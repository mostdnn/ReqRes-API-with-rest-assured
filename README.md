# Rest Assured API Testing Framework

## Overview
This repository contains a Rest Assured API testing framework designed to test RESTful web services. The framework uses TestNG for test management and Maven for dependency management. Allure Reports is integrated for visual reporting, and the framework supports Data-Driven Testing using external data sources such as Excel and CSV.
## Key Features:
Rest Assured for API testing
TestNG for test execution and reporting
Allure Reports for interactive, visual test reports
Data-Driven Testing with TestNG DataProvider or external data files (Excel, CSV)
Maven for dependency management and build automation
Page Object Model (POM) structure for better maintainability and scalability

![Test Framework Architecture](assets/framework-architecture.png)

## Prerequisites
Before you begin, ensure that you have the following installed:
Java JDK 8+
Maven (for managing dependencies and building the project)
IntelliJ IDEA (or your preferred Java IDE)
Allure Commandline (for generating Allure reports)
Rest Assured libraries
TestNG and Allure TestNG Adapter dependencies

## Project Structure
```bash
├── pom.xml               # Maven project file
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── yourcompany
│   │               └── testautomation
│   │                   ├── pages       # Page Object classes
│   │                   ├── tests       # TestNG classes
│   │                   └── utils       # Utility classes
│   └── resources
│       └── config.properties  # Configuration file
├── target                # Allure and test output
└── README.md             # Project documentation

How to Run Tests
Run from IntelliJ:
Right-click on the Test class or TestNG.xml file and select Run.
Run from Command Line:
bash

mvn test
Allure Reports
After running the tests, generate the Allure report by using the following command:

bash
allure serve target/allure-results


"Conclusion"

This Rest Assured API testing framework is a powerful and flexible solution for automating API tests. By leveraging TestNG for test execution and Allure Reports for interactive reporting, it provides a comprehensive and maintainable testing solution for RESTful web services. The framework supports Data-Driven Testing for running tests with multiple data sets and integrates easily with popular tools like Maven and IntelliJ IDEA.


