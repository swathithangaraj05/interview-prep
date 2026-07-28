Self Intro
-----------
Good morning/afternoon.

My name is Swathi, and I have around 3 years of experience as a QA Engineer in both Manual and Automation Testing.

Currently, I am working at Capgemini, where I am involved in testing web applications across different domains such as airline booking and e-commerce.

In Manual Testing, I have experience in Functional Testing, Regression Testing, Smoke Testing, Integration Testing, End-to-End Testing, and Defect Management using JIRA. I am involved in requirement analysis, test scenario creation, test case execution, defect reporting, and validation.

On the Automation side, I have hands-on experience with Selenium WebDriver using Java. I have worked with TestNG, Cucumber BDD, Maven, Jenkins, Git, and the Page Object Model framework. I have automated critical business workflows and integrated test execution into CI/CD pipelines.

I also have experience in API Testing using Postman and Rest Assured, SQL for database validation, and basic Mobile Testing using Appium.

I have been working in Agile Scrum environments, actively participating in sprint planning, daily stand-ups, sprint reviews, and retrospectives.

Currently, I am looking for a challenging opportunity where I can further enhance my skills in both automation and quality engineering while contributing to the organization's success.

That's a brief introduction about myself.

## 1.What is SDLC?
SDLC stands for Software Development Life Cycle.
It is the complete process followed to develop software from the initial requirement to maintenance.
The phases include Requirement Gathering, Design, Development, Testing, Deployment, and Maintenance.
As a QA Engineer, my involvement usually starts from the requirement analysis phase, where I understand user stories and prepare test scenarios.

## 2.What is STLC?
STLC stands for Software Testing Life Cycle.
It is the testing process followed by the QA team.
The phases include Requirement Analysis, Test Planning, Test Case Design, Environment Setup, Test Execution, Defect Reporting, and Test Closure.
In my projects, after understanding the user stories, I prepared test cases, executed them, logged defects in JIRA, and verified the fixes before closing the sprint.

## 3.What is Smoke Testing?
Smoke Testing is the initial level of testing performed after receiving a new build.
Its purpose is to verify whether the critical functionalities of the application are working properly.
If the smoke test fails, we won't continue with further testing because the build is considered unstable.
For example, in the EasyJet application, we first checked whether users could log in, search for flights, and access the booking page before executing the complete regression suite.

## 4.What is Sanity Testing?
Sanity Testing is performed after a bug fix or a small change to verify that the specific functionality is working correctly.
It focuses only on the modified functionality.
For example, if the developer fixes a payment issue, I verify only the payment module instead of testing the entire application.

## 5.Difference between Smoke and Sanity Testing
Smoke Testing is performed on the entire application to verify whether the build is stable enough for testing.
Sanity Testing is performed after bug fixes to verify only the affected functionality.
In simple terms, Smoke Testing checks whether we can start testing, while Sanity Testing checks whether a specific fix is working.

## 6.What is Regression Testing?
Regression Testing ensures that existing functionalities are not affected after implementing new features or fixing defects.
Whenever developers make changes, there is a possibility that existing modules may break.
So we execute the regression suite before every release.
In my EasyJet project, even if developers modified only the payment module, we executed regression tests for login, flight search, booking, payment, and booking confirmation to ensure nothing else was impacted.

## 7.What is Functional Testing?
Functional Testing verifies whether each feature of the application behaves according to the business requirements.
Here we focus on validating the functionality rather than the internal code.
For example, in the Waitrose project, I verified functionalities like user registration, login, product search, adding items to the cart, checkout, payment, and order confirmation.

## 8.What is Retesting?
Retesting is performed to verify whether a previously reported defect has been fixed by the developer.
Unlike Regression Testing, Retesting focuses only on the failed test case.
For example, if I reported a bug where users couldn't able to login the application, after the fix, I would execute only the login
test case to confirm that the issue is resolved.

## 9.What is UAT?
UAT stands for User Acceptance Testing.
It is performed by business users or clients before the application is released to production.
The purpose is to confirm that the application meets business requirements and is ready for real users.

