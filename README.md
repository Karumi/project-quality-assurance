# Project Quality Assurance

The goal of this repository is to define a general guidance for tech projects quality assurance at Karumi.


## Pull requests

* Pull requests are **mandatory**, even if you are alone in the project.

* At least one reviewer's approval is required to merge a pull request (depending on the size of the team, having more reviewers is desirable).

* Use a template to describe **what** are you trying to solve with your code and **why** are you doing it in that way. If you don't have a template yet and you are using Github, feel free to use [the following one](PULL_REQUEST_TEMPLATE_1.md)
or [a more details versions](PULL_REQUEST_TEMPLATE_2.md).


* Pull requests have to be linked to a CI service that automatically validates your code.

* All new features have to include tests for the feature. If none are created for time reasons, create an issue to later tackle the problem.

* All bugfixes have to include a test that verifies that the bug has been addressed.

* Do not add *TODO* nor *FIXME* comments to PRs, create issues for that matter.

* If you are developing a project with visual content, always include screenshots/videos.

# Issues

* Issues have to describe a feature or bug in detail with no ambiguity. 

    * **In case of a feature**: Explain what is the expected outcome and the cases you want to cover. Include potential error scenarios and, when applicable: translation keys, designs, assets, etc.

    * **In case of a bug**: Describe the steps you have to follow to reproduce it. Include a severity level.

* Tag your issues, *enhancement* and *bug* are the most common tags but you can use the ones that better fit your project.

* Include a responsible of the issue when possible.

* Use a template (file *.github/ISSUE_TEMPLATE.md*). [Feel free to use this one](ISSUE_TEMPLATE.md).


* Organize your issues with your preferred project manager tool. If you are using Github, the projects tab might work just fine. Create at least 4 phases for issues: *TODO, WIP, REVIEW* and *DONE*.

# Continuous Integration

* It is mandatory to verify:

    * That your project compiles

    * Your tests are passing 

    * There are no linting issues

    * Checkstyle

    * Database migrations and configuration files are working

* It is optional to store information about the following points to keep track of the evolution of the project:

    * Calculate tests code coverage

    * Run other static analysis tools such as complexity metrics

* When applicable, your CI service should be the one deploying new versions when merging your pull request. That doesn't mean that manual releases can't be done by the person responsible of the project.

# Repository

* Include a *.gitignore* file to avoid uploading build, temporal or local configuration files.

* Protect your *master* branch so that no one can commit directly on it.

* Include a *README.md* file describing, at least, all the steps required to compile, run the project and all the tests.

* All projects should be runnable in local (docker is the best option for backend projects) for both, development and testing.

* Tag your public releases. Publish the release in Github and include a description of the main features you included in the release.

* Do not ever upload sensitive information to your repository such as API keys, users, passwords or certificates unless you are forced to (Terraform or mobile certificates can be stored in private repositories).

# Project

* Create alarms for backend services, the most simple one will just send a request to a health endpoint to see if it works.

* Log crashes and errors to keep track when things go south.

* Every project must have a way to revert a release in case something goes wrong.

* Use a tool to keep track of milestones, deadlines, releases and the like.

* Keep track of the decisions you make for the project in a document.

* Every meeting need outcomes, future tasks and assignees, no exceptions.

**Projects will have when possible two or more developers working on it in order to enforce these requirements.**

