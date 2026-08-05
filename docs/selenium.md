# SELENIUM
---------

### 1.Explain the selenium architecture and WebDriver flow?
Selenium WebDriver follows a client-server architecture. I write the automation script in Java using Selenium WebDriver APIs. When I execute a Selenium command, Selenium converts it into a W3C WebDriver request and sends it to the browser-specific driver, such as ChromeDriver. The browser driver acts as a bridge and communicates with the browser. The browser executes the requested action on the application and sends the response back to the browser driver, which then returns it to Selenium WebDriver. Finally, Selenium passes the response back to my test script, and the execution continues with the next command.
Simple diagram:
----------------

Java Test Script
        ↓
Selenium WebDriver API
        ↓
ChromeDriver / EdgeDriver
        ↓
W3C WebDriver Protocol
        ↓
Browser
        ↓
Web Application
        ↑
      Response

### 2.In Selenium, which is the client and which is the server?
In Selenium WebDriver architecture, the Selenium WebDriver library (Java client) acts as the client because it sends automation commands. The browser driver, such as ChromeDriver, EdgeDriver, or GeckoDriver, acts as the server because it receives those commands, communicates with the browser, and returns the response back to the client.

### 3.Which locator strategy do you prefer and why?
I don't have a single preferred locator for every situation. I choose the locator based on the application's HTML structure. My first preference is id because it is usually unique and provides better readability and performance. If id is not available, I prefer name, followed by CSS Selector. When CSS cannot uniquely identify the element, I use XPath. I try to avoid using dynamic or absolute XPath because they are more likely to break when the UI changes.

### 4.What is the difference between findElement() and findElements()?
findElement() is used to locate a single web element. It returns the first matching element, and if no element is found, it throws a NoSuchElementException. findElements() is used to locate multiple web elements. It returns a list of matching elements, and if no elements are found, it returns an empty list instead of throwing an exception. In my project, I used findElement() for unique elements like the Login button and Username field, and findElements() for product lists, search results, table rows, and to verify whether optional elements were present.

### 5.Explain implicit, explicit and fluent wait?
Implicit Wait is a global wait that applies to all element searches and waits for a specified time before throwing an exception. Explicit Wait is used to wait for a specific element or condition and is more efficient because it proceeds as soon as the expected condition is met.   Fluent Wait is an advanced form of Explicit Wait that allows us to configure the maximum wait time, polling interval, and exceptions to ignore. In my project, I mainly used Explicit Wait because it provided better control and made the automation scripts more reliable.

### 6.Why is Thread.sleep() not recommended?
Thread.sleep() pauses the execution for a fixed amount of time, even if the element becomes available earlier. This increases the execution time unnecessarily. Explicit Wait is more efficient because it proceeds as soon as the expected condition is met.

### 7.How do you handle stale element reference exceptions?
A StaleElementReferenceException occurs when Selenium tries to interact with a web element but the element is no longer available to the current DOM. This usually happens when the page is refreshed, reloaded, or when the element is recreated dynamically.To handle it, I first identify the reason for the DOM change, then locate the element again before interacting with it. I also use Explicit Wait to wait until the element becomes available or clickable. In my project, relocating the element and using Explicit Wait resolved most stale element issues.

### 8.How do you handle frames, windows and alerts?
In Selenium, I use the switchTo() method to handle frames, windows, and alerts. For frames, I switch to the frame before interacting with its elements and then return to the main page using defaultContent(). For multiple windows or tabs, I use getWindowHandles() to get all window IDs, switch to the required window, perform the actions, and then switch back to the parent window if needed. For alerts, I use switchTo().alert() to accept, dismiss, or read the alert message. In my project, I handled iframes for payment pages, multiple windows for links opening in new tabs, and alerts for confirmation pop-ups such as delete operations.

### 9.What happens if you don't switch to an alert before interacting with it?
If I don't switch to the alert, Selenium cannot interact with the main web page because the alert blocks further actions. If I try to click an element or perform any operation without handling the alert, Selenium throws an UnhandledAlertException. Therefore, I first switch to the alert using driver.switchTo().alert(), perform the required action such as accept(), dismiss(), or getText(), and then continue with the remaining test steps.

### 10.How do you automate dropdowns?
In my project, I handled both standard and custom dropdowns. For example, on the booking page, some dropdowns like passenger count were standard HTML dropdowns, so I used the Select class. For auto-suggestion or searchable dropdowns such as airport selection, I entered the search text, waited for the suggestions to appear, and selected the required option by clicking it.

### 11.Which methods are available in the Select class?
The Select class provides methods such as selectByVisibleText(), selectByValue(), and selectByIndex(). It also provides methods like getOptions(), getFirstSelectedOption(), getAllSelectedOptions(), isMultiple(), and corresponding deselect methods for multi-select dropdowns.

