# Scala Server project Quality Assurance

The goal of this repository is to define general guidance for server-side projects written in Scala at Karumi. This document complements the [Project Quality Assurance](./README.md) with all the specifics we follow for server-side projects written in Scala.

## Feature kickstart

We all love to start new features. These are a few questions you should ask to prevent future delays.

* Are the feature functional and non-functional requirements ready?
  - [ ] Does the feature description include all the information needed to start designing the database usage?
  - [ ] Is it designed keeping in mind the format and structure of the data?
  - [ ] Can we reuse part of the already implemented platform?
  - [ ] Do the user stories describe the usage of the feature from the back office or the admin panel?
  - [ ] Does it include a description of different scenarios related to corner or edge cases?
  - [ ] Does it include any non-functional requirement related to performance or any resource usage?
  - [ ] Does it include examples needed to validate the feature form the acceptance criteria viewpoint?
  - [ ] In case of implementing any feature with any user interface component like emails or the back office user interaction, does the user stories provide links to the sketch design or assets?

* Localization
  - [ ] Are the translations for this feature defined? If no, require them; if they are, consider if there is enough room to display them, especially the dynamic ones (the ones which will be displaying usernames, amount of money, etc.)

* Are the error scenarios well defined?
  - [ ] The client is just sending the mandatory information, what this feature would do?
  - [ ] The client is not sending the data requested properly, what this feature would do?
  - [ ] Third-party services are down, how the server should behave?
  - [ ] Are all the business error handled? If not, should they be?

## Pull requests

* Guide the reviewers in how to test the new feature, the endpoints or sites that are affected, how to access them. If there is any context requirement (user logged in, malfunctioning third party service, etc) specify how did you test it.

  * All pull requests must have tests of the endpoints or screens showing UI changes if any.

  * If needed, specify if there are changes in any DB schema and how the evolution is being performed.

  * Review if any special index needs to be configured in order to improve the service performance. If this is the case, specify it and explain the reason why this index is needed.

  * We should indicate if any infrastructure change is required.

  * Breaking changes in public API endpoints are not allowed, pay an special attention to this when sending the PR.

  * If there is any change in how the platform communicates with other services, link to the documentation of the endpoint being used.

  * If there is any heavy task performed in the worker servers, specify how these tasks are going to be executed.

## Issues

* Always include specifications on how the service should be used.
  * Add or link all the specs where the usage of the endpoints is described.
  * Contemplate common error scenarios such as third-party services not responding, possible performance issues, etc.
  * Include all the translation keys that are needed to implement the new features. Always include the English copy.
  * List all the actions that have to be tracked in the new feature if applicable.
  * Recommended tags for your issues besides the common ones: _DB_, _API_, _STATS_, _INFRASTRUCTURE_.

## Fixing an issue

* Try to reproduce it.
  * If it’s fixed, indicate when it was resolved.
  * If not, ask for more information on the ticket.

* Attach media resources (images videos) showing how it looked like after your fix.
* Attach curl or postman example requests.
* Briefly explain what was happening.
* Add tests to assure that the scenario described above shouldn’t happen again.
* Keep track of this issue in the following release to check if it’s fixed if not, update information and reschedule this issue fix.

## Asking for review

Don’t forget you are not your code, the point of establishing a PR process is gathering feedback about how to improve the product you are working.

* Try to fix just one thing at a time.
* Use the template you can find in this repo where you’ll have to introduce the issue you are fixing/developing; what was needed and why the implementation is the way it is.
* Indicate how it can be tested, ideally it should be in an automatic way, but if not, explain why and the tests the reviewer will have to perform in order to check it’s working as expected.
* Indicate how it should be tested by hand. You might have forgotten some scenarios, and the only way to find them out is using exercising that code.
* Be respectful to your colleagues and answer or at least ACK all their comments.

## Reviewing

Think that nobody does their job poorly on purpose (or at least not the most of us). If something is not looking good, try to figure out why almost always there is a reason.

* The best way to have all the context is not the web tool used for PR, checkout the branch and open it.
* Try to understand why it’s done the way it is before suggesting changes.
* Don’t forget that this is about code quality, no about being right. Your comments or suggestion can be declined if there are reasons for so.
* If you can, provide snippets of code showing your idea/suggestion, it’s usually better to discuss it.
* Try to review the PR you have been asked to, your opinion may be relevant, that every developer wants to see their job reflected in the product. The longer a PR is open, the higher the possibility to get conflicts at merge time.

## Continuous Integration

* Besides what's mandatory for every other project, in server-side projects it's also required to:
  * Verify our changes does not introduce any breaking change in the public API.
  * If a database migration is needed, ensure the migration can be applied properly without increasing the platform downtime.