## 10.The developer fixed the payment bug. Which testing will you perform?
First, I'll perform Retesting to verify that the reported payment defect has been fixed. Then I'll perform Sanity Testing on the related payment functionalities, such as different payment methods and confirmation screens, to ensure the module is stable. Finally, before the release, I'll execute the Regression Testing suite to make sure the code changes haven't impacted other areas of the application.

## 11.What is a Test Case?
A test case is a document that contains the preconditions, test steps, test data, expected result, and actual result to verify whether a specific functionality is working correctly.
Before test execution, I prepare test cases based on the business requirements and user stories to ensure all possible scenarios, including positive, negative, and edge cases, are covered.
For example, in the EasyJet project, while testing the flight booking module, I created test cases for valid booking, invalid passenger details, payment failure, seat selection, and booking confirmation to ensure complete test coverage.

Example of a test case:
-----------------------
For the Login functionality, one test case is:
Username: Valid
Password: Valid
Click Login
Expected Result: User should be successfully logged into the application.

## 12.What are the components of a test case?
A test case generally includes Test Case ID, Test Scenario, Test case Description, Test Data, Test case priority, Test Steps Description, Expected Result, Actual Result, Bug id, Status, and Comments.

## 13.What is a Test Scenario?
A Test Scenario is a high-level description of what needs to be tested. It defines the functionality that should be validated without describing the detailed execution steps.
Based on each test scenario, we create multiple test cases to cover different conditions.
For example, 'Verify Flight Booking' is a test scenario. Under this scenario, I create multiple test cases such as booking with valid details, invalid passenger details, payment failure, booking with promo code, and booking confirmation.

## 14.Difference Between Test Scenario and Test Case
A Test Scenario is a high-level statement describing what needs to be tested, whereas a Test Case contains detailed steps, test data, and expected results for validating that functionality.
One Test Scenario can have multiple Test Cases.
For example, 'Verify Login Functionality' is a Test Scenario. Under that, I create multiple Test Cases such as valid login, invalid login, blank fields, and password validation.

## 15.What is a Test Suite?
In my project, we grouped related test cases into Test Suites based on the application modules, such as Login, Booking, and Payment. During regression testing, we executed only the impacted Test Suites along with the critical business flow test cases instead of running the entire regression suite.

## 16.What is Severity?
Severity refers to the impact of a defect on the application's functionality.
Generally, the QA Engineer decides the Severity based on the technical impact of the defect.
In my projects, I assigned High Severity to defects that affected major functionalities such as payment failure or flight booking failure because users could not complete their transactions.

Example
-------
Payment page crashes.
Severity = High
Because the core functionality is broken.

## 17.Who decides Severity?
Generally, the QA Engineer decides the Severity based on the technical impact of the defect.

## 18.What is Priority?
Priority indicates how quickly a defect should be fixed based on business requirements.
It depends on the business impact rather than the technical impact.
In my project, if the company logo was displayed incorrectly on the home page before a production release, it was assigned High Priority because it affected the company's image, even though the functionality was not impacted.

## 19.Who decides Priority?
Priority is usually decided by the Product Owner, Business Analyst, Project Manager, or sometimes in discussion with the QA and Development teams.

## 20.Difference Between Severity and Priority
Severity refers to the impact of a defect on the application's functionality, whereas Priority refers to the urgency with which the defect should be fixed.
Severity is mainly a technical perspective, while Priority is a business perspective.
For example, if users are unable to complete payment, it is High Severity and High Priority because it directly affects business.
If there is a spelling mistake in the company name on the home page, it may be Low Severity but High Priority because it affects the company's reputation.

## 21.Can High Severity have Low Priority?
Yes. For example, if the Help page crashes but very few users use that feature, it can be High Severity because the functionality is broken, but Low Priority because it doesn't impact the core business.

## 22.What is a Defect Life Cycle?
The Defect Life Cycle is the process that a defect follows from the time it is identified until it is closed.
In my project, after identifying a defect, I logged it in JIRA with all the necessary details such as steps to reproduce, screenshots, severity, and priority.
The defect was then assigned to the developer for fixing. After the fix was deployed, I performed Retesting. If the issue was resolved, I closed the defect. If the issue still existed, I reopened it."

Defect Life Cycle
------------------
New -> Assigned -> Open -> Fixed -> Retest -> Closed OR Retest -> Reopened

## 23.Which tool did you use?
I used JIRA for defect tracking and management.