### 12.How do you identify whether a dropdown is a Select dropdown?
I inspect the HTML using the browser's Developer Tools. If the dropdown is created using the <select> tag, I use the Select class. If it is created using elements like div(division), ul(unorderedlist), or li(list), I treat it as a custom dropdown and automate it using normal Selenium locators.

### 13.What is the difference between selectByVisibleText(), selectByValue(), and selectByIndex()?
The Select class provides three methods to select an option from a standard HTML dropdown. selectByVisibleText() selects the option based on the text displayed to the user. selectByValue() selects the option based on the value attribute in the HTML. selectByIndex() selects the option based on its position in the dropdown, starting from index 0.

### 14.Which one do you prefer?
I usually prefer selectByVisibleText() because it is more readable and closely matches what the user sees. If the displayed text changes frequently, I may use selectByValue() if the value attribute is stable. I rarely use selectByIndex() because the order of options can change.

### 15.Can the Select class be used for all dropdowns?
No. The Select class can only be used with standard HTML dropdowns that use the <select> tag. If the dropdown is built using elements like div, ul, or li, it is considered a custom dropdown, and I handle it by clicking the dropdown and selecting the required option using Selenium locators.

### 16.How do you handle a multi-select dropdown?
A multi-select dropdown allows users to select more than one option. In Selenium, I first create a Select object and use the isMultiple() method to verify whether the dropdown supports multiple selections. If it does, I use methods like selectByVisibleText(), selectByValue(), or selectByIndex() to select multiple options. If needed, I use methods like deselectAll() or deselectByVisibleText() to remove selections.

### 17.How do you handle dynamic webelment?
Dynamic web elements are elements whose attributes change dynamically, making fixed locators unreliable. To handle them, I first look for stable attributes such as name or placeholder. If required, I use relative XPath, CSS Selectors, or XPath functions like contains() and starts-with(). I also use Explicit Wait to ensure the element is available before interacting with it. In my project, I handled dynamic elements using these techniques to make the automation scripts more stable and maintainable.

### 18.Which do you prefer for dynamic elements: CSS Selector or XPath?"
If a stable CSS attribute is available, I prefer a CSS Selector because it is concise and generally performs well. However, if I need to locate an element based on visible text, parent-child relationships, or partial attribute matching, I use a relative XPath with functions like contains() or starts-with(). The choice depends on which locator is more stable and maintainable for that particular element.

### 19.How do you perform mouse and keyboard interactions?
In my project, I mainly used the Actions class whenever advanced user interactions were required. For example, I used it to perform click actions on elements that were not easily clickable through the normal click() method. I also know how to use the Actions class for mouse hover, double-click, right-click, and drag-and-drop, although those scenarios were not part of my project.
In my project, while selecting the source and destination airports, I used keyboard actions like the Arrow Down key and Enter key to select the required airport from the auto-suggestion list.

### 20.How do you take screenshots and use javaScriptExecutor?
In my automation framework, I implemented screenshot capture in the TestNG Listener. Whenever a test failed, the listener automatically captured the screenshot and attached it to the Extent Report. This made debugging much easier.I used JavaScriptExecutor mainly for scrolling to elements before interacting with them, and only occasionally for clicking elements when Selenium's normal click couldn't perform the action.

### 21.Can JavaScriptExecutor replace WebDriver?
No. WebDriver methods should always be the first choice. JavaScriptExecutor should be used only when normal Selenium methods cannot interact with the element.

### 22.When do you use JavaScriptExecutor?
Scroll to an Element and Click an Element
If Selenium throws exceptions like:
ElementClickInterceptedException.
ElementNotInteractableException.

### 23.How do you run the cross-browser tests?
Cross-browser testing is the process of verifying that the application works correctly across different browsers such as Chrome, Edge, and Firefox.We achieve this using TestNG parameterization. I pass the browser name as a parameter through the TestNG XML file, and based on that parameter, we initialize the corresponding browser driver in Base Class. This allows to execute the same test cases on multiple browsers without changing the test code.
In my project, we used the config.properties file to store the default browser configuration. During execution, the framework reads the browser value from this file. If we need to run the tests on a different browser, we pass the browser name through the Maven command line. The command-line value overrides the default configuration, and the Base Class launches the appropriate browser, such as Chrome or Edge. This approach allows us to execute the same automation suite across multiple browsers without changing the test code.

### 24.Why do selenium tests become flaky,and how do you reduce flakiness?
In my project, the main cause of flaky tests was synchronization issues because some pages loaded dynamically. We handled this by using Explicit Waits instead of Thread.sleep(). We also used stable locators and avoided dynamic XPath wherever possible. In addition, our test cases were independent, so one test did not affect another. These practices significantly reduced flaky test failures.  

