[Back](../index.md)

# Essilor SuperApp iOS
## Technical Documentation



### GETTING STARTED
myTransitions iOS requires Xcode 11.0 and above for development. This project uses Swift 5 as the Programming Language, Storyboard for the Interface and CocoaPods for Third Party Libraries. The app also uses CoreData to store offline information. The current Xcode version used for development is 11.5. The minimum iOS Version required is iOS 11.0


### INSTALLATION AND DEVELOPMENT
In order to start with the development, first, you will need an Apple account for development. It must be under the team **Rogomi, Inc.** Then, open the **myTransitions.xcworkspace** under the repository root directory. If possible, do a **pods repo update** in order to avoid missing library errors.


### PROGRAMMING LANGUAGE 
myTransitions iOS uses the latest Swift version, Swift 5, for development.


### MINIMUM VERSION 
myTransitions iOS requires devices with at least iOS 12.0


### APPLICATION ID
dev.transitions.iris.app


### DEBUGGING
We use a few debugging tools to test myTransition’s functionalities.  

For the Native App, we use Xcode's debugging console to create breakpoints and test variables, API responses, and identify null objects which sometimes causes the crash.

To test the API before integrating for app usage, we use [Postman](https://www.getpostman.com/). Postman is a very reliable REST API tool. We can test different HTTP Methods especially POST, PATCH, PUT, DELETE and GET. We can also add header variables to test SSO and token authentications.

We also use iOS Simulator in order to test the apps in different screen sizes and iOS Versions.


### WEB API
Google Sign In API, Azure


### THIRD PARTY LIBRARIES
Most of the third party libraries are installed using CocoaPods. They can be added by searching library names found in https://cocoapods.org/, inserting them in the Podfile and running the pod install command in the Terminal.

#### Important Libraries
**Alamofire** - For Web API 
Communications
**SwiftyJSON** - To ease up processing of response data  
**ObjectMapper** - To easily create models for response data

#### Firebase Platform Libraries.
**Firebase/Analytics** - Used for App Analytics  
**Firebase/Crashlytics** - Used to identify causes of crashes from users

#### UI Libraries
**IQKeyboardManagerSwift** - To automatically scroll up the UITextView on screen when the keyboard is up.  
**IBAnimatable** - To easily add special UI Designs on specific views, and see them reflected on the Interface Builder. Also has methods to animate views.  
**SDWebImage** - To easily load Images from URL and has caching functions.  
**MBProgressHUD** - Used to add heads up display on screen to indicate loading while user is waiting for data to be loaded from the API  
**JTAppleCalendar** - Used for the Calendar module

#### Other Useful Libraries 
**ReachabilitySwift** - Used to check internet connection status   
**SwiftDate** - Used to easily process Date objects in swift   
**Fakery** - To easily create dummy data.   
**GoogleSignIn** - Used to sign in to Google


### ACTIVITIES AND CONTROLLERS

#### Core Classes

#### View Controllers


### APPLICATION FLOW DIAGRAM