## 24.What information do you include while logging a defect? or What information belongs in a high-quality defect report?
Whenever I log a defect in JIRA, I make sure to include complete information so that the developer can easily reproduce the issue.

The defect report includes:
---------------------------
Defect Summary
Module Name
Environment
Build Version
Steps to Reproduce
Expected Result
Actual Result
Severity
Priority
Screenshot or Screen Recording
Log Files (if applicable).

## 25.What is Integration Testing?
Integration Testing is the process of verifying that two or more modules work correctly when they are integrated together.
The main objective is to ensure that the data flows correctly between different modules and there are no interface-related issues.
In the EasyJet application, after selecting a flight in the Flight Search module, the selected flight details should automatically appear in the Booking page. After completing the booking, the payment page should display the correct booking amount. Finally, after successful payment, the Booking Confirmation page should show the correct booking reference. During Integration Testing, I verified that data was passed correctly between all these modules.

## 26.When do you perform Integration Testing?
Integration Testing is performed after Unit Testing and before System Testing, once the individual modules are developed and integrated.

## 27.What is System Testing?
System Testing is the process of testing the complete integrated application as a whole to verify that it meets the specified business requirements.
Unlike Integration Testing, which focuses on the interaction between modules, System Testing verifies the entire application's functionality from the end user's perspective.
In my project, after all the modules were integrated, I tested the complete flight booking application, including Login, Flight Search, Booking, Seat Selection, Payment, and Booking Confirmation, to ensure the application worked correctly as a complete system.

## 28.Who performs System Testing?
Generally, the QA team performs System Testing after Integration Testing is completed.

## 29.What is End-to-End (E2E) Testing?
End-to-End Testing is the process of validating a complete business workflow from the beginning to the end, just as a real user would use the application.
The objective is to ensure that all integrated systems and business processes work together correctly without any interruption.
In my EasyJet project, A customer logs into the application, searches for a flight, selects the preferred flight, enters passenger details, selects seats, completes the payment, receives the booking confirmation email, and later views the booking under 'My Trips'. I verified this complete business flow without skipping any step.

## 30.Why is End-to-End Testing important?
It ensures that the complete business workflow works correctly across all integrated modules and external systems, providing confidence that the application is ready for production.

## 31.Explain the difference between Integration Testing, System Testing, and End-to-End Testing.
Integration Testing verifies whether different modules work correctly together and whether data is passed properly between them.
System Testing verifies the complete integrated application to ensure it meets the business requirements.
End-to-End Testing validates a complete business workflow from the user's perspective, ensuring that the entire process works correctly from start to finish.
For example, in a flight booking application, checking whether the Booking module correctly passes data to the Payment module is Integration Testing. Testing the entire flight booking application is System Testing. Completing the full user journey—from login to booking confirmation and verifying the booking in 'My Trips'—is End-to-End Testing.

## 32.How often do you release to production?
The release schedule depends on business requirements. In my project, we followed 2-week sprints, and production releases were generally planned once every 2 to 4 weeks after successful testing and business approval.

## 33.What testing do you perform before a production release?
Before every production release, we execute Smoke Testing to verify the build stability, followed by Functional Testing for new features, Regression Testing to ensure existing functionalities are not impacted, and UAT is completed by the business team. Once all critical defects are closed and stakeholders approve the release, the application is deployed to production.

## 34.How long does Regression Testing take?
The duration of Regression Testing depends on the size of the application, the number of impacted modules, and the number of test cases in the regression suite. There is no fixed duration.
In my project, for a minor change affecting only one module, regression testing usually took 1 to 2 days. For major releases involving multiple modules, it took 3 to 5 days. If it was a very large release, it could take one week or more.

## 35.What is QA (Quality Assurance)?
Quality Assurance, or QA, is a process-oriented approach that focuses on preventing defects by improving the software development and testing processes.
The main objective of QA is to ensure that the correct processes, standards, and methodologies are followed throughout the Software Development Life Cycle to build a quality product.
QA is proactive because it aims to prevent defects before they occur.

## 36.What is QC (Quality Control)?
Quality Control, or QC, is a product-oriented approach that focuses on identifying defects in the developed software through performing various testing activities.
The main objective of QC is to verify that the final product meets the specified requirements and is free from defects.
QC is reactive because it identifies defects after the product has been developed.