### 25.What is Selenium webdriver and what are the advantages and limitations?
Selenium WebDriver is an open-source tool used to automate web applications. It communicates directly with browsers through browser-specific drivers such as ChromeDriver and EdgeDriver. It supports multiple browsers and programming languages and can be integrated with tools like TestNG, Maven, and Jenkins to build a complete automation framework. Its main advantages are cross-browser support, multiple language support, and easy integration with other tools. Its limitations are that it can automate only web applications, cannot directly automate CAPTCHA or OTP verification, and requires additional tools for reporting and test management.

### 26.Why did you choose Selenium WebDriver?
We chose Selenium WebDriver because it is open source, supports multiple browsers, integrates well with Java, TestNG, Maven, and Jenkins, and is suitable for building a robust automation framework.

### 27.Can Selenium automate desktop applications?
No. Selenium is designed only for web application automation. For desktop applications, tools such as WinAppDriver or AutoIt are commonly used.

### 28.What are the selenium important components?
The Selenium Suite has four main components: Selenium IDE, Selenium WebDriver, Selenium Grid, and Selenium RC. Selenium IDE is used for record-and-playback automation. Selenium WebDriver is the core component used to automate web applications and is the most widely used in real projects. Selenium Grid is used for parallel and cross-browser execution across different machines and browsers. Selenium RC is the older version of Selenium and has been deprecated in favor of Selenium WebDriver. In my project, we mainly used Selenium WebDriver with Java, TestNG, Maven, and Jenkins.

### 29.Which Selenium component did you use in your project?
In my project, I mainly used Selenium WebDriver for web automation. We also used TestNG for test execution, Maven for dependency management, Extent Reports for reporting, and Jenkins for CI/CD. We did not use Selenium IDE or Selenium RC. Selenium Grid can be used for parallel execution, but in our project, cross-browser execution was handled through framework configuration.

### 30.What is different between WebDriver.close() and WebDriver.quit()?
In my project, I used driver.quit() in the @AfterMethod to ensure that all browser windows were closed after each test execution. This prevented leftover browser instances and ensured a clean environment for the next test. I used driver.close() only in scenarios where I needed to close a child window or tab and then switch back to the parent window.

### 31.What happens if you call driver.close() when there is only one browser window open?"
driver.close() closes that browser window. Since there are no other windows left, the browser is closed. However, unlike driver.quit(), it does not explicitly terminate the WebDriver session. Therefore, driver.quit() is the recommended method for ending test execution because it closes the browser and cleans up the WebDriver session properly.

### 32.What is different between get() and navigate().to()?
driver.get() and driver.navigate().to() are both used to open a URL in the browser. The main difference is that driver.get() is mainly used to launch a webpage, whereas driver.navigate().to() is part of the Navigation interface, which also provides additional navigation methods like back(), forward(), and refresh(). In terms of opening a URL, both methods behave similarly.In my project, I mainly used driver.get() to launch the application at the start of each test because it is simple and clear. I used driver.navigate() methods such as back(), forward(), and refresh() only in scenarios where I needed to verify browser navigation.

### 33.Which one do you prefer?
I generally prefer driver.get() for launching the application because it is straightforward and commonly used. I use driver.navigate().to() when I am already working with browser navigation features such as back, forward, or refresh.

### 34.Is there any performance difference between get() and navigate().to()?
No. In Selenium WebDriver, both methods ultimately load the requested URL. There is no significant performance difference. The choice depends on readability and whether the test involves browser navigation.

### 35.What is the difference between visibilityOfElementLocated(), presenceOfElementLocated(), and elementToBeClickable()?
These are all Explicit Wait conditions provided by Selenium, but they are used for different purposes.presenceOfElementLocated() waits until the element is available in the DOM, but it may still be hidden. visibilityOfElementLocated() waits until the element is both present and visible, making it suitable for typing into fields or reading text. elementToBeClickable() waits until the element is present, visible, and enabled, so it is mainly used before clicking buttons or links. In my project, I mostly used elementToBeClickable() for click actions and visibilityOfElementLocated() for text fields and validations.

### 36.Why is mixing implicit and explicit wait discourage?
In my project, we mainly used Explicit Wait because different elements loaded at different times. This allowed us to wait only for the required element instead of applying a global wait to every element, making our automation scripts more stable and efficient.

### 37.Why is mixing implicit and explicit wait discourage?
In my project, we mainly used Explicit Wait because different elements loaded at different times. This allowed us to wait only for the required element instead of applying a global wait to every element, making our automation scripts more stable and efficient.