* You can use [scalafmt](https://github.com/scalameta/scalafmt) for linting and formatting purposes.
* Tests can be written in [ScalaTest](https://github.com/scalatest/scalatest) using other tools like [ScalaCheck](http://www.scalacheck.org/).
* Use embedded versions of the database or the caching system like [H2](http://www.h2database.com/), [embedded Redis](https://github.com/kstyrc/embedded-redis) or [WireMock](https://github.com/tomakehurst/wiremock) when possible. If for some reason, the usage of embedded third-party systems for testing purposes is not supported, remember to provide the infrastructure needed for the tests execution through a [Docker](https://docker.github.io/) configuration file.
* The CI environment should be used to upload new release versions to your preferred service (AWS, Heroku, Google Cloud, etc).

## CVS

* Include a linting configuration when possible.
  * Ideally, your project should contain an _EditorConfig_ file so that it's easier to work with other developers around different environments.
  * Try to use a feature/fix branch approach, no one should code directly on master/develop.
  * Create a branch for release tentatives, and those branches will be alive while the release is being checked, any change related to that release should be done following the same feature branch approach, but having that release branch as reference branch.
  * Do not track more code than needed.
  * Setup a proper ignore file, a good example for Android can be found [here](https://github.com/github/gitignore/blob/master/Scala.gitignore).

## Project tooling

### Lint and formatting

Be sure that the code styles is consistent across the whole project.

* [ScalaFMT](https://github.com/scalameta/scalafmt).

### Scheduled tasks, cron jobs, and queues

Scheduled tasks can be implemented for this type of projects using any cron job based tool like [AWS Elastic Beanstalk Periodic Tasks](https://aws.amazon.com/premiumsupport/knowledge-center/cron-job-elastic-beanstalk/). Keep in mind that the time zone used to schedule these task will be UTC and this can't be changed in AWS.

The usage of queues could be needed in order to speed up part of the platform response time. We recommend the usage of [AWS SQS](https://aws.amazon.com/sqs). Keep in mind the dead-letter queue configuration and the number of retries we should perform before considering as an unrecoverable failure.

### HTML rendering

The usage of a front-end web to implement the back office or the application user interface is quite common. For this purpose, the usage of a template system like [Twirl](https://www.playframework.com/documentation/2.6.x/ScalaTemplates) or [Scalate](https://github.com/scalate/scalate) could be helpful. The template engines can be also helpful for email or PDF rendering.

If for some reason you'd like to develop a single page application to consume the API developed by the main service we'd recommend you the usage of [React](https://reactjs.org) and [Redux](https://redux.js.org/) or any third party tool ready to consume a REST API like [admin-on-rest](https://github.com/marmelab/admin-on-rest).

### Migrations

Using SQL databases is quite common in our projects. As this type of databases requires migrations we strongly recommend the usage of a migration tool like [Flyway](https://github.com/flyway/flyway/) for this purpose. The usage of [this](https://github.com/flyway/flyway-sbt) sbt plugin could simplify the migrations execution.

### Code generators

The usage of code generators for boilerplate code could be really helpful. Generating the API specifications using any standard format and the code needed to consume the database are two common scenarios. The tools we use for this are:

* API specifications: [Swagger](https://swagger.io/).
* API clients code generation: [Swagger Code Gen](https://swagger.io/swagger-codegen/)
* Database access code generation: [Slick](http://slick.lightbend.com/) & [Slick Codegen](https://github.com/tototoshi/sbt-slick-codegen).

### Tests

It’s important to verify that our app is doing what is suppose to do for that we can use:

* Verification: [ScalaTest](https://github.com/scalatest/scalatest), [ScalaCheck](http://www.scalacheck.org/), and [Mockito](http://site.mockito.org/).
  * HttpStubs: [MockWebServer](https://github.com/square/okhttp/tree/master/mockwebserver) or [WireMock](http://wiremock.org/)
  * PDF Testing: [PDFUtil](http://www.testautomationguru.com/introducing-pdfutil-to-compare-pdf-files-extract-resources/).
  * Redis support: [Embedded Redis](https://github.com/kstyrc/embedded-redis).
  * Elastic MQ support: [Elastic MQ](https://github.com/adamw/elasticmq).
  * SQL support: [H2 database](http://www.h2database.com/)

### Crashes

Keep track of how the app behaves in production.

* [Rollbar](http://rollbar.com/) is the tool we’ve been using the most.

### Distribution

Distribute often; it’s an excellent way to gather feedback. For instance, we aim to deploy a staging version of the platform to clients after every push to master and production versions when needed. This has wider implications that you could expect:

- Issues need to be defined to be fitted in the release period.
- Feedback cycle is high enough to detect issues.
- Bugs are discovered early.

* [AWS Code Pipeline](https://aws.amazon.com/codepipeline) works perfectly and provides useful feedback.

## Project

* Use one of the many tools to keep track of crashes and errors like _Rollbar_ or _Sentry_.

* Create different configurable versions to point to different environments or support different behaviors of the software using simple config changes.

* Configure your debug and release builds.

* Always disable stats tracking while running tests or using your app from a development environment. The only safe way to do it is to specifically block tracking from your production code. In order to detect a test environment, you can test if there is any test class loaded.