## 37.Which one do you perform as a QA Engineer? QA or QC?
As a QA Engineer, my primary responsibility is Quality Control because I execute test cases, identify defects, perform regression testing, and verify the application's functionality. However, I also contribute to Quality Assurance by participating in requirement reviews, test planning, process improvements, and suggesting preventive measures to improve the overall quality of the software.

## 38.Can you explain Verification and Validation with your project?
Verification is the process of checking whether we are developing the product correctly without executing the application.
In my project, It was performed during the requirement analysis phase. We reviewed the Business Requirement Document and user stories with the Business Analyst to ensure the requirements were complete and clear before development started.
Validation is the process of checking whether we are building the correct product by executing the application.
In my project, It is performed after the application was developed. I executed functional, regression, and end-to-end test cases to verify that the application behaved according to the business requirements.

## 39.What is Black Box Testing?
Black Box Testing means testing the application without knowing the internal code. As a tester, I only verify whether the application is working according to the requirements by giving inputs and checking the outputs.

## 40.What is White Box Testing?
White Box Testing means testing the application's internal code, logic, and program flow. It is usually performed by developers during Unit Testing.

## 41.What is Grey Box Testing?
Grey Box Testing is a combination of Black Box and White Box Testing. The tester has some knowledge about the application's design or database but does not know the complete source code.

## 42.How do you design test cases from a User Story?
First, I read the user story and acceptance criteria to understand the requirement. Then I identify all possible test scenarios. Based on those scenarios, I write detailed test cases covering positive, negative, boundary, and edge cases. After reviewing the test cases, I upload them to the test management tool (In my project, we used Jira for defect tracking. For test case management, we maintained our test cases in Excel) and execute them once the build is available.

## 43.What test design techniques have you used?
I mainly use Boundary Value Analysis and Equivalence Partitioning for input validations. I use Positive and Negative Testing to verify application behavior with valid and invalid inputs. Based on my experience, I also use Error Guessing to identify hidden defects.

## 44.What makes the good test case?
A good test case should be clear, concise, and easy to execute. It should completely cover the business requirement, include positive and negative scenarios, have clear test steps, test data, and expected results, and be reusable and easy to maintain for future regression testing.

## 45.Why are screenshots or videos important?
Screenshots or videos provide visual evidence of the defect. They help developers reproduce the issue more easily and reduce misunderstandings.

## 46.How do you decide the regression scope when time is limited?
In my project, if a change was made in the Payment module and we had limited time, I would first perform retesting to verify the defect fix. Then I would perform sanity testing on the changed functionality. Finally, I would execute regression testing only on the impacted modules and critical business flows instead of the entire regression suite to ensure the recent changes had not affected the existing functionality.

## 47.When should testing stop?
In my project, we stopped testing after all planned test cases were executed, critical and high-severity defects were fixed and verified, regression testing was completed successfully, and the business team approved the application during UAT. Once the exit criteria were met, the application was released to production.

## 48.What is Unit testing?
Unit Testing is the first level of testing in the Software Testing Life Cycle. It is performed by developers to verify that an individual unit or component of the application is working correctly. A unit can be a method, function, or class. The main objective of Unit Testing is to identify defects at an early stage before the code is integrated with other modules.

## 49.What is Functional Testing?
Functional Testing is a type of testing where I verify whether the application's functionality is working according to the business requirements. I execute test cases using valid and invalid inputs and compare the actual result with the expected result to ensure the feature works correctly.
For example, if I'm testing the Login page, I verify whether the user can log in with valid credentials, whether an error message is displayed for invalid credentials, and whether all validations work correctly. This is Functional Testing because I'm checking the functionality of the application.

## 50. What is Non Functional testing?
Non-Functional Testing is a type of testing where I verify how well the application performs rather than what it does. It focuses on aspects such as performance, security, usability, reliability, and compatibility to ensure the application provides a good user experience.
For example, if 5,000 users try to make a payment at the same time, I verify whether the application can handle the load without slowing down or crashing. This is Performance Testing, which is a type of Non-Functional Testing.