### 38.What is pageLoadStrategy and when would you change it?
pageLoadStrategy controls how long Selenium waits for a page to load after navigation. It has three options: NORMAL, EAGER, and NONE. NORMAL waits for the complete page to load and is the default strategy. EAGER waits only until the HTML document is loaded, while NONE does not wait for the page to load at all. In my project, we used the default NORMAL strategy because it provided reliable execution, and we used Explicit Waits to handle dynamic elements. I would consider EAGER if page load time became a bottleneck and the test did not depend on images or other static resources

### 39.Did you change the pageLoadStrategy in your project?
No, we used the default NORMAL strategy because it suited our application. We relied on Explicit Waits for synchronization. However, I understand when EAGER or NONE can be useful in improving execution time for specific applications.

### 40.How do you handle browser cookies, local storage and session state?
Cookies, local storage, and session storage are used by browsers to store user information. In Selenium, I manage cookies using WebDriver methods such as getCookies() and deleteAllCookies(). For local storage and session storage, I use JavaScriptExecutor because Selenium does not provide direct APIs for them. In my project, I mainly used cookies by clearing them before test execution to ensure a clean browser session. I understand how to access and clear local storage and session storage using JavaScript when required.

### 41.How do you handle shadow DOM element?
In my project, I didn't encounter Shadow DOM elements because our application used standard HTML elements. However, I understand that if an application uses Shadow DOM, Selenium 4 provides the getShadowRoot() method to access elements inside it. In earlier versions, JavaScriptExecutor was used to access the shadow root.

### 42.What is the difference between an iframe and a Shadow DOM?
For an iframe, I switch the WebDriver context using switchTo().frame(). For a Shadow DOM, I access the shadow root using getShadowRoot() because the elements are encapsulated within the same page.

### 43.How do you handle Webtables in selenium?
I handle web tables by first locating the table and then identifying its rows and columns using XPath or CSS selectors. Depending on the requirement, I can retrieve all the data, validate specific cell values, count rows and columns, or perform actions like clicking an Edit or Delete button in a particular row. For dynamic tables, I avoid hardcoded row numbers and use dynamic XPath based on unique values such as an employee name or booking ID. This makes the automation more reliable and maintainable.

### 44.How do you identify a specific row?
I use a unique value such as an employee name, order ID, or booking ID to locate the row dynamically using XPath.

### 45.What is the difference between a static and a dynamic web table?
A static web table has a fixed number of rows and columns, while a dynamic web table changes based on the application's data, such as search results, bookings, or orders. For dynamic tables, I use dynamic locators instead of fixed row indexes.
 
### 46.How do you upload and download files using selenium?
In my project, we configured the download folder using browser options in our Selenium framework. After clicking the download button, we verified that the file was downloaded successfully by checking the configured folder. Because the filename included a timestamp and changed on every execution, we validated the download using the common filename prefix instead of an exact filename. For uploads, we used Selenium's sendKeys() method to provide the file path directly to the file input element.

### 47.How do you know the file download is completed?
After clicking the download button, I wait until the file appears in the configured download folder. Then I verify that the file exists and, if required, validate its name, size, or content.

### 48.How do you test links, including broken links?
In my project, we mainly verified that links navigated to the correct pages as part of functional testing. We didn't have a dedicated automation script to validate all broken links, but I know that broken link validation can be automated using Selenium along with Java's HttpURLConnection by checking the HTTP response code.

### 49.Can Selenium itself identify a broken link?
No. Selenium can only retrieve the URL and click the link. To determine whether the link is broken, I use Java's HttpURLConnection to check the HTTP response code.

### 50. Why do we use HttpURLConnection instead of clicking every link?
Using HttpURLConnection is faster because it directly checks the server's HTTP response without loading the entire webpage. This makes broken link validation more efficient, especially when a page contains many links.

### 51.How do you use selenium Grid for remote and parallel execution?
In my project, we didn't use Selenium Grid. We achieved cross-browser execution by passing the browser through the command line and reading it from our framework configuration. We mainly ran tests on Chrome and Edge. However, I know that if the project needs faster execution across multiple browsers or machines, Selenium Grid is the preferred solution because it supports remote and parallel execution.

### 52.What is the difference between TestNG parallel execution and Selenium Grid?
TestNG Parallel Execution:
->Runs multiple tests in parallel on the same machine.
->Improves execution speed using multiple threads.
Selenium Grid:
->Runs tests in parallel across different machines, browsers, and operating systems.
->Uses RemoteWebDriver to execute tests remotely.

### 53.What are the selenium relative locators and when would you use them?
In my project, we mostly used IDs, CSS Selectors, and XPath because they were sufficient for locating elements. We did not have a requirement to use Relative Locators. However, I understand that they are useful in Selenium 4 when elements are positioned relative to each other and don't have stable attributes.

