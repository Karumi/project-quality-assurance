# Project Quality Assurance

The goal of this repository is to define a general guidance for Android projects quality assurance at Karumi.

## Pull requests

* Guide the reviewers on how to test the new feature, the screens that are affected, how to access them. If there is any context requirement (user logged in, malfunctioning API, etc) specify how did you test it.

* All pull requests must have screenshots of the new screens or UI changes if any. It is recommended to show changes on different devices and resolutions (small phones, tablets).

* Specify if there are changes in any DB schema and how the evolution is being performed.

* If there is any change on how the app communicates with the server, link to the documentation of the endpoint being used.

* Include new permissions being requested to users.

# Issues

* Always include visuals on how the screen should look like (wireframes, mocks, etc).

* Add or link all your new assets to the issue.

* Contemplate common error scenarios such as no internet access, no permissions, etc.

* Include all the translation keys that are needed to implement the new features. Always include the english copy.

* Recommended tags for your issues besides the common ones: _UI_, _DB_, _API_.

# Continuous Integration

* Besides what's mandatory for every other project, in Android it's also required to:

  * Verify your UI is being rendered correctly

  * Check your API integration

* You can use _ktlint_ and _detekt_ for linting purposes.

* UI tests can be written in _Espresso_ (functional approach) or _Shot_ (Snapshot based).

* Use _MockWebServer_ to check your API integration.

* The CI environment should be used to upload new beta versions to your preferred service (Google Play, Fabric, etc)

# Repository

* Include a linting configuration.

* Ideally, your project should contain an _EditorConfig_ file so that it's easier to work with other developers around different environments.

# Project

* Use one of the many tools to keep track of crashes and errors like _Crashlytics_.
