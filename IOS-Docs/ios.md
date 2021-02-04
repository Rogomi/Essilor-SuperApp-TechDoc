[Back](../index.md)

# My Transitions iOS
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
#### Linked Libraries
**AdSupport.framework** - Used for Google Analytics  
**AppTrackingTransparency.framework** - Required by apple for iOS 14 and above to allow the user to decide whether they let the app have access to IDFA or not.

#### Cocoapods
Most of the third party libraries are installed using CocoaPods. They can be added by searching library names found in https://cocoapods.org/, inserting them in the Podfile and running the pod install command in the Terminal.

##### Important Libraries
**Alamofire** - For Web API Communications  
**SwiftyJSON** - To ease up processing of response data  
**ObjectMapper** - To easily create models for response data

##### Firebase Platform Libraries.
**Firebase/Analytics** - Used for App Analytics  
**Firebase/Crashlytics** - Used to identify causes of crashes from users

##### UI Libraries
**IQKeyboardManagerSwift** - To automatically scroll up the UITextView on screen when the keyboard is up.  
**IBAnimatable** - To easily add special UI Designs on specific views, and see them reflected on the Interface Builder. Also has methods to animate views.  
**SDWebImage** - To easily load Images from URL and has caching functions.  
**MBProgressHUD** - Used to add heads up display on screen to indicate loading while user is waiting for data to be loaded from the API  
**JTAppleCalendar** - Used for the Calendar module
**FlagKit** - Used for profile country
##### Other Useful Libraries 
**ReachabilitySwift** - Used to check internet connection status   
**SwiftDate** - Used to easily process Date objects in swift   
**Fakery** - To easily create dummy data.   
**GoogleSignIn** - Used to sign in to Google
**GoogleAPIClientForREST/Calendar** -  To connect to Google Calendar
**SwiftAudio** - Used to play podcasts
**SkeletonView** Used to display a loading view for incoming data

### ACTIVITIES AND CONTROLLERS

#### Core Classes

#### View Controllers

- **AppTabBarController** - manages the app access, redirects to Login screen when user is not logged in.    
  ##### Methods
  - `openLogin()`
  - `clearTabs()`
  - `gotToLanding()`

- **AuthViewController** - contains functions that allows the user to sign in via their Google account. Handles offline error and checking user credentials  
  ##### Methods
  - `ssign(... didSignInFor user: GIDGoogleUser!)`
  - `showOfflineAlert()`
  - `validDomain()`
  - `showInvalidEmailAlert()`

- **UserSocialProfileViewController** - contains functions that displays a specific user's profile information and timeline for activities, groups and comments.
  ##### Methods
  - `didTapBackButton(_ sender: Any)`
  - `didTapOverflowButton(_ sender: Any)`
  - `numberOfSections(in tableView: UITableView)`
  - `tableView(... numberOfRowsInSection section: Int)`
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`

- **LikesViewController** - contains functions that displays list of users that liked a social item (Posts, Comments, Podcast, etc.)
  ##### Methods
  - `didTapCloseButton(_ sender: Any)`
  - `tableView(... numberOfRowsInSection section: Int)`
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`

- **CommentsViewController** - contains functions that displays list of comments and their specific replies.
  ##### Methods
  - `didTapCloseButton(_ sender: Any)`
  - `numberOfSections(in tableView: UITableView)`
  - `tableView(... numberOfRowsInSection section: Int)`
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`

- **CalendarViewController** - contains functions that handle the Calendar Screen, which allows the user to view their work calendar and see the event for the selected date  
  ##### Methods
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`
  - `configureCalendar(...)`
  - `calendar(... cellForItemAt date: Date,...)`
  - `getList(date: Date)`
  - `getEventsByDate(date: Date)()`

- **PodcastDashboardViewController** - controls the podcast dashboard
  ##### Methods
  - `getPodcastCategories(only: Bool)`
  - `tableView(... numberOfRowsInSection section: Int)`
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`
  - `tableView(... estimatedHeightForRowAt indexPath: IndexPath)`
  - `numSections(in collectionSkeletonView: UITableView)`
  - `collectionSkeletonView(... numberOfRowsInSection section: Int)`
  - `collectionSkeletonView(... didSelectRowAt indexPath: IndexPath)`

- **PodcastSearchViewController** - contains functions that allows the user to search through podcasts
  ##### Methods
  - `getPodcasts()`
  - `getFilteredPodcast()`
  - `didTapCancelButton(_ sender: Any)`
  - `editingChanged(_ sender: UITextField)`
  - `tableView(... numberOfRowsInSection section: Int)`
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`

- **PodcastPlayerViewController** - contains functions that allows the user to play podcasts
  ##### Methods
  - `didTapOverflowButton(_ sender: Any)`
  - `didTapCloseButton(_ sender: Any)`
  - `didTapLikes(_ sender: Any)`
  - `didTapComments(_ sender: Any)`
  - `togglePlay(_ sender: Any)`
  - `previous(_ sender: Any)`
  - `next(_ sender: Any)`
  - `startScrubbing(_ sender: UISlider)`
  - `scrubbing(_ sender: UISlider)`
  - `scrubbingValueChanged(_ sender: UISlider)`
  - `updateTimeValues()`
  - `updateMetaData()`
  - `setPlayButtonState(forAudioPlayerState state: AudioPlayerState) `
  - `handleAudioPlayerStateChange(data: AudioPlayer.StateChangeEventData)`
  - `handlePlayerFailure(data: AudioPlayer.FailEventData)`

- **PodcastCategoryViewController** - contains functions that allows the user to view podcasts in a category
  ##### Methods
  - `didTapCloseButton(_ sender: Any)`
  - `getFilteredPodcast()`
  - `didTapCancelButton(_ sender: Any)`
  - `editingChanged(_ sender: UITextField)`
  - `tableView(... numberOfRowsInSection section: Int)`
  - `tableView(... cellForRowAt indexPath: IndexPath)`
  - `tableView(... didSelectRowAt indexPath: IndexPath)`  
  
- **PodcastDetailsViewController** - controls the display of podcast information details  
  ##### Methods
  - `didTapCloseButton(_ sender: Any)`
  
### APPLICATION FLOW DIAGRAM