### 54.What is the difference between WebElement.getText(), getAttribute(), getDomAttribute() and getDomProperty()?
getText() returns the visible text displayed on the page. getAttribute() returns the value of an HTML attribute and, in some cases, the current property value. getDomAttribute() returns the original attribute value defined in the HTML, whereas getDomProperty() returns the current value of the DOM property, which may change after JavaScript execution or user interaction. In my project, I mainly used getText() and getAttribute() for validations, while I know getDomAttribute() and getDomProperty() are useful when distinguishing between the original HTML value and the current runtime value.

### 55.What is the difference between browser options, capabilities and preferences?
Browser Options, Capabilities, and Preferences are all used to configure the browser before launching it. Browser Options control browser-specific behavior, such as headless mode, incognito mode, or starting maximized. Capabilities define browser and platform information and are mainly used for Selenium Grid or remote execution. Preferences are browser-specific settings like download location, notification settings, and password manager configuration. In my project, we mainly used ChromeOptions and EdgeOptions along with browser preferences to configure the download folder and disable browser pop-ups.

### 56.What are the different Selenium timeout types?
Selenium provides five main timeout types: Implicit Wait, Explicit Wait, Fluent Wait, Page Load Timeout, and Script Timeout. Implicit Wait is a global wait for locating elements. Explicit Wait waits for a specific condition and is the most commonly used in real projects. Fluent Wait extends Explicit Wait by allowing custom polling intervals and exception handling. Page Load Timeout controls how long Selenium waits for a page to load, while Script Timeout controls how long Selenium waits for asynchronous JavaScript execution. In my project, we mainly used Explicit Wait because it gave us better control over dynamic elements.

### 57.How do isDisplayed(), isEnabled() and isSelected() differ?
isDisplayed() checks whether an element is visible on the webpage. isEnabled() checks whether the element is enabled and ready for user interaction. isSelected() checks whether a checkbox, radio button, or option is currently selected. In my project, I used isDisplayed() for UI validations, isEnabled() before clicking buttons, and isSelected() to validate checkboxes and radio buttons.

### 58.What is WebDriver BiDi and why is it useful?
In my project, we didn't use WebDriver BiDi because our automation requirements were covered by standard Selenium WebDriver. However, I understand that BiDi is useful for capturing browser events, monitoring network traffic, and collecting console logs without relying on browser-specific DevTools

### 59.How should assertions be designed in selenium tests?
Assertions should validate the expected business outcome of a test case. They should be clear, reliable, and placed after the relevant user action. I avoid asserting every intermediate step and instead verify the final result, such as a successful login, correct page title, product details, cart count, or confirmation message. I also use Explicit Waits before assertions on dynamic elements to improve test stability. In my project, I mainly used TestNG assertions like assertEquals(), assertTrue(), and assertFalse().

### 60.What is the difference between Hard Assert and Soft Assert?
In my project, we mainly used Hard Assertions because each test case validated one specific scenario, and there was no need to continue execution after a critical validation failed. We used Soft Assertions only when multiple independent validations needed to be performed within the same test.

### 61.Should selenium PageFactor be used in a modern framework?
In my project, we followed the Page Object Model and stored locators using By objects. We used Explicit Waits before interacting with elements, so we did not use PageFactory. This approach made our framework simpler to maintain and worked well with dynamic web elements.

### 62.How do you design reusable waits without hiding failures?
I design reusable waits by creating common utility methods for frequently used wait conditions, such as waiting for an element to become visible or clickable. This avoids duplicate code and improves maintainability. I also make sure not to catch and ignore exceptions inside these methods because that hides the real failure. Instead, I allow the TimeoutException to propagate so the test fails at the correct point with a clear error message. In my project, we followed this approach using reusable Explicit Wait methods."

### 63.Why shouldn't you catch all exceptions in a wait method?
Because it hides the root cause of the failure. If a wait fails but the exception is ignored, the test may continue and fail later with a misleading error. Allowing the exception to propagate helps identify the actual synchronization issue quickly.

### 64.What information should selenium automation log?
In my project, we used Log4j2 for logging. We logged browser launch, URL navigation, important user actions such as login and checkout, validation steps, and exceptions. On test failures, our framework captured screenshots and attached them to the Extent Report. This made it much easier to identify and debug failures.

### 65.Q1. Why do we need logging if we already have Extent Reports?
Extent Reports provide a user-friendly execution summary with screenshots, while logs contain detailed execution steps and exception information. When debugging a failure, both are useful—the report shows what failed, and the logs help explain why it failed.

