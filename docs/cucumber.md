### CUCUMBER
### --------

### 1. What is Cucumber?
Cucumber is a Behavior Driven Development framework that allows us to write test scenarios in simple English using Gherkin language. It improves communication between Business Analysts, Developers, and Testers because everyone can understand the scenarios. In Cucumber, the Feature file contains the business scenarios, Step Definition classes implement those steps in Java, and Selenium performs the browser actions.

### 2.What is the advantage of Cucumber over TestNG?
TestNG is mainly used for test execution and assertions, whereas Cucumber focuses on writing business-readable test scenarios using Gherkin. In many projects, both are used together.

### 3.What is BDD?
BDD stands for Behavior Driven Development. It is an approach where the application's behavior is described in simple English before automation is implemented. This improves collaboration between business teams and technical teams because everyone understands the requirements in the same way. In our project, The Business Analyst shared the acceptance criteria, and we converted those into Gherkin scenarios. This reduced misunderstandings because the Feature files acted as a common document for both business and technical teams.

### 4.What language does Cucumber use?
Cucumber uses Gherkin language.

### 5.What is Gherkin?
Gherkin is a simple, readable language used to write Cucumber Feature files. It uses keywords like Feature, Scenario, Given, When, Then, And, and But.
	Feature: Login
	Scenario: Valid Login
	Given User launches the application
	When User enters valid username and password
	Then User should navigate to the Home page

### 6.Can non-technical people read Gherkin?
Yes. Gherkin is designed so that business users, testers, and developers can all understand the scenarios.

### 7.Explain the Cucumber Framework Flow.
In our framework, execution starts from the Runner class. The Runner reads the Feature files and identifies the Step Definitions using the Glue package. Each Step Definition calls methods from the Page Object classes. The Page Objects interact with the application through Selenium WebDriver. We use TestNG for execution, Maven for dependency management, Log4j2 for logging, Extent Reports for reporting, and Hooks for browser setup and teardown. Browser and application details are stored in config.properties.

### 8.What is the role of the Runner class?
The Runner class starts Cucumber execution and specifies the Feature file location, Glue path, Plugins, and Tags.

### 9.What is a Feature File?
A Feature file contains business requirements written in Gherkin language. It includes one Feature and multiple Scenarios describing different functionalities of the application. Since it is written in simple English, both technical and non-technical team members can understand it. In my project, each module had a separate Feature file. For example, Login.feature, FlightSearch.feature, and Booking.feature. This made the framework organized and easy to maintain.

