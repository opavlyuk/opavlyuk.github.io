














Effective Testing Strategies:
A Guide to Unit, Integration, and End-to-End Tests
























Oleksandr Pavliuk





































"If it isn't tested, it doesn't work!"
				- Richard Stallman aka St IGNUcius
Abstract
The document provides a comprehensive overview of the key testing techniques used in software development to ensure high-quality, reliable, and secure applications. This guide covers the principles, best practices, and real-world examples of unit, integration, and end-to-end testing, enabling developers to adopt these strategies in their projects effectively. By following this guide, development teams can significantly reduce the number of defects in their software, leading to increased customer satisfaction, improved product performance, and reduced development costs.
	In this document "testing" refers to testing by the developer, which typically consists of unit tests and integration tests but can sometimes include regression tests and end-to-end tests. Numerous additional kinds of testing are performed by specialized test personnel and are rarely performed by developers. These kinds of testing are not discussed further in this guideline.


Conformance


All terms in this document, including “unit testing”, “integration testing”, “end-to-end testing” etc are to be interpreted as described in [ISTQB Glossary].
Context and problem

In the complex world of software development, defects are an inevitable part of the process. Studies have shown that even experienced developers produce an average of 10 to 50 defects per 1,000 lines of code. These defects can lead to software malfunctions, security vulnerabilities, and unsatisfactory user experiences.
In fact, research indicates that nearly 85% of software projects experience cost overruns, often due to defects and the time required to fix them. Furthermore, the cost of fixing a defect increases exponentially as the project progresses, making early detection crucial for minimizing expenses and delays.
	


Solution


Testing plays a critical role in this process by identifying defects, validating functionality, and ensuring that the software delivers a consistent and satisfying user experience. Testing by the developer is a key part of a full testing strategy. Approximate defect-detection rates based on historical data and research are 15-50% for unit testing, 30-60% for integration testing and 40-70% for end-to-end testing.
	Please keep in mind that even considering the numerous kinds of testing available, testing is only one part of a good software-quality program. High-quality development methods, including minimizing defects in requirements and design, are at least as important. Collaborative development practices are also at least as effective at detecting errors as testing, and these practices detect different kinds of errors.


General considerations
In Binariks we profess the Test Pyramid way of thinking on the tests. Please find more on the practical view of the topic in Practical Test Pyramid and Fixing test hourglass. If you’re still doubting, please check On the Diverse And Fantastical Shapes of Testing.

Automated testing is still testing. Please get yourself familiar with basic test case design techniques:
https://sysgears.com/articles/test-design-techniques-overview/
https://www.lotus-qa.com/test-case-design-techniques/


Consider using tools to measure code coverage.


Use mutation testing to evaluate the quality of tests themself (more on the topic - Mutation Testing).


Consider revising your testing approaches if time spent on testing significantly exceeds the following average values for developer testing:

Check the documentation of your testing tools for test naming conventions.

Avoid test flakiness as the plague. Test flakiness in software development refers to the phenomenon where a test case or a suite of test cases produces inconsistent results when executed multiple times under the same conditions. A flaky test may pass in one run and fail in another, even though no changes have been made to the code, environment, or test parameters. This unpredictability makes it challenging to determine the root cause of a failure and can undermine confidence in the test suite. For more details please check  Test Flakiness - One of the main challenges of automated testing. Here you can find an almost exhaustive list of techniques on how to triage and treat that - Test Flakiness - One of the main challenges of automated testing (Part II). 

After addressing a bug that was not detected through automated testing, it is important to create targeted test cases for that specific scenario.

Keep track of test results over time to identify patterns and trends, such as flaky tests or recurrent failures, which can provide insights into potential issues in the application.

To supply test data for software testing, it's preferable to use fake data generators instead of hardcoded values.

Structure the code of your test according to the following logical sections:
Pre-conditions: carry out actions necessary to achieve the desired state of the system under test.
Steps: perform the call(s) that initiate the behavior being tested, ideally limited to a single call.
Checks: verify the test results by making assertions based on the expected outcomes.

Avoid god-tests. Ensure that each test focuses on a single aspect or behavior of the application. Keep tests small and concise - aim for short, clear, and easy-to-understand tests.

If you find it challenging to choose a short and concise name for your test case, consider splitting complex test scenarios into smaller, more manageable tests.

Unit testing


Unit testing (synonyms - component testing, module testing) is a test level that focuses on individual software components. The definition is rather broad and can refer to testing of units (components) of different levels (like routine, class, module, service etc), which are tested in isolation from the more complete system. In the current document we will cover only tests that check the code as it is written at the functional unit level.
	