### 66. Which logging framework did you use?
In my project, we used Log4j2 for application and framework logging. It allowed us to log different levels such as INFO, WARN, ERROR, and DEBUG, making troubleshooting much easier.

### 67.What is NoSuchElementException? When have you faced it?
NoSuchElementException occurs when Selenium is unable to locate an element using the given locator. This can happen if the locator is incorrect, the element has not loaded yet, or the element is inside a frame that hasn't been switched to.
In my project, I first verified the locator in the browser's Developer Tools. If the locator was correct, I added an Explicit Wait to wait until the element became visible. In some cases, I updated the XPath because the application's DOM had changed.

### 68.What is TimeoutException?
TimeoutException occurs when Selenium waits for a condition using Explicit Wait, but the condition is not satisfied within the specified timeout period.I checked whether the locator was correct, verified that the page loaded completely, and confirmed that the wait condition matched the application's behavior. If necessary, I increased the timeout value after confirming the application response time.

### 69.What is ElementClickInterceptedException?
ElementClickInterceptedException occurs when another element, such as a popup, loading spinner, or overlay, blocks the target element from being clicked.I waited for the overlay to disappear using an Explicit Wait. If required, I scrolled the element into view before clicking it.

### 70.What is ElementNotInteractableException?
ElementNotInteractableException occurs when Selenium finds the element, but it cannot interact with it because it is hidden, disabled, or not yet ready for interaction. I verified that the element was visible and enabled before interacting with it. I also used elementToBeClickable() to ensure it was ready.

### 71.Which Selenium exception did you face most often?
The most common exceptions I encountered were NoSuchElementException and StaleElementReferenceException. These usually occurred due to dynamic page loading or DOM updates, and I resolved them using Explicit Waits, stable locators, and by locating the element again after the DOM changed.

### 72.When do you use alertIsPresent()?
I use it before switching to a browser alert to avoid NoAlertPresentException.

### 73.When do you use frameToBeAvailableAndSwitchToIt()?
I use it when a frame may take time to load. It waits for the frame to become available and switches to it automatically.


SCENARIO
---------
### 74.The element is present but Selenium cannot click it. What will you do?
I would check if another element is covering it, wait until it becomes clickable, scroll it into view if needed, and then try clicking again.

### 75. Your locator worked yesterday but not today. What will you do?
I would inspect the element in the browser to see if its attributes or structure have changed. If necessary, I would update the locator to make it more stable.

### 76. Your test fails with StaleElementReferenceException. How will you fix it?
I would locate the element again after the page refresh or DOM update instead of reusing the old WebElement reference.

### 77. Your click works locally but fails in Jenkins. Why?
I would check whether the browser is running in headless mode, verify synchronization using Explicit Waits, review browser and driver versions, and analyze the execution logs and screenshots to identify environment-specific issues.

### 78.A Selenium click fails with ElementClickInterceptedException. How do you diagnose and fix it?
ElementClickInterceptedException occurs when Selenium finds the target element, but another element is blocking the click. To diagnose the issue, I first identify what is intercepting the click, such as a loading spinner, popup, modal dialog, sticky header, or cookie banner. Then I apply the appropriate solution based on the root cause instead of using JavaScript click immediately.
I encountered click issues mainly due to loading overlays and dynamically loaded elements. I resolved them by using Explicit Waits, waiting for the overlay to disappear, and ensuring the element was clickable before performing the click. 

### 79.Why shouldn't you immediately use JavaScript click?
Because JavaScript click bypasses the browser's normal user interaction. If the click is blocked by a real application issue, using JavaScript click may make the test pass while hiding a genuine defect. I always identify and fix the root cause first, and only use JavaScript click as a last resort when there is a known application limitation.

### 80.A test fails with NoSuchElementException even though the element is visible manually. What do you check?
NoSuchElementException means Selenium could not locate the element using the given locator. If I can see the element manually, I don't assume the locator is wrong immediately. I follow a systematic debugging approach to identify the root cause and verified the locator using Developer Tools. Most of the time, the issue was caused by dynamic page loading, so I added an Explicit Wait for the element to become visible. In a few cases, the application's DOM had changed, and I updated the XPath to make it more stable. This resolved the NoSuchElementException.

### 81.Can you simply catch the StaleElementReferenceException and retry?
Retrying can work in some cases, but I don't rely on it as the primary solution. I first synchronize the test using an Explicit Wait and then locate the element again. Simply retrying without understanding why the DOM changed can lead to flaky tests.

### 82.A test times out waiting for a spinner to disappear, but the page looks complete. How do you debug it?
In my project, I first verified the spinner locator and confirmed whether the application hid or removed the spinner after loading. I also checked if another overlay was still present. Instead of waiting only for the spinner, I preferred waiting for the next page element, such as a results table or button, to become visible. This made the synchronization more reliable and reduced flaky failures.

