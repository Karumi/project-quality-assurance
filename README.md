# Project Quality Assurance

The goal of this repository is to define general guidance for tech projects quality assurance at [Karumi](http://karumi.com/). **This document describes the guidelines we follow for every single project**, for more in-detail steps and rules applied to specific platforms, you can read the following READMEs:

* [Android](./android-quality-assurance.md)
* [iOS](./ios-quality-assurance.md)

## Pull requests

* Pull requests are **mandatory**, even if you are alone in the project. The usage of pull requests improves the way the history of the project evolves so we can better understand how and why something was implemented. Additionally, this practice helps developers review the content of a pull-request before merging a branch and consider it as done.

* At least one reviewer's approval is required to merge a pull request (depending on the size of the team, having more reviewers is desirable).

* Use a template to describe **what** are you trying to solve with your code and **why** are you doing it in that way. If you don't have a template yet and you are using Github, feel free to use [the following one](PULL_REQUEST_TEMPLATE_1.md)
or [a more details version](PULL_REQUEST_TEMPLATE_2.md).

* Pull requests have to be linked to a CI service that automatically validates your code. Depending on the project you are working on, different continuous integration services can be used. We recommend you to use one where the CI configuration is versioned in the project repository itself.

* All new features have to include tests for the feature. If none are created for time reasons, create an issue to later tackle the problem, but remember, sending the PR with the production code and the tests evaluating the correct implementation of the production code at the same time is desirable.

* All bugfixes have to include a test that verifies that the bug has been addressed. This will help you avoid regressions, so once you fix the bug and add the test, you won't face the same bug again.

* Do not add *TODO* nor *FIXME* comments to PRs, create issues for that matter.

* If you are developing a project with visual content, always include screenshots/videos. Sometimes these resources can be generated automatically using a testing strategy known as "visual regression testing" or "screenshot testing".

## Issues

* Issues have to describe a feature or bug in detail with no ambiguity.

  * **In case of a feature**: Explain what is the expected outcome and the cases you want to cover. Include potential error scenarios and, when applicable: translation keys, designs, assets, etc.

  * **In case of a bug**: Describe the steps you have to follow to reproduce it and what's the expected behavior. Include:
  
    * A severity level.
    
    * The version of the app or the project where the bug is reproduced.
    
    * The scenario or the special conditions to reproduce the error.

* Tag your issues, *enhancement* and *bug* are the most common tags, but you can use the ones that better fit your project.

* Include a responsible for the issue when possible.

* Use a template (file *.github/ISSUE_TEMPLATE.md*). [Feel free to use this one](ISSUE_TEMPLATE.md).

* Organize your issues with your preferred project management tool. If you are using GitHub, the projects tab might work just fine. Create at least 4 phases for issues: *TODO, WIP, REVIEW* and *DONE*. Before moving an issue to the **DONE**  column, you should review with your team what **DONE** means. For some teams, merging a branch could be considered as **DONE**, others won't consider a task as done until the new version is released to the final users.

## Continuous Integration

* Before merging a branch, it is mandatory to verify:

  * That your project compiles.

  * Your tests are passing.

  * There are no linting issues.

  * Checkstyle.

  * Database migrations and configuration files are working.

* It is optional to store information about the following points to keep track of the evolution of the project:

  * Calculate tests code coverage.

  * Run other static analysis tools such as complexity metrics.

  * When applicable, your CI service should be the one deploying new versions when merging your pull request automatically. That doesn't mean that manual releases can't be done by the person responsible for the project.

## Repository

* Include a *.gitignore* file to avoid uploading build, temporal or local configuration files.

* Protect your *master* branch so that no one can commit directly to it.

* Include a *README.md* file describing, at least, all the steps required to compile, run the project and all the tests.

* All projects should be runnable in local ([Docker](https://www.docker.com/) is the best option for backend projects) for both, development and testing.

* Tag your public releases. Publish the release in Github and include a description of the main features you included in the release.

* Do not ever upload sensitive information to your repositories such as API keys, users, passwords or certificates unless you are forced to (Terraform or mobile certificates can be stored in private repositories).

## Project

* Create alarms for backend services, the most simple one will just send a request to a health endpoint to see if it works.

* Log crashes and errors to keep track when things go south.

* Every project must have a way to revert a release in case something goes wrong.

* Use a tool to keep track of milestones, deadlines, releases and the like.

* Keep track of the decisions you make for the project in a document.

* Every meeting need outcomes, future tasks, and assignees, no exceptions.

**Projects will have when possible two or more developers working on it to enforce these requirements.**

## License

    Copyright 2018 Karumi

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


