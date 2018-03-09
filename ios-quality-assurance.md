# PROJECT QUALITY ASSURANCE #

The idea behind this document is to have a reference of how to create, develop and maintain an iOS project in Karumi.

These are no hard rules, but we encourage them as we wrote this document based on our experience doing consultancy projects and in-house project.

Although this document is written having in mind that the reader will be using Swift, most of the advice can be easily adapted to Obj-C.

## Feature kickstart ##

We all love to start new features. These are a few questions you should ask in order to prevent future delays.

* Is the design ready?
    - [ ] Is there any style guide? If not, ask why?
    - [ ] Are all the assets exported included placeholders? If not, ask.
    - [ ] Is the design prepared for devices with different sizes? If not, ask why.
    - [ ] Is the visual design ready for corner case data (long names or numbers, etc.)? If not, point it out.
* Localization
    - [ ] Are the sentences for this feature defined? If no, require them; if they are, consider if there is enough room to display them, especially the dynamic ones (the ones which will be displaying usernames, amount of money, etc.)
* Are the error scenarios well defined?
    - [ ] There is no internet connection, what this feature would do?
    - [ ] Our server is down, how the app should behave?
    - [ ] Are all the business error handled? If not, should they be?
* Server-side integration.
    - [ ] Is the API defined/available? If not, try to do it, at least explain how the model would look.

## Issues ##

### Reporting ###
A fix starts with the issue report. Take your time to do it, indicate what’s going on and what was expected instead.

* Add screenshots/video of the issue.
* Indicate how to reproduce it.
* Indicate if the bug is blocker or can be bypassed by the user (this will help with its triage)
* Try to identify when this bug started to happen.
* Attach any crash report related and the URL to the crash tracking system.

### Fixing ###

* Try to reproduce it. 
    * If it’s fixed, indicate when it was resolved.
    * If not, ask for more information on the ticket.
* Attach media resources (images videos) showing how it looked like after your fix.
* Briefly explain what was happening.
* Add tests to assure that the scenario described above shouldn’t happen again.
* Keep track of this issue in the following release to check if it’s fixed if not, update information and reschedule this issue fix.

## Pull requests ##

### Asking for review ###

Don’t forget you are not your code, the point of establishing a PR process is gathering feedback about how to improve the product you are working.

* Try to fix just one thing at a time.

* Use the template you can find in this repo where you’ll have to introduce the issue you are fixing/developing; what was needed and why the implementation is the way it is.

* Indicate how it can be tested, ideally it should be in an automatic way, but if not, explain why and the tests the reviewer will have to perform in order to check it’s working as expected.

* Indicate how it should be tested by hand. You might have forgotten some scenarios, and the only way to find them out is using exercising that code.

* Be respectful to your colleagues and answer or at least ACK all their comments.

### Reviewing ###

Think that nobody does their job poorly on purpose (or at least not the most of us). If something is not looking good, try to figure out why almost always there is a reason.

* The best way to have all the context is not the web tool used for PR, checkout the branch and open it.

* Try to understand why it’s done the way it is before suggesting changes.

* Don’t forget that this is about code quality, no about being right. Your comments or suggestion can be declined if there are reasons for so.

* If you can, provide snippets of code showing your idea/suggestion, it’s usually better to discuss it.

* Try to review the PR you have been asked to, your opinion may be relevant, that every developer wants to see their job reflected in the product. The longer a PR is open, the higher the possibility to get conflicts at merge time.


## Continuous integration ##

Consider continuous integration the source of truth. If something is working on your machine, but not in CI, fix it.

* Run all the tests (unit, integration and UI ones) for a PR.
* Setup your CI output to inform about possible errors (Build logs, execution logs, screenshots diffing)

## CVS ##

* Try to use a feature/fix branch approach, no one should code directly on master/develop.

* Create a branch for release tentatives, and those branches will be alive while the release is being checked, any change related to that release should be done following the same feature branch approach, but having that release branch as reference branch.

* Do not track more code than needed.

* Setup a proper ignore file, a good example for Swift can be found [here:] (https://github.com/github/gitignore/blob/master/Swift.gitignore)

## Project tooling ##

### Lint ###

Be sure that the code styles is consistent across the whole project.

* SwiftLint

### Tests ###

It’s important to verify that our app is doing what is suppose to do for that we can use:

* Verification: [Nimble](https://github.com/Quick/Nimble), [SwiftCheck](https://github.com/typelift/SwiftCheck), [ios-snapshot-test-case](https://github.com/uber/ios-snapshot-test-case/)
* HttpStubs: [OHHttpStub](https://github.com/AliSoftware/OHHTTPStubs)

### Code generation ###

If some parts of the code can be generated automatically, let’s do that.

* Miscellanea: [Sourcery](https://github.com/krzysztofzablocki/Sourcery)
* API integration: [Swagger](https://github.com/swagger-api/swagger-codegen)

### CI/Integration ###

As said before, CI environment is mandatory for every project.

* Tool: [Fastlane](https://fastlane.tools)
* CI platform: [Bitrise](https://www.bitrise.io/) seems to be working fine for iOS and Android.

### Crashes ###

Keep track of how the app behaves in production.

* [Fabric](https://get.fabric.io) is the tool we’ve been using the most.

### Distribution ###

Distribute often; it’s an excellent way to gather feedback. For instance, we aim to deploy a weekly beta to our clients. This has wider implications that you could expect: 

- Issues need to be defined to be fitted in one week.
- Feedback cycle is high enough to detect issues.
- Bugs are discovered early.

* [Testflight](https://developer.apple.com/testflight/) works perfectly and can be integrated with Fastlane