### 83.Why is waiting for the next page element often better than waiting for the spinner?
Because the spinner is only an indicator of loading, and its behavior can vary between applications. Waiting for the actual element that the test needs—such as a table, button, or success message—directly verifies that the page is ready for the next action. This makes the test more stable and less dependent on the implementation of the loading spinner.

### 84.A test opens a payment window, but Selenium remains on the original page. How do you handle it robustly?
Although my project didn't include an external payment gateway, I handled multiple windows for scenarios such as opening product details or external pages. I always stored the parent window handle, waited for the new window to open, switched using the window handle, completed the required actions, and then switched back to the parent window. This approach made the tests stable and avoided NoSuchWindowException.

### 85.Why do you wait for the number of windows instead of switching immediately?
Because the new window may take a moment to open. If I try to switch immediately, Selenium may still see only one window, which can lead to failures. Waiting until the expected number of windows is available makes the test more reliable.

### 86.An iframe is reloaded during a test and subsequent element actions fail. What do you do?
Although my project didn't have an iframe that reloaded frequently, I worked with iframe-based pages. Whenever I interacted with elements inside an iframe, I first switched to the frame. If the frame refreshed, I switched back to the default content, waited for the iframe to become available again using frameToBeAvailableAndSwitchToIt(), switched into it, and located the elements again before continuing. This made the tests stable and prevented frame-related failures.

### 87.Why can't you reuse the old WebElement after the iframe reloads?
When the iframe reloads, its DOM is recreated. The old WebElement references point to elements from the previous DOM, so Selenium can no longer interact with them. That's why I locate the elements again after switching back into the refreshed iframe.

### 88.What exception might occur if you try to use the old element after the iframe reloads?
Most commonly, I may get a StaleElementReferenceException because the element belongs to the old DOM. In some cases, if I haven't switched back into the iframe, I may also encounter a NoSuchElementException.

### 89.Which ExpectedCondition would you use to handle this scenario?
ExpectedConditions.frameToBeAvailableAndSwitchToIt() is the best choice because it waits for the iframe to become available and switches into it automatically, reducing synchronization issues.

### 90.A dropdown option is visible but Selenium Select throws UnexpectedTagNameException. Why, and how do you automate it?
UnexpectedTagNameException occurs when we use Selenium's Select class on an element that is not an HTML <select> tag. Many modern applications use custom dropdowns built with <div>, <ul>, or <li> elements, and the Select class only works with <select> elements.

### 91.A file-download test passes locally but fails on Selenium Grid. How do you fix it?
The first thing I check is where the file is actually being downloaded. In Selenium Grid, the browser runs on a remote machine or container, so the downloaded file is not stored on my local machine. Therefore, checking my local download folder will fail.

### 92.Why can't you verify the file in your local Downloads folder?
Because Selenium Grid executes the browser on a remote node. The downloaded file is stored on that remote machine, not on the machine running the test script.

### 93.An automated login test fails only when run after another test. How do you identify the dependency?
we ensured that each test launched a fresh browser session and performed login independently. This prevented dependencies between test cases and improved reliability.

### 94.How do you avoid dependencies between tests?
I make each test independent by creating its own test data, starting with a fresh browser session, clearing cookies if needed, and avoiding reliance on the execution order of other tests.

### 95.A test fails only at a smaller browser resolution. Is it an automation defect or a product defect?
we usually executed tests in a maximized browser. If a smaller resolution caused failures, I would first reproduce the issue manually. If the application behaved incorrectly, I would raise a defect. If only the automation failed because the element was outside the viewport, I would update the script by scrolling to the element before interacting with it.

### 96.How do you scroll to an element if it's outside the viewport?
I can use JavaScriptExecutor to scroll the element into view before performing the action.

### 97.How would you automate a page with data that loads continuously as the user scrolls?
My project didn't have infinite scrolling, but if I encounter it, I would use JavaScriptExecutor to scroll, Explicit Waits to wait for new records, and validate that additional data has loaded before continuing.

### 98.How do you know when to stop scrolling?
I stop scrolling when the required record is found or when the number of records no longer increases after scrolling, indicating that all available data has been loaded.

### 99.A CAPTCHA appears in the automated test environment. What should you do?
Selenium should not be used to solve CAPTCHA because CAPTCHA is specifically designed to block automated interactions. The recommended approach is to bypass or disable it in the test environment.

### 100.A test occasionally clicks the wrong row action in a changing table. How would you fix it?
Instead of clicking a button based on its position in the table, I locate the row using a unique value such as Order ID or Username, and then click the action button within that specific row. This prevents failures when the table order changes.