When to write

	Unit tests are a fundamental aspect of software development and should only be skipped in exceptional cases.
	These exceptions may include:

Rapid prototyping: During the early stages of a project, when creating a proof of concept or prototype, it might not be practical to write unit tests. The focus at this stage is often on validating ideas and gathering feedback, and the code may change significantly in future iterations.
Legacy code: In cases where a codebase is old, poorly structured, or lacks proper documentation, writing unit tests might be challenging. Instead, it might be more appropriate to focus on higher-level tests, such as integration or system tests, to ensure the overall functionality of the software.

	The following ARE NOT exceptions:

Simple code: There is no code so straightforward that the chance of introducing bugs is minimal and writing unit tests might not be necessary.
Time constraints: When facing tight deadlines or limited resources, resist the urge to skip unit testing. Otherwise, you'll end up spending the same amount of time fixing issues right before or after the release, but with even more pressure.

What to test

It is crucial to ensure that the core routines representing the domain logic are covered with unit tests. Everything else is up to the developer.
	When developing software, it is generally safe to assume that certain components or aspects have already been tested, which can help reduce the testing scope and focus on the application-specific functionality. That includes third-party dependencies like operational systems, libraries and frameworks, programming languages themself, browsers and cloud services. However, you should still test the integration of these components with your application.
	Many companies, like Google, follow best practices that require any code changes to include corresponding unit test cases that pass. As the code base grows, having a collection of such tests executed before submitting code is crucial for catching bugs early. This saves time later in writing integration tests, debugging, and verifying fixes to existing code.

Characteristics of a good unit test

Fast: It isn't uncommon for mature projects to have thousands of unit tests. Unit tests should take little time to run. Milliseconds.
Isolated: Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.
Repeatable: Running a unit test should be consistent with its results, that is, it always returns the same result if you don't change anything in between runs.
Self-Checking: The test should be able to automatically detect if it passed or failed without any human interaction.
Timely: A unit test shouldn't take a disproportionately long time to write compared to the code being tested. If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.

Key points

Unit tests are not only important for verifying the accuracy of the code but also for promoting a clean design of the functions or methods. Well-designed code is usually easy to test, and unit tests play a significant role in achieving this.


When testing at the unit level, we focus on specific routines that use test doubles of external dependencies. Though there exist a variety of terms to denote different types of testing scaffolding, to keep it simple and pragmatic here we stick to the approach described in  Testing on the Toilet: Know Your Test Doubles.
	Please follow Mocks Aren't Stubs by M. Fowler to learn more on the topic.


Integration testing
Integration tests evaluate whether separately developed software components function properly when interconnected with one another.
When to write


the codebase grows and reaches a point where numbers of functional units are available to test as a group;
exists interaction with external API’s or other services.
What to test
Focus on the points of connection between components. When designing test cases, carefully evaluate whether the tests could be performed at the unit level instead.

Key points
For the integration testing approaches check the article https://www.geeksforgeeks.org/software-engineering-integration-testing/.
Also, here are some typical mistakes developers make when writing automated integration tests:


Overlapping test scope: Writing integration tests that cover functionality already tested by unit tests can lead to redundancy, increased test execution time, and wasted effort.
Testing too many components at once: Attempting to test multiple components simultaneously can make tests complex, harder to maintain, and more challenging to diagnose in case of failures.
Ignoring test environment differences: Failing to account for differences between test and production environments can lead to tests passing in the test environment but failing in production due to configuration, infrastructure, or data discrepancies.
Overusing test doubles: Excessive use of mocks, stubs, or other test doubles can make tests too dependent on implementation details, reducing their ability to detect issues in the integration between components.


End-to-end testing
End-to-end testing is a way to check if a whole software system works properly from start to finish. It tests how the software behaves in real-life situations, like how users interact with it and how it connects to other parts of the system, like databases and APIs.

When to write


	With end-to-end tests, you have to wait: first for the entire product to be built, then for it to be deployed, and finally for all end-to-end tests to run.
What to test
Base use cases from the user perspective should be tested on this stage. Often such cases are called Critical User Journeys.
	A critical user journey describes a set of interactions a user has with a service to achieve some end result. It is the combination of a critical goal and the journey of tasks a user undertakes to achieve that goal.

Key points
	
When making test cases, think like a user. Imagine you're using the app for the first time.
Refer to acceptance testing documents and user stories to understand the user's perspective.
Focus on testing app features where failure would cause the most problems in end-to-end tests.
Don't test exceptions in end-to-end tests. Instead, use integration tests or low-level unit tests for unusual user scenarios.

	For more details on the end-to-end testing, please follow https://www.browserstack.com/guide/end-to-end-testing.
	