### 10.What are Step Definitions?
Step Definitions are Java methods that implement the steps written in the Feature file. They are connected using annotations like @Given, @When, and @Then. Whenever Cucumber executes a scenario, it matches each Gherkin step with its corresponding Step Definition. In my project, the Step Definitions were responsible only for calling methods from the Page Object classes. We avoided writing Selenium code directly inside the Step Definitions to keep the framework clean.	`

### 11.What are Hooks?
Hooks are methods that execute before or after each Scenario. They are commonly used for browser setup, WebDriver initialization, taking screenshots on failure, and closing the browser. In my project, we used @Before to initialize WebDriver and read values from config.properties. We used @After to capture screenshots for failed scenarios using Extent Reports and then called driver.quit() to close the browser.

### 12.What is Scenario Outline?
Scenario Outline is used when the same Scenario needs to run multiple times with different input data. The test data is provided in the Examples table, and Cucumber executes the scenario once for each row. In my project, we used Scenario Outline for Login testing with multiple username and password combinations instead of writing separate scenarios.

### 13.What are Tags?
Tags are used to group and execute specific scenarios. For example, we can run only Smoke, Regression, or Sanity tests without executing the entire test suite. In my project, we maintained tags such as @Smoke, @Regression, and @Sanity. It help execute only the required scenarios, reducing execution time.

### 14.Can multiple tags be used?
Yes. Multiple tags can be used together using logical operators like AND, OR, and NOT to execute the required set of scenarios. we used combinations of tags to execute Smoke and Regression suites separately through the Runner Class.

### 15.Can one Scenario have multiple tags?
 A Scenario can have multiple tags depending on the test requirements.

### 16.Why did you use Cucumber instead of TestNG alone?
We chose Cucumber because the business team wanted readable test scenarios. Feature files written in Gherkin allowed Business Analysts, Developers, and Testers to understand the same scenarios. We still used TestNG for execution, parallel runs, and assertions, while Cucumber handled the BDD layer. In my project, the Business Analysts reviewed the Feature files during requirement discussions. Since the scenarios were written in simple English, it became easier to validate requirements before automation development started.

### 17.Explain Given, When and Then.
Given, When, and Then are the main Gherkin keywords used to describe a test scenario. 'Given' represents the precondition or initial state of the application. 'When' represents the action performed by the user. 'Then' represents the expected result or validation after the action. We also use 'And' to continue the same type of step without repeating the keyword. In my EasyJet project, 'Given' was used to launch the application, 'When' was used for actions like searching flights or selecting seats, and 'Then' was used to validate results such as displaying available flights or confirming the booking.

### 18.What is the purpose of 'And'?
'And' is used to improve readability by continuing the previous Given, When, or Then step without repeating the keyword.

### 19.What is the Runner class?
The Runner Class is responsible for starting the Cucumber execution. It specifies the location of the Feature files, Step Definition package using the Glue option, execution Tags, reporting plugins, and other Cucumber configurations through the @CucumberOptions annotation. In my project, we used a TestNG Runner Class. The Feature file location, Glue package, Smoke or Regression tags, and Extent Report plugins were configured in the Runner Class.

### 20.What is Glue?
Glue specifies the package where Cucumber searches for the Step Definition classes.

### 21.Difference between Scenario and Scenario Outline?
A Scenario executes only once with one set of test data. A Scenario Outline executes the same scenario multiple times using different sets of test data provided in the Examples table.
For example: For Login testing, we used Scenario Outline to validate multiple username and password combinations without creating separate scenarios.

### 22.When should you use Scenario Outline?
Whenever the same business flow needs to be executed with multiple input values.

### 23.What is Examples?
Examples is a table used with Scenario Outline to provide multiple sets of test data. Cucumber executes the Scenario once for each row in the Examples table. In my project, we used Examples for login credentials and different passenger details while validating the same booking flow.

### 24.Can a Scenario have Examples?
No. The Examples keyword is specifically used with Scenario Outline. A normal Scenario executes with the data directly provided in its steps.

### 25.How do you pass data from Feature File?
We can pass test data from the Feature file using Scenario Outline with Examples, DataTable, or Doc String. The choice depends on the type of data and the test scenario. We mainly used Scenario Outline with Examples for different login credentials and DataTables whenever multiple values had to be passed in a single scenario.

### 26. Which method did you use most?
Mostly Scenario Outline with Examples because many of our scenarios required multiple input combinations.

### 27.What is DataTable?
We used DataTables whenever multiple user details needed to be passed in one execution, such as passenger information or profile details.

### 28.Which Java object is commonly used to read a DataTable?
List<Map<String, String>> is commonly used because it allows accessing values using column names.

### 29.When do you use DataTable instead of Scenario Outline?
Scenario Outline is used when the same Scenario needs to execute multiple times with different data. DataTable is used when one Scenario needs multiple rows or columns of data during a single execution.
For example: For multiple login combinations, we used Scenario Outline. For entering multiple passenger details in one booking, DataTable was more suitable.

### 30.Which is better for Login testing?
Scenario Outline because the same login scenario runs with different credentials.

### 31.Why did you use the Page Object Model?
It separates locators and actions from test logic, making the framework more maintainable and reusable.

### 32.Difference between Background and Hooks?
Background is used for common business steps that should run before every Scenario in a Feature file. Hooks are Java methods used for technical tasks such as browser launch, screenshot capture, and closing the browser. In our project, we used Hooks for launching and closing the browser. We rarely used Background because most setup activities were technical rather than business-related.

### 33.Can Background and Hooks be used together?
Yes. Hooks perform technical setup and cleanup, while Background executes common business steps before every Scenario.

### 34.Which one executes the Scenario multiple times?
Scenario Outline with Examples executes the Scenario multiple times.

### 35.How do you generate Cucumber Reports?
We generate Cucumber reports by configuring plugins in the Runner Class. We can generate HTML, JSON, JUnit XML, and Extent Reports. After execution, these reports show the status of each Scenario, execution time, screenshots, and failure details. In my project, we generated Extent Reports after every execution. For failed scenarios, screenshots were automatically attached through Hooks, making it easier to analyze failures.

### 36.Why are reports important?
Reports provide execution status, failure details, screenshots, and logs, helping the team quickly analyze test results and share them with stakeholders.

### 37.What is BDD and how does cucucmber support it?
In my project, we followed BDD using Cucumber. We converted the business requirements and acceptance criteria into Feature files using Gherkin. For example, for a flight booking flow, we described the precondition using Given, the user action using When, and the expected result using Then. The corresponding Step Definition methods called our Page Object methods, which performed the Selenium actions. This helped the QA, development, and business teams understand and review the scenarios easily.

### 38.What is the main difference between BDD and Cucumber?
BDD is a development approach or methodology, whereas Cucumber is a tool or framework that helps implement BDD by allowing us to write and execute scenarios using Gherkin.

### 39.Why did your project use Cucumber?
We used Cucumber because it provided business-readable Feature files, improved collaboration between technical and non-technical teams, and allowed us to connect those scenarios with our Selenium automation through Step Definitions.

### 40.Explain Gherkin syntax with all keywords
Gherkin is the business-readable language used by Cucumber. The main structure starts with Feature, which represents the functionality, followed by Scenarios representing individual behaviors. Inside a Scenario, we use Given for preconditions, When for actions, and Then for expected results. And and But are used for additional steps. For common steps we can use Background, and for data-driven testing we use Scenario Outline with Examples. Tags are used to group and execute specific scenarios. We can also use DataTables for structured data and Doc Strings for multiline data.

### 41.What is role of the feature file and step definition file?
In my project, Feature files were used to write business scenarios such as login, flight search, seat selection, and booking in Gherkin format. The Step Definition classes mapped those Gherkin steps to Java methods. We kept the actual Selenium actions inside Page Object classes, so the Step Definitions mainly acted as a bridge between the Feature file and Page Objects. This separation made the framework readable and maintainable.

### 42.Should we write Selenium code directly inside the Step Definition?
Technically we can, but we don't prefer it. In a POM-based framework, Step Definitions should call Page Object methods, while locators and Selenium actions should be maintained in the Page Classes. This keeps business logic and UI implementation separate.

### 43.What are Hooks in cucumber? Explain @Before, @After, @BeforeStep and @AfterStep?
Hooks in Cucumber are special methods that allow us to execute common setup and cleanup code before or after scenarios or individual steps. They help us manage the test environment without putting technical setup code inside the Feature file. The commonly used hooks are @Before, @After, @BeforeStep, and @AfterStep. In my project, we mainly used @Before for browser and WebDriver setup and @After for screenshot capture and browser cleanup. We didn't use @BeforeStep and @AfterStep for normal execution because step-level operations can increase execution time. We used them only when step-level logging or debugging was required.

### 44.Does @Before run before every Scenario?
Yes. By default, @Before executes before every Scenario that is included in the Cucumber execution.

### 45.What is the difference between @Before Hook and Background?
@Before is Java code and is mainly used for technical setup such as WebDriver initialization. Background is written in the Feature file and is used for common business steps that should run before every Scenario.

### 46.You need to take a screenshot only when a test fails. How would you implement this in cucumber?
In my project, we use Extent Reports, so I implement this in the Cucumber @After Hook. After each Scenario, I check scenario.isFailed(). If the Scenario fails, I capture the screenshot using Selenium's TakesScreenshot, save it using our Screenshot utility, and attach the screenshot to the corresponding ExtentTest. Finally, I close the browser using driver.quit(). This way, screenshots are generated only for failed scenarios

### 47.What happens if the test passes?
The scenario.isFailed() condition is false, so no screenshot is captured. The browser is simply closed during teardown.

### 48.Why use OutputType.BYTES?
I use OutputType.BYTES because Cucumber's scenario.attach() can directly attach the screenshot bytes to the report, which is convenient for displaying the screenshot with the failed scenario.

### 49.A @Before hook needs to run only for scenario tagged @smoke. How do you do it?
In my project, we used conditional Hooks when a particular setup was required only for a specific test category. For example, if some setup was required only for Smoke scenarios, we used @Before("@smoke"). This prevented unnecessary setup from running for Regression or other scenarios and helped keep execution efficient.

### 50.Can we have multiple conditional Hooks?
Yes. We can define multiple Hooks with different tags. For example, @Before("@smoke") can handle Smoke-specific setup and @Before("@regression") can handle Regression-specific setup.

### 51.Can @After also be conditional?
Yes. We can use the same approach with @After("@smoke") to execute cleanup only for scenarios tagged @smoke.

### 52.You have a step definition that matches two Gherkin steps. What error occurs and How do you fix it?
If two Step Definitions match the same Gherkin step, Cucumber reports an AmbiguousStepDefinitionsException. This happens because Cucumber cannot determine which Java method should execute. I fix it by making the step definitions unique, usually by changing the Gherkin wording or using more specific expressions. I also avoid creating duplicate step definitions for the same business action.

### 53.Is UndefinedStepException the error in this case?
No. UndefinedStepException occurs when Cucumber cannot find any matching Step Definition. When multiple Step Definitions match the same step, the problem is an ambiguity, and Cucumber reports AmbiguousStepDefinitionsException.

### 54.What is the difference between DataTable and Doc String?
DataTable is used for structured data in rows and columns, whereas Doc String is used for large blocks of text such as JSON, XML, or multi-line content.

### 55.A particular test is flaky and be temporarily skipped without deleting it. How do you handle it?
In my project, if a test was temporarily unstable, we used a tag such as @Skip and excluded it from the execution using the Cucumber tag expression. We kept the test in the Feature file and tracked the reason for skipping it. Once the issue was fixed, we removed the skip tag so the test could be included again.

### 56.Why don't you just delete the flaky test?
Because the test is still a valid requirement. Deleting it would mean losing the coverage. We temporarily exclude it while the issue is being investigated and then enable it again after fixing the problem.

### 57.How do you run a specific tagged test from the command line using maven?
In my project, we used Maven for execution, so we could run specific test suites from the command line using Cucumber tag expressions. For example, during daily execution we could run mvn test -Dcucumber.filter.tags="@Smoke" to execute only Smoke scenarios. For regression, we could pass the Regression tag instead of running the complete suite.

### 58.Why is running by tags useful?
It allows us to selectively execute tests based on the requirement, such as Smoke, Sanity, or Regression, which saves execution time and is especially useful in CI/CD pipelines.

### 59.	Your test suite has 200 scenario. The CI pipeline must run only the critical path tests on every commit. How do you organize it?
In my project, I would use tags to separate the test suite based on priority. For example, critical login, search, and booking scenarios would have an @Critical or @Smoke tag. Our CI pipeline would execute mvn test -Dcucumber.filter.tags="@Critical" on every commit. Full regression would run separately, such as nightly or before a release. This gives developers quick feedback while still maintaining full regression coverage.

### 60.Why not run all 200 tests on every commit?
Running all 200 scenarios on every commit would increase execution time and delay feedback. Critical-path tests provide quick validation of the most important functionality, while the complete regression suite can run at a different stage.

### 61.What is the Difference between DataTable and scenario Outline with example?
I used Scenario Outline when I needed to execute the same flow with multiple test-data combinations, such as testing login with different credentials. I used DataTable when I needed to pass multiple related values within a single scenario, such as passenger details. So, Scenario Outline controls multiple executions, whereas DataTable passes structured data to a step.

### 62.Can DataTable execute a Scenario multiple times?
No. A DataTable itself doesn't repeat the Scenario. It passes the table data to the step. If I need multiple executions with different data, I would use Scenario Outline with Examples.

### 63.write the Gherkin scenario to test adding multiple products to a cart using DataTable?
Feature: Shopping Cart

Scenario: Add multiple products to the cart
  Given User is on the products page
  When User adds the following products to the cart
    | product              |
    | Sauce Labs Backpack  |
    | Sauce Labs Bike Light|
    | Sauce Labs Bolt T-Shirt |
  Then all selected products should be displayed in the cart

@When("User adds the following products to the cart")
public void addProductsToCart(List<Map<String, String>> products) {

    for (Map<String, String> product : products) {
        String productName = product.get("product");
        productsPage.addProductToCart(productName);
    }
}

I would create a DataTable containing the product names in the Feature file. In the Step Definition, I would receive it as List<Map<String, String>> and loop through each row. For each product name, I would call the Page Object method to add that product to the cart. Finally, I would verify that all selected products are present in the cart.

### 64.you need to the login feature with 5 different user roles. Design the feature file?
Since I need to test the same login flow with five different user roles, I would use a Scenario Outline with an Examples table. I would keep the common login steps in the Scenario Outline and provide the username, password, and role as test data in Examples. Cucumber will execute the scenario once for each row, so the same flow will be validated for all five roles.

### 65.Why not create 5 separate Scenarios?
Because the test flow is the same. Creating five separate scenarios would duplicate the same steps. Scenario Outline avoids duplication and makes the Feature file easier to maintain.

### 66.How do you integrate POM with cucumber?
we followed Cucumber with POM. The Feature files contained the business scenarios, Step Definitions handled the Gherkin steps, and Page Object classes contained the locators and Selenium actions. We initialized the Page Objects with the WebDriver and called their methods from the Step Definitions. We avoided writing locators and Selenium actions directly in Step Definitions, which made the code reusable and easier to maintain.

### 67.Why don't you write Selenium code directly in Step Definitions?
Because it creates duplication and makes the Step Definition classes difficult to maintain. By keeping Selenium actions inside Page Objects, the same methods can be reused by multiple scenarios and any UI locator changes can be handled in one place.

### 68.How do you share WebDriver instance across multiple step definition classes in cucumber?
In my framework, we maintain WebDriver in a separate WebDriver Manager class. The driver is initialized in the Cucumber @Before Hook. The Step Definition classes get the driver from the WebDriver Manager instead of creating their own driver. This allows Login, Dashboard, Booking, and other Step Definition classes to work with the same browser session. Finally, we close the driver in the @After Hook.
For normal execution, I share the WebDriver through a Driver Manager or Test Context. For parallel execution, I maintain one WebDriver per thread using ThreadLocal.

### 69.Why shouldn't each Step Definition class create its own WebDriver?
If each Step Definition creates its own WebDriver, it will create separate browser sessions. We would lose the application state between steps and scenarios. Sharing the same driver instance ensures that the test continues in the same browser session.For normal execution, I share the WebDriver through a Driver Manager or Test Context. For parallel execution, I maintain one WebDriver per thread using ThreadLocal.

### 70.Design a cucumber + selenium framework folder structure for an e-commerce project?
For my e-commerce Cucumber Selenium framework, I would use a Maven-based POM structure. Feature files are maintained under the features folder. Step Definitions implement the Gherkin steps, while Page Object classes contain locators and Selenium actions. Hooks handle WebDriver setup, screenshots and cleanup. I would keep reusable components such as WebDriver Manager, Config properties and Screenshot utilities under the utils package. Configuration and test data would be maintained separately under resources. We can also maintain Extent Reports, screenshots and logs separately. This separation makes the framework reusable, maintainable and easy to scale.

### 71.Why this structure?"
The main reason is separation of responsibilities. Feature files contain business scenarios, Step Definitions connect Cucumber with the application, Page Objects handle UI actions, and utilities handle common functionality. So if a locator changes, I only need to update the Page Object instead of changing the Feature file or Step Definition.

### 72.Write the scenario to cover both positive and negative cases for a user registration form?
I would use a Scenario Outline because the registration flow remains the same while the test data changes. I would cover positive and negative cases such as valid registration, mandatory field validation, invalid email, missing phone number, and password mismatch. I would maintain these different combinations in the Examples table along with the expected validation message.

### 73.How do you handle  dynamic data (ex: generated order id's)between steps in cucumber?
In my framework, for dynamic values such as order IDs or booking references, I would store the value in a shared Test Context after it is generated. If another Step Definition class needs the value, it retrieves it from the same context. This is useful because the value is generated at runtime and cannot be hardcoded.

### 74.Why not use a static variable?
A static variable can work for simple sequential execution, but it can cause problems during parallel execution because multiple scenarios may overwrite the same value. A scenario-specific Test Context is safer, especially when we run tests in parallel.

### 75.Write a cucumber feature for a bank transfer between two accounts, covering success and failure cases.
For a bank transfer feature, I would use a Scenario Outline because the transfer flow is common but the test data and expected results vary. I would cover positive cases such as a valid transfer and negative cases such as insufficient balance, invalid destination account, same source and destination account, and invalid transfer amount. I would maintain these combinations in the Examples table.

Feature: Bank Transfer

  Scenario Outline: Transfer money between two accounts
    Given User is logged into the banking application
    And User has sufficient balance in the source account
    When User transfers "<amount>" from "<sourceAccount>" to "<destinationAccount>"
    Then The transfer result should be "<expectedResult>"

    Examples:
      | sourceAccount | destinationAccount | amount | expectedResult              |
      | 10001         | 20001               | 1000   | Transfer successful         |
      | 10001         | 20001               | 50000  | Insufficient balance        |
      | 10001         | 99999               | 1000   | Invalid destination account |
      | 10001         | 10001               | 1000   | Cannot transfer to same account |
      | 10001         | 20001               | -500   | Invalid transfer amount     |

### 76.What cases are covered?

Success:

Valid source account
+ Valid destination account
+ Valid amount
+ Sufficient balance
        ↓
Transfer successful

Failure:

Insufficient balance
Invalid destination account
Same source and destination account
Invalid/negative amount

### 77.your test needs to verify the email delivery after user registration. How do you automate this?
After successful user registration, I would verify the email delivery separately from the UI validation. I would register the user with a unique email address, then access a test mailbox or email-testing service through an API. I would wait for the email to arrive, verify the recipient, subject, and required content, and if there is a verification link, I would extract it and validate it. This is more reliable than trying to automate a real email client using Selenium.

### 78.Would you use Selenium to verify the email?"
No, I would not normally use Selenium for email verification. Selenium is mainly for browser UI automation. I would use an email API or a test-mailbox service to retrieve and validate the email. Selenium can then be used to open the verification link if the requirement is to verify the complete activation flow.

### 79.you have 500 scenarios and tests running slowly. How would you implement the parallel execution in cucumber?
I would implement parallel execution through Maven and configure the required thread count. Since multiple scenarios will execute simultaneously, I would maintain WebDriver using ThreadLocal so every scenario gets its own browser instance. I would also make sure test data, screenshots, and reports are handled independently to avoid conflicts. Before enabling parallel execution fully, I would identify scenarios that share state or depend on execution order and make them independent.

### 80.Why do you need ThreadLocal<WebDriver> for parallel execution?
Because a single WebDriver instance cannot safely be shared by multiple parallel scenarios. ThreadLocal gives each execution thread its own WebDriver instance, so the scenarios remain isolated.

### 81.Can all 500 scenarios run in parallel?
For parallel Cucumber execution, I use ThreadLocal<WebDriver> to maintain a separate WebDriver instance for each thread. When a scenario starts, I create the driver and store it in ThreadLocal. Step Definitions and Page Objects retrieve the driver using getDriver(). After the scenario finishes, I quit the browser and remove the driver from ThreadLocal. This prevents different scenarios running in parallel from sharing the same browser session.

### 82.Implement thread-safe WebDriver management for parallel cucumber execution?
For parallel Cucumber execution, I use ThreadLocal<WebDriver> to maintain a separate WebDriver instance for each thread. When a scenario starts, I create the driver and store it in ThreadLocal. Step Definitions and Page Objects retrieve the driver using getDriver(). After the scenario finishes, I quit the browser and remove the driver from ThreadLocal. This prevents different scenarios running in parallel from sharing the same browser session.

### 83.Why can't we use a normal static WebDriver?
A normal static WebDriver would be shared by all parallel threads. One scenario could change the page or close the browser while another scenario is using it. ThreadLocal gives each thread its own isolated WebDriver instance.

### 84.Write a feature file for password reset functionalities with all edge cases?
For password reset, I would cover both functional and security-related edge cases. I would test a valid registered email, unregistered email, invalid or empty email, valid and invalid reset links, expired and already-used links, password policy validation, password mismatch, and verify that the reset link cannot be reused after a successful reset. I would use Background for the common business step of opening the Forgot Password page and Scenario Outline for validations that require multiple sets of test data.

### 85.What security-related cases would you test for password reset?
I would test expired tokens, already-used tokens, tampered or invalid tokens, token reuse after a successful reset, password policy enforcement, and making sure the reset response doesn't reveal whether an email address is registered.

### 86.What reporting plugins are available in cucumber? How do you generate HTML report?
Cucumber provides built-in reporting through its plugins, such as HTML, JSON, and JUnit reports. In my project, we also use Extent Reports for a more detailed and customized report with screenshots. For the standard Cucumber HTML report, I configure the html plugin in the Cucumber Runner. After execution, Cucumber generates an HTML report in the specified location. We can also generate a JSON report and use it with other reporting tools.

### 87.How do you generate a basic Cucumber HTML report?
Cucumber provides a built-in HTML reporting plugin. I configure the html plugin in the @CucumberOptions of the Runner class and specify the report location. After running the tests using Maven, Cucumber automatically generates the HTML report in that location.

### 88.how do you rerun only the failed scenarios automatically after the first run?
In Cucumber, I use the Rerun plugin to capture the scenarios that failed during the first execution. I configure rerun:target/failed-scenarios.txt in the Cucumber options. After the first execution, Cucumber stores the failed scenarios in this file. Then I use a separate runner that takes this file as its feature source and executes only those failed scenarios. This avoids rerunning the scenarios that already passed.I can also generate the Extent Report for the rerun execution so that the final report shows the results of the failed scenarios after retry.

### 89.Why do you use a separate runner for failed scenarios?
I keep a separate rerun runner so that the normal execution and failed-scenario execution are clearly separated. The main runner executes the complete test suite, while the rerun runner reads the failed-scenarios file and executes only those failures. This is especially useful when we have a large regression suite because we don't have to execute all the scenarios again.

### 90.how would you integrate cucumber tests with jenkins to publish test results?
I generate the required report files during the Maven execution and configure Jenkins to publish the report artifacts. For example, the JUnit XML report can be consumed by Jenkins for test-result publishing, while the HTML or Extent report can be published as an HTML report for detailed analysis.

### 91.How do you handle a drop down, date picker, and file upload within a cucumber scenario?
In my Cucumber framework, I handle these controls through Page Objects. For standard dropdowns, I use Selenium's Select class, while custom dropdowns are handled through normal click and selection actions. For date pickers, I either enter the date directly or navigate through the calendar depending on the implementation. For file uploads, I use sendKeys() with the file path on the file input element. The Step Definitions only call these Page Object methods, keeping the framework maintainable.

### 92.Can you use Select for every dropdown?
No. Select works only for HTML <select> elements. For custom dropdowns implemented using div, li, or other elements, I handle them using normal Selenium actions.

### 93.How do you handle a dynamic date picker?
I identify the current month and year, navigate to the required month using the next or previous controls, and then select the required day. I would make the date selection method parameterized so it can be reused for different dates.

### 94.How do you upload a file without using the OS file chooser?
If there is an <input type='file'> element, I use sendKeys() with the absolute or configured file path. Selenium sends the path directly to the file input.