### 101.Why shouldn't you use row indexes?
Because the table order can change due to sorting, filtering, or new records being added. Using unique business data makes the automation more reliable.

### 102.A Selenium suite leaves many Chrome processes running after failures. How do you correct it?
This usually happens when the browser is not closed properly after a test failure. I ensure that driver.quit() is always executed in the cleanup method, such as @AfterMethod or @AfterClass, even if the test fails.

### 103.The test clicks Save twice because the first response is slow. How would you prevent a duplicate record?
I would ensure that Selenium performs only one click and then waits for the application's response.In my project, after clicking buttons like Login or Checkout, we used Explicit Waits for the next expected state instead of clicking again. This prevented duplicate submissions.

### 104.Would you use JavaScript click if the first click is slow?
No. If the click has already been performed, using JavaScript click again may create duplicate records. Instead, I wait for the application's response and verify the result.

### 105.The browser displays an SSL certificate warning in the test environment. What do you do?
My project didn't face SSL certificate warnings, but if it happened in the QA environment, I would configure the browser to accept insecure certificates instead of manually bypassing the warning.

### 106.Should you ignore SSL warnings in Production?
No. Production should use valid SSL certificates. Accepting insecure certificates is only appropriate for controlled test environments.

### 107.A test fails because a toast message disappears too quickly. How do you validate it reliably?
we validated dynamic success messages using Explicit Waits instead of fixed delays. This allowed us to capture the toast message before it disappeared and reduced flaky failures.

### 108.Why shouldn't you use Thread.sleep() for toast messages?
Thread.sleep() waits for a fixed amount of time and may either miss the toast if it disappears quickly or unnecessarily slow down the test. Explicit Waits respond as soon as the toast appears, making the test faster and more reliable.

### 109.A browser notification permission popup blocks the test. How do you handle it?
In my project, we configured browser options before launching Chrome to disable notification popups. This prevented browser permission dialogs from interrupting our automated tests.

ChromeOptions options = new ChromeOptions();
Map<String, Object> prefs = new HashMap<>();
prefs.put("profile.default_content_setting_values.notifications", 2);
options.setExperimentalOption("prefs", prefs);
WebDriver driver = new ChromeDriver(options);

### 110.Why don't you automate clicking 'Allow' or 'Block'?
Because it's a browser-level popup, not an application element. Configuring the browser before execution is more reliable than trying to interact with the popup after it appears.

### 111.The application uses Basic Authentication before loading the login page. How would you automate it?
My project didn't use Basic Authentication. If it did, I would use Selenium 4's authentication support or request a test environment where authentication is handled outside the UI so that the automation remains secure and maintainable.

### 112.Should usernames and passwords be hardcoded in the script?
No. Credentials should be stored securely, such as in a configuration file, environment variables, or a secure secrets manager, and never hardcoded into the test scripts.

### 113.The test passes, but screenshots are attached to the wrong tests during parallel execution. What is the cause and fix?
Our framework was designed for thread safety by maintaining separate WebDriver instances for each test. If screenshots were attached incorrectly, I would verify that both the driver and reporting objects are managed using ThreadLocal.

### 114.Why is ThreadLocal important?
ThreadLocal ensures that each parallel test thread has its own WebDriver and report object, preventing interference between simultaneously running tests.

### 115.A UI test fails because test data already exists from an earlier run. How would you redesign it?
In my project, we tried to make each test independent. We avoided depending on existing records and created fresh test data whenever possible.

### 116.Why shouldn't tests share data?
Because shared data creates dependencies between tests. One test may change or delete data that another test expects, leading to inconsistent and unreliable results.

### 117.Selenium finds two elements with the same ID. How would you handle and report it?
If I encountered duplicate IDs, I would temporarily use a more reliable locator to continue automation, while simultaneously raising a defect so the developers could correct the HTML.

### 118.Is duplicate ID an automation defect?
No. Duplicate IDs are an application defect because they violate HTML standards. The automation script can work around it temporarily, but the application should be fixed.

### 119.A test requires scrolling, but scrollIntoView() places the button under a sticky header. What is your fix?
In my project, if an element was hidden behind a sticky header after scrolling, I adjusted the scroll position using JavaScript before clicking the element.

### 120.Can Actions class also help?
Yes. The Actions class with moveToElement() can bring the element into view naturally. If that isn't sufficient, JavaScript scrolling with an offset provides better control.

### 121.A test fails only when the application is translated into another language. How do you make it robust?
A test fails only when the application is translated into another language. How do you make it robust?

### 122.If text-based XPath is the only available locator, what would you do?
I would first discuss with the development team about adding a stable attribute such as data-testid or a unique ID. If that isn't possible, I would maintain language-specific locators carefully, but this would be my last option because it's harder to maintain.
