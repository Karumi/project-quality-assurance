# Design Collaboration Guidelines

As app developers, one of our top priorities should always be to create implementations that match as much as possible the designs. To accomplish this goal, we need to define a standard vocabulary between the design team and us. Designers are, more and more, integrating design systems as part of their work, and we can benefit from that to build common ground. **Here we define the minimum standard requirements to keep consistency and the usual forgotten pieces of app design.** Independently of the size of your team, there is already a set of best practices applied by your designer that you can benefit, and others you will need anyway at some point while developing the app itself.

* [A Comprehensive guide to design systems](https://www.invisionapp.com/blog/guide-to-design-systems/)

## Style guide - Foundation
These are the basic styles that will serve as the foundation of all the other part of the design. The style guide will be helpful to avoid the mistake of not using the proper element as part of the application UI. Regardless if you follow material design, fluent design or any other guidelines, these style elements will facilitate tasks such as design adjustment and rebranding.

### Color Palette
A list of all the color used in the app with a name associated.

![color palette](./assets/color-palette.png)

* [SwiftGen Colors](https://github.com/SwiftGen/SwiftGen#colors)
* [Asset catalog colors on Xcode 9](https://blog.zeplin.io/asset-catalog-colors-on-xcode-9-c4fdccc0381a)
* [Android Resources Color](https://developer.android.com/guide/topics/resources/more-resources.html#Color)
* [Material Guidelines Color System](https://material.io/guidelines/style/color.html#color-color-system)

### Typography - Fonts
A list of Fonts and Size. When possible, a complete style guide including color and format should also be provided.

![typography](./assets/typography.png)

## Layout

### Sizing and Spacing
Defining base templates that respect ratio and size of most used or more common devices that will be used. And a general rule for padding or margin that you can apply to most, if not all, of the app screens. Include general rules when spacing values are constant (e.g., 8dp) or if something has to be centered or positioned relative to other views.

![layout ios](./assets/layout-ios.png)

![layout android](./assets/layout-android.png)

### Size Classes - Responsive UI

Interface elements and layouts can be configured to automatically change shape and size on different devices, during multitasking on a tablet, in split view, when the screen is rotated, and more.

* [Size Classes and Core Components](https://developer.apple.com/videos/play/wwdc2017/812/)
* [Responsive UI](https://material.io/guidelines/layout/responsive-ui.html)
* [Adaptivity and Layout](https://developer.apple.com/ios/human-interface-guidelines/visual-design/adaptivity-and-layout/)

## Components - Pattern library - Atoms
Different design systems will have different naming for it, in Atomic Design you will call this Atoms, in others, it's just called Pattern Library, or Components. All these building blocks should be based on the style guide and will be used to build more complex elements of user interface like pages and screens.

Commons components  you can find in most applications are:
* Labels
* Inputs
* Buttons

### Animations

Views can contain animations they are generally under two categories, animated views or animated assets.

Animated views allow in general the following change of properties as animation point:

* Size.
* Position.
* Transform: scale, rotate, or translate.
* Color and transparency.

Animated assets are used for loaders or visual description of first use or empty case. They are defined with a motion graphic tool like Adobe After Effects and integrated into the app with a framework like Lottie. 

[View Programming Guide for iOS > Animations](https://developer.apple.com/library/content/documentation/WindowsViews/Conceptual/ViewPG_iPhoneOS/AnimatingViews/AnimatingViews.html)
[Lottie](https://airbnb.design/introducing-lottie/)

## Interaction Model - Patterns

### Navigation
As today most of the mobile apps are single window full-screen design, in collaboration with the designer, it's essential to review a prototype of the navigation with the design of the App using tools like Marvel or Invision.

There are mainly two ways to navigate from one screen to another:

* Stack: You will find this concept under Navigation Stack or Back Stack under the respective platform. You can quickly identify these screen through the fact that they have a Back/Up Button on the top left Corner.
Important: Remind UX and Product Owner that navigation from a notification should keep into account the stack designed to get to the desired screen.

![navigation stack](./assets/navigation-stack.png)

* Modal/Dialog, It's a screen that sits on top of the current screen, the user must interact with it before they can return to the previous screen. It should contain text and UI controls focused on a specific task. They inform users about critical information, require users to make decisions, or involve multiple tasks. You could identify them as they have at least a cancel button or a close button.
Important: Remind UX and Product Owner a Modal could not be initial screen as they have a dismiss button.

* [Best Practices for Modals / Overlays / Dialog Windows](https://uxplanet.org/best-practices-for-modals-overlays-dialog-windows-c00c66cddd8c)

![navigation stack](./assets/modal.png)

### Screen transitions

If in the navigation prototype no screen transitions are described, ensure with UX and Product Owner that native transitions from the platform will be applied. And if any custom transitions are described, they should include at least duration and easings curves used. 

## Empty States
An essential step while design and estimating how complicated a screen is, is to define its empty states.

* [Designing For The Empty States](https://tympanus.net/codrops/2013/01/09/designing-for-the-empty-states/)
* [Material Guidelines Empty States](https://material.io/guidelines/patterns/empty-states.html)

### First use
Explain to the user functionality of the app, generally shown the first time that user uses the app, or it can appear until the user makes the first interaction that generates content.

### User Cleared
Shown to the user that clear the content of the screen is shown.

### Error Cases
Indicate to the user that the App wasn't able to load the content of the page.

### Placeholder
Placeholder is needed mainly in two cases: 

* When displaying images provided from a remote source, if not set yet or while loading.
* Form input fields to describe the expected value. 

## Loading cases
While reviewing the UI, let the UX and Product Owner know which interactions with users will generate load content or perform lengthy data processing operations. Use activity indicators and progress bars to let people know your app isn’t stalled and to give them some idea of how long they’ll be waiting.

A general guideline is to show a loader:
 * When a user interaction blocks the UI, like validating a form through a remote API call.
 * When loading background content could take more than 1 ms

![components progressactivity behavior](./assets/components-progressactivity-behavior-loading-files-circular.gif)

![activity indicators](./assets/activity-indicators.gif)

## Tooling

This guideline does not come with a recommendation of tooling, the ones that we tested and used in projects until now are:

* [Zeplin](https://zeplin.io/)
* [InVision](https://www.invisionapp.com/)
* [Marvel App](https://marvelapp.com/)