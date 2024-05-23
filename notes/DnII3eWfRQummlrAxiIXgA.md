# Cypress vs Selenium vs Playwright: The best Automated-Testing Tool

Automation testing is a software testing paradigm where tests are run automatically using a tool or a script. It differs from manual testing where a human verifies an application’s functionality by interacting with an interface or supplying values to an executable program. The testing tool used in automated testing has two major components, a test runner and a tracking agent. The test runner runs the test from a command (or button click) while the tracking agent keeps track of passing and failing tests. These testing tools apply to different types of software testing which include unit, integration, and end-to-end (e2e) testing.

When it comes to frontend web application testing, one can choose to test the code or test an end user's behavior while using the app. One can gain more value testing a user's behavior because it doesn't focus on implementation details. This is a form of e2e testing and there are several tools for carrying out such testing. These include Cypress, Selenium, and Playwright. This article compares these three tools using metrics such as browser support, language support, ease of setup, and performance. The purpose of this comparison is to enlighten you on the best tool for your use-case based on the mentioned metrics.

## What is Automated testing?

Automated testing is a testing technique that involves the use of software tools in executing test cases. It oftentimes involve test cases written in a scripting language such as Python, Javascript, or Lua. The scripts are written to test the different functionalities of a piece of software.
Automated testing can be seen as a process of automating manual test cases, that is, using software tools to execute test cases that would have been executed manually. The goal of automated testing is to reduce the amount of manual work involved in test execution leading to higher test coverage. Some benefits of automated testing are faster feedback, improved test coverage, greater accuracy, and Reusability among others.

Automated testing isn’t another testing paradigm similar to unit and functional testing. It is more or less a way to automate unit, integration, and end-to-end tests. There are diverse automated testing tools available for different types of testing needs, but this article focuses on end-to-end testing using: Selenium, Cypress, and Playwright.

### Use-Cases of Automated Testing
1. Cross-browser testing
2. Load and performance testing
3. Automating unit, integration, and end-to-end tests


## Comparing Cypress, Selenium, and Playwright as Automated Testing Tools

You will now look at a comparison of Cypress, Selenium, and Playwright based on: browser support, ease of setup, ease of scripting, performance, speed

### Based on Browser Support
Browser support refers to the ability of a certain website or web app to function consistently on different web browsers (Chrome, Mozilla Firefox, Safari, and Microsoft Edge). If your favourite automated testing tool can work across major browsers, you can have peace of mind that your app works no matter the browser choice of your users. The essence of considering browser support is that cross-browser testing is one of the major tests carried out by testers and devs. Now, take a look at all three automated testing tools in terms of browser support.

Cypress: Cypress supports major browsers like Chromium and Firefox. [It has experimental support for Safari](https://docs.cypress.io/guides/guides/launching-browsers#WebKit-Experimental). This means some features will not work properly. Asides this, it has good support on Chrome, Firefox, and Edge. It can run tests across multiple browser versions directly from the Cypress test runner which makes it convenient to run tests on older browser versions, maintained versions, and unreleased versions.
![Cypress browser selector](https://i.imgur.com/5NMO9RH.png)

Selenium: Selenium supports popular web browsers including Google Chrome, Mozilla Firefox, Safari, Microsoft Edge, and Internet Explorer (Edge IE mode). It achieves this through the Selenium webdriver which acts as a bridge between test scripts and a chosen browser. There is no single webdriver, as each browser type has its own webdriver. Available webdrivers include:


- [ChromeDriver](https://chromedriver.chromium.org/downloads) for Google Chrome.
- [GeckoDriver](https://firefox-source-docs.mozilla.org/testing/geckodriver/index.html) for Mozilla Firefox.
- [EdgeDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) for Microsoft Edge.
- [IE Driver Server](https://www.selenium.dev/documentation/ie_driver_server/) for Internet Explorer.

Selenium's support for a wide range of browsers makes it the most suitable tool for testing web applications on different browsers. The only downside is the requirement of downloading each browser and its webdriver.

Playwright: Like Selenium, Playwright supports multiple browsers including Firefox, Chromium-based browsers, and Safari using a single API. It provides a unified API for automating web browsers. This makes it an effective tool for cross-browser testing and automation. Playwright defines this cross-browser testing behavior in a configuration file `playwright.config.js`. The content of the file responsible for the cross-browser testing looks is structured as shown below:
```js
module.exports = defineConfig({
  /* Configure projects for major browsers */
  projects: [
    {
      name: "chromium",
      use: { ...devices["Desktop Chrome"] },
    },
    {
      name: "firefox",
      use: { ...devices["Desktop Firefox"] },
    },
    {
      name: "webkit",
      use: { ...devices["Desktop Safari"] },
    },
    /* Test against mobile viewports. */
    {
      name: "Mobile Chrome",
      use: { ...devices["Pixel 5"] },
    },
    {
      name: "Mobile Safari",
      use: { ...devices["iPhone 12"] },
    },
  ],
});
```
So once a user invokes a test using `npx playwright test`, playwright executes the available tests automatically in all the browsers defined. After the tests are completed, it opens up a summary in the local browser to show the tests that passed and those that failed in all the respective browsers. The image below shows the browsers Playwright downloads during it’s installation process on Linux. 
![Supported browser](https://imgur.com/V7eOQyj.png)
In terms of browser support, of the three, Selenium is the most suitable automated testing tool because it has comprehensive browser coverage. Though there are certain factors to consider when it comes to choosing an automated testing tool based on browser support, Cypress and Playwright are good options for Chromium-based browsers but Selenium is the best option.
|                 | Cypress | Selenium | Playwright | Winner                 |
| --------------- | ------- | -------- | ---------- | ---------------------- |
| Browser support | 4/5     | 5/5      | 5/5        | Selenium or Playwright |

### Ease of Scripting
An automated testing tool is controlled using a form of scripting. This scripting functionality can be implemented in a known programming language like Python or a custom domain-specific language. The tools in this article support different languages to different degrees. This section analyzes the ease of writing scripts for automated testing with Playwright, Cypress, and Selenium. 

Cypress: Cypress only supports scripting in Javascript. This has its pros and cons. For the pros, only supporting Javascript means that Cypress will have a singular way of achieving a task. This makes it easy for someone new to the tool to get productive because many other users would have encountered the same issue. The major con in a singular support for Javascript means that a developer or tester that isn’t familiar with JavaScript syntax will have to learn the language before getting productive writing tests with Cypress. As for the scripting API, Cypress makes it easy to easily write queries, assertions, and actions using methods such as `cy.get`, `cy.<element>.should`, and `cy.<element>.click`. `<element>` here refers to an element obtained from a [cypress query](https://docs.cypress.io/api/table-of-contents#Queries). The script below is a simple automated testing script written for Cypress in JavaScript. It opens Google.com and searches for “cat memes”. It then verifies that the search was successful. Cypress’ simplicity enables this script to be written in 11 lines or less if you remove the describe block.

```js
describe("Search for cat memes on Google", () => {
  it("visits google and searches for cat memes", () => {
    cy.visit("https://google.com");
    cy.get('textarea[name="q"]').type("cat memes");
    cy.get('form[role="search"]').submit();
    cy.title().should("contain", "cat memes");
  });
});
```
Selenium: Selenium allows you to write scripts in multiple languages, from common scripting languages like Python and Javascript to more business oriented languages like Java and C#. Selenium supports multiple languages because it has a wide community of adopters and has been in existence the longest. Writing scripts in certain languages is easier than others partly due to the structure of the language, and partly due to the availability of well-maintained libraries and frameworks for Selenium in those languages. Find below the same script as the Cypress case that searches for cat memes on Google search implemented in JavaScript for Selenium.
```js
const { Builder, Browser, By, Key, until } = require("selenium-webdriver");
(async function testGoogleSearch() {
  let driver = await new Builder().forBrowser(Browser.CHROME).build();
  try {
    await driver.get("https://www.google.com");
    await driver.findElement(By.name("q")).sendKeys("cat memes", Key.RETURN);
    await driver.wait(until.titleIs("cat memes - Google Search"), 1000);
  } finally {
    await driver.quit();
  }
})();
```
Playwright: Playwright similar to Selenium supports more than one language. It has official support for [Javascript/Typescript, Python, Java, and .NET](https://playwright.dev/docs/languages). Its API is more page-oriented. This mean selectors (locators in this case) start from the `page` object, which is passed as an argument. Playwright’s JavaScript API focuses on human readability, making tests easier to write. It’s explicit use of the await syntax might seem verbose, but it makes it obvious that a task may take some time to complete. This flows with Selenium’s approach and differs from Cypress automatic await. The snippet below is code for searching for cat memes on Google Search, written for Playwright using JavaScript.
```js
import { test, expect } from "@playwright/test";
test.describe('Search for cat memes on Google"', () => {
  test("visit google and searche for cat memes", async ({ page }) => {
    await page.goto("https://google.com");
    const searchBox = page.locator("textarea[name='q']");
    await searchBox.fill("cat memes");
    await searchBox.press("Enter");
    await expect(page).toHaveTitle("cat memes - Google Search");
  });
});
```
Here’s the summary of how the three testing tools rank up to each other:
|                       | Cypress | Selenium | Playwright | Winner                 |
| --------------------- | ------- | -------- | ---------- | ---------------------- |
| Browser support       | 4/5     | 5/5      | 5/5        | Selenium or Playwright |
| Ease of scripting     | 2/5     | 5/5      | 4/5        | Selenium               |

### Ease of Setup
Similar to how a user will leave a website if it takes too long to load, a potential QA tester may abandon a tool if it is too difficult to set up. Fortunately, none of the testing tools in this guide are difficult to set up. However, you should have in mind which of these tools is the easiest to set up.

Cypress: Cypress comes as an npm package and a [standalone downloadable application](https://docs.cypress.io/guides/getting-started/installing-cypress#Direct-download) that you can immediately install and write tests with. After installation, you only add a new project, choose a browser of choice, and start writing test cases in JavaScript.
![Cypress project view](https://imgur.com/pJbvM4o.png)
Setting up Cypress as an npm package is equally straightforward. You add it to your project using `npm install cypress --save-dev` and start up the application using `npx cypress open`. From there, you can skip the project initialization and go straight to picking a browser and running example tests or writing new ones.

Playwright: Playwright is set up from the command line, using an npm command: `npm init playwright`. This initialization step is an interactive workflow that asks you to choose your desired scripting language (Javascript or Typescript), the location of your test scripts, and whether to include a Github Actions Workflow for CI.

After these prompts, you can write new tests or run existing example tests using the command: npx playwright test. Playwright also includes a UI mode that is accessed using the `--ui` flag when invoking it using npm.
![Playwright UI mode](https://imgur.com/tEURhbH.png)
Aside from Playwright’s dependency on Node.js, it simplifies browser setup/connection by downloading the required testing browsers in the local directory. This means that even if you do not have the required browsers installed, you can still run Playwright tests.
![Playwright’s supported browsers](https://i.imgur.com/ItgZnIH.png)

Selenium: Selenium has the most involved setup among the three tools. For starters, you need to have the drivers for the browsers you want to test with. So if you wish to test your applications with Chrome and Firefox, you will need to have both browsers installed alongside their selenium webdrivers. This tedious setup process can be abstracted by the client library, giving you a straightforward way of running your tests. However, this convenience is not present in all Selenium client libraries. 

Here’s the summary of how the three testing tools rank up to each other:
|                       | Cypress | Selenium | Playwright | Winner                 |
| --------------------- | ------- | -------- | ---------- | ---------------------- |
| Browser support       | 4/5     | 5/5      | 5/5        | Selenium or Playwright |
| Ease of scripting     | 2/5     | 5/5      | 4/5        | Selenium               |
| Ease of set up        | 5/5     | 2/5      | 4/5        | Cypress                |

### Based on performance and speed
It's important to think about how well an automated testing tool works and how fast it is before picking one. This helps make sure the tool fits with what the project needs, what the team can handle, and the project's long-term goals.

Cypress: Cypress is generally known for its faster-than-average execution time. This is most likely the case because it executes commands inside the target browser. It doesn't use an external driver like Selenium does but injects JavaScript code into the browser. The injected code then does all the DOM node parsing and manipulation to achieve the testing goal. Also, Cypress provides a feature called Parallelization. This feature allows Cypress to execute many tests simultaneously. While Selenium also supports parallel test execution, Cypress' direct test execution model makes it faster.

Selenium: Selenium's architecture, which relies on a driver for different browsers adds a lag to its test execution speed and performance. This dependency on drivers does not exist for both Cypress and Playwright. Selenium works by creating a separate driver instance for each browser session. So if a user tries to execute tests in parallel, Selenium will create as many web driver instances as browsers involved. This architecture puts Selenium behind Cypress and Playwright despite its versatility.

Playwright: Like Cypress, Playwright offers fast execution by leveraging its unified API feature. Playwright by default runs tests on Chromium, Firefox, and Webkit. It can do this because it installs these browsers during its installation process. Playwright does not fail when tests are flaky because it ensures that elements are visible before proceeding with tests. Playwright’s major contender when it comes to Performance and speed is Cypress because it has a similar simplified architecture. Both Playwright and Cypress have Node.js as a dependency, unlike Selenium that has a broader community of supported frameworks.

Here’s the summary of how the three testing tools rank up to each other:

|                       | Cypress | Selenium | Playwright | Winner                 |
| --------------------- | ------- | -------- | ---------- | ---------------------- |
| Browser support       | 4/5     | 5/5      | 5/5        | Selenium or Playwright |
| Ease of set up        | 5/5     | 2/5      | 4/5        | Cypress                |
| Ease of scripting     | 2/5     | 5/5      | 4/5        | Selenium               |
| Performance and speed |     4/5    |     3/5     |     5/5       |           Playwright       

## Conclusion

In this article, you explored the concept of automated testing and learnt how it can be done with three prominent testing tools: Cypress, Selenium, and Playwright. You explored how these testing tools differ in terms of their setup, scripting, performance, and speed. So while all these tools may be robust with good community support, you should always choose a tool that closely matches your use-case.