## 51.What is Ad Hoc Testing?
In my experience, after completing the planned test case execution, I used to spend some time by exploring the application beyond the documented test cases. I tested the scenarios like, invalid inputs, multiple clicks, refreshing the browser during transaction, session timeout, and navigation between pages to identify the hidden defects.

## 52.What is Accessibility Testing?
Accessibility Testing ensures that an application can be used easily by people with disabilities by verifying keyboard navigation, screen reader support, color contrast, alternative text for images, and proper labeling of UI elements.

## 53.What is Compatibility testing?
Compatibility Testing is a type of non-functional testing where I verify whether the application works correctly across different browsers, operating systems, devices, screen resolutions, and network environments.

## 54.Explain

Load Testing: It verifies the application's performance under the expected number of users.

Stress Testing: Stress Testing verifies the application's behavior when the load exceeds its expected capacity.

Spike Testing: Spike Testing verifies the application's stability during sudden increases or decreases in user traffic.

Endurance Testing: Endurance Testing verifies the application's performance under the expected load for a long duration.

Volume Testing: Volume Testing verifies the application's behavior when processing or storing a large volume of data.

Scalability Testing: Scalability Testing verifies whether the application can handle increasing users or transactions by scaling resources while maintaining performance.

## 55.What is security testing from a manual tester's perspective
Security Testing is a type of non-functional testing performed to verifying user authentication, role-based access, session timeout after inactivity, password validation, and ensuring users could not access unauthorized pages by changing the URL manually. Any security-related issues identified during testing were reported to the development team for further investigation.

## 56.What is alpha and beta testing?
Alpha: It is performed within the internal organisation before software is released to the external user.
It is usually conducted by QA Team, developers or internal employees.
The Objective is to identify the defect before release.
Beta: It is performed by real users or customers. It is conducted by selected external users.
The objectives is to collect user feedback and identify real world issues.

## 57.What is RTM?
RTM stands for Requirement Traceability Matrix. It is a document used to map each business requirement with its corresponding test cases to ensure that every requirement is covered by testing. It helps us verify that no requirement is missed during the testing process.

## 58.How do you create and manage the test data?
I create test data based on the business requirements and the test scenarios. I prepare data for positive, negative, boundary, and edge-case scenarios to ensure complete test coverage. I maintain the test data in Excel or the test management tool used in the project, and I update it whenever the requirements change.

## 59.How do you prioritize test cases?
I prioritize test cases based on business impact, critical functionality, risk, frequency of use, and recent code changes. I always execute high-priority and business-critical test cases first, followed by medium- and low-priority test cases. This helps ensure that the most important functionalities are verified even when testing time is limited.

## 60.How do you review your test cases?
After preparing the test cases, I review them to ensure they completely cover the business requirements. I verify that the test case title is clear, the test steps are easy to understand, the expected results are accurate, and both positive and negative scenarios are covered. I also check for duplicate or missing test cases. Finally, I discuss the test cases with the QA Lead or team members for peer review before execution.

## 61.What should test plan contains?
A Test Plan contains the testing objective, scope, strategy, test environment, deliverables, test data, entry and exit criteria, roles and responsibilities, schedule, risks, and tools required for the testing process.

## 62.What should test execution report contains?
A Test Execution Report is a document that summarizes the results of test execution. It provides information about how many test cases were executed, passed, failed, blocked, or not executed. It also includes defect details, execution progress, and the overall testing status, helping stakeholders understand the quality of the application before release.

## 63.How do you ensure test case are independent and repeatable
I ensure test cases are independent by using separate test data and clear preconditions, and I ensure they are repeatable by defining clear steps and expected results so they can be executed multiple times with consistent outcomes.

## 64.How do you maintain and version test case?
I maintain test cases by reviewing and updating them whenever there is a change in the business requirements or application functionality. I ensure that outdated test cases are modified instead of creating duplicates. If version control is followed in the project, I update the test case version or maintain a revision history so that changes can be tracked easily. This helps keep the test repository up to date and ensures that the test cases always reflect the latest requirements.

## 65.What is the difference between Error, Defect, and Failure?
An Error is a mistake made by a human, usually during requirements, design, or coding. A Defect (or Bug) is the flaw in the software caused by that error. A Failure occurs when the application behaves differently from the expected result during execution because of the defect.

SCENARIO
---------

## 66.you are given the login page. what manual test cases would you prepare?
First, I would understand the login requirements and acceptance criteria. Then I would prepare test cases with valid credentials, and combination of invalid, blank, malformed(input or request is not in the expected format or structure.), locked disabled, keyboard navigation, unverified accounts, password masking, case and whitespace handling, boundary length, enter key submission, and repeated clicking. For security behavior, protected pages cannot be reached after logout through Back or a direct URL.

## 67. How would you manually test a new registration form?
First, I would understand the business requirements and acceptance criteria. Then I would identify all the fields in the registration form and prepare functional test cases covering UI validation, mandatory field validation, positive scenarios, negative scenarios, field validations, boundary value scenarios, business rules, and successful registration. After preparing the test cases, I would execute them, report any defects, retest the fixes, and perform regression testing if required.

## 68.How would you test the forgot password?
First, I would understand the business requirements for the Forgot Password functionality. Then I would prepare test cases covering the navigation, input validation, positive and negative scenarios, password reset process, email or OTP verification, password validation, and successful login with the new password. After executing the test cases, I would report defects, retest the fixes, and perform regression testing if required.

## 69.An OTP is valid for two min. what test cases do you create?
I would prepare test cases to verify OTP generation, successful validation within 2 minutes, expiry after 2 minutes, invalid OTP handling, resend OTP functionality, and edge cases around the expiry time to ensure the OTP feature works correctly.

## 70.How do you test session timeout in a checkout or booking flow?
First, I would understand the session timeout requirement. For example, if the session timeout is 15 minutes, I would log in, add a product to the cart or proceed to the booking/payment page, remain inactive for more than 15 minutes, and then try to continue the checkout or booking process. I would verify that the application expires the session, redirects the user to the login page or displays a session expired message, and does not allow further actions until the user logs in again.

## 71.how do you test the file upload feature?
First, I would understand the business requirements, such as the supported file types, maximum file size, and upload restrictions. Then I would prepare test cases covering positive and negative scenarios, file validation, boundary value testing, error handling, and successful upload verification. After execution, I would report defects, retest the fixes, and perform regression testing if required.

## 72.How do you test a Date Picker?
First, I would understand the business requirements, such as the allowed date range, date format, and any restrictions like future or past dates. Then I would prepare test cases covering date selection, navigation, validations, boundary dates, leap years, disabled dates, and error handling to ensure the date picker works correctly.

## 73.What are the environments?
Developers develop the feature in the DEV environment.
They deploy a new build to the QA environment.
The QA team performs smoke testing to ensure the build is stable.
QA executes functional, integration, system, retesting, and regression testing.
After QA sign-off, the build is moved to Load and Performance(LNP).
LNP executes non functional testing and they moved to UAT.
Business users verify the seat selection feature.
Once approved, the build is deployed to Production, where customers can use it.



TESTNG
------

## 1.What is AventStack dependency?
Extent Reports is a reporting library developed by AventStack. It generates interactive HTML reports that show test execution results, including passed, failed, and skipped test cases, along with screenshots, logs, and execution time.

## 2.Why did you use Extent Reports instead of the default TestNG report?
The default TestNG report provides basic execution results. Extent Reports provides a more detailed and user-friendly HTML report with logs, screenshots, pass/fail status, execution time, and better visualization, making it easier to analyze test results.


## AGLIE
-------

## 1. What is Agile?
Agile is a software development methodology where the application is developed and tested in small iterations called sprints.
It focuses on continuous delivery, customer feedback, collaboration, and adapting to changing requirements.
In my projects at Capgemini, we followed the Agile Scrum methodology. We worked in 1-week sprints, where developers and testers worked together from requirement analysis until the release. This helped us deliver features faster and identify defects early.

## 2.What is Scrum?
Scrum is the most commonly used Agile framework. It divides the project into small iterations called sprints. Scrum includes defined roles, ceremonies, and artifacts that help the team deliver quality software quickly.
In my project, we followed Scrum with sprint planning, daily stand-up meetings, sprint reviews, and retrospectives every sprint.

## 3. What is a Sprint?
A Specific set of user stories is completed in a fixed time period is called Sprint.
In my EasyJet project, each sprint lasted 1 weeks. During the sprint, I prepared test cases, executed manual tests, automated stable features using Selenium, logged defects in JIRA, and verified bug fixes before the sprint ended.

## 4. What is Sprint Planning?
Sprint Planning is the meeting held at the beginning of every sprint where the team decides which user stories will be developed and tested during that sprint.
As a QA Engineer, I participated in sprint planning meetings to understand the requirements, estimate testing effort, identify dependencies, and clarify any questions with the Product Owner before development started.

## 5.What happens in the Daily Stand-up?
Daily Stand-up is a short meeting held every day, usually for 15 minutes.
Each team member answers three questions:
What did I complete yesterday?
What am I working on today?
Is there any blocker?
During stand-ups, I updated the team about completed testing, defects raised, automation progress, and any issues affecting testing.

## 6.What is Sprint Review?
Sprint Review is conducted at the end of the sprint.
The development team demonstrates the completed features to the Product Owner and stakeholders to collect feedback.
As a QA Engineer, I confirmed that all planned testing was completed, major defects were resolved, and the features were ready for demonstration.

## 7.What is Sprint Retrospective?
Sprint Retrospective is the meeting conducted after the Sprint Review to discuss how the sprint went.
The team discusses:
What went well
What could be improved
Action items for the next sprint
For example, if testing was delayed because requirements changed frequently, we discussed improving requirement clarification before development started.

## 8. Who is the Product Owner?
The Product Owner represents the business and is responsible for managing the product backlog and prioritizing user stories.
Whenever we had questions about business requirements or acceptance criteria, we discussed them with the Product Owner to avoid misunderstandings before testing started.

## 9. Who is the Scrum Master?
The Scrum Master ensures that the Scrum process is followed correctly and removes blockers faced by the team.
For example, if our QA environment was unavailable or we were waiting for a deployment, the Scrum Master coordinated with other teams to resolve the issue.

## 10. What is a User Story?
A User Story is a short description of a feature from the end user's perspective.
A typical format is:
As a customer,
I want to book a flight,
So that I can travel to my destination.
In my project, every sprint consisted of multiple user stories. Before testing, I analyzed the user stories, understood the acceptance criteria, and prepared test scenarios and test cases.

## 11. What are Story Points?
Story Points are used to estimate the effort required to complete a user story.
The estimation considers:
Complexity
Risk
Development effort
Testing effort
The Scrum team estimates story points together using Planning Poker.
As a QA Engineer, I contributed by estimating the testing effort required for each story.

## 12. What are Acceptance Criteria?
Acceptance Criteria are the conditions that must be satisfied before a user story is considered complete.
For example, in a flight booking application:
User Story:
As a customer, I want to book a flight.
Acceptance Criteria:
User should be able to search flights.
User should be able to select a flight.
Payment should be successful.
Booking confirmation should be generated.
Confirmation email should be sent.
Before testing, I always verified the acceptance criteria and created test cases to ensure all conditions were covered.

## 13. What is Definition of Done (DoD)?
Definition of Done is a checklist that defines when a user story is considered completely finished.
In my project, a user story was considered Done only when:
Development was completed.
Code review was completed.
Unit testing passed.
Manual testing passed.
Automation scripts were updated.
Regression testing passed.
No critical or high-severity defects remained open.
Product Owner approved the feature.
Only after meeting all these conditions was the user story moved to Done in JIRA.

## 14.How did you work in Agile?
In my EasyJet project, we followed a 1-week Agile Scrum sprint.

At the beginning of each sprint, I participated in Sprint Planning to understand the user stories and estimate testing effort. Based on the requirements, I prepared test scenarios and test cases.

Once development was completed, I performed Functional, Smoke, Regression, and End-to-End Testing. I logged defects in JIRA, tracked them through the defect lifecycle, and performed retesting after developers fixed them.

Every day, I attended the Daily Stand-up to share my testing progress, automation status, and any blockers.

At the end of the sprint, I participated in the Sprint Review, where completed features were demonstrated to stakeholders, and in the Sprint Retrospective, where the team discussed improvements for the next sprint.

This answer demonstrates your understanding of Agile while showing how you applied it in your real project, which is what interviewers for a 3-year QA role are looking for.
