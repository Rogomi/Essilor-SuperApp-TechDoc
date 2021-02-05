[Back](../index.md)

# My Transitions Android

## Technical Documentation

### GETTING STARTED

//Todo:

### INSTALLATION AND DEVELOPMENT

In order to start the development, first, you need to start Android Studio. Import the Transitions-World project and then wait for the build to finish.

### PROGRAMMING LANGUAGE

My Transitions uses Kotlin for development

### MINIMUM VERSION

My Transitions can run on Android Systems with minimum SDK version 26. It may encounter multiple issues on lower SDK versions.

### APPLICATION ID

dev.transitions.iris.app

### DEBUGGING

We use Android Virtual Device in Android Studio in order to test the Native Apps in different screen sizes and SDK Versions.

### THIRD-PARTY LIBRARIES

Most of the third-party libraries are integrated using Gradle. They can be added by searching library names found in the Dependencies tab in the Project Structure window.

#### Important Libraries

- **Firebase/Crashlytics** - used to report crashes from Users that are not encountered during development and debugging.
- **Coroutine** - is a concurrency design pattern that you can use on Android to simplify code that executes asynchronously.
- **Retrofit** - is type-safe REST client for Android and Java which aims to make it easier to consume RESTful web services.

### IMPORTANT CLASSES

#### Main Utilities

- **RetrofitBuilder** - a class which contains the network settings (i.e timeout span).
- **AppPreferences** - handles the storing of simple data such as user name, if user login, etc.
- **ApiService** - a class which contains the endpoints call. what kind of httprequest, the parameters to be passed, response type.
- **ApiEndpoint** - a class which contains the constant endpoint strings
- **GoogleSignInHelper** - a class which contains methods for handling the Google SSO
- **CalendarEndpoint** - a class that contains Google Calendar endpoint strings
- **CalendarService** - a class that contains calls for a Google Calendar API request

#### Activities/Fragments

- **LoginActivity** - handles the Google login page
  ##### Methods
  - `initActions()` - initialize the Google sign in button
  - `onLoginSuccess(account: GoogleSignInAccount)` - called when the Google sign in is successful
  - `goToMain()` - redirects the application to the MainActivity
  
- **MainActivity** - container of fragments and controls the main bottom navigation
  ##### Methods
  - `initNavigation()` - initialize bottom navigations
  
- **PodcastsFragment** - handles the list of podcast by category
  ##### Methods
  - `initPodcasts()` - calls the list of podcasts to the server
  - `onPadcastSelected()` - opens the PodcastPlayerFragment
  - `onGetPodcastsPercategory()` - render the list of podcast returned from the server
  
 - **PodcastPlayerFragment** - handles the podcast player
  ##### Methods
  - `runService()` - initialize the service that controls the player from the background
  - `updatePlayerButton()` - update the player buttons
  - `updatePosition()` - update the time of playing audio in the seekbar
  
- **CalendarFragment** - handles the calendar page
  #### Methods
  - `onEventsSuccess(eventHolder: EventHolder)` - called when the fetching of the events from the API is successful
  - `initCalendar()` - initializes the calendar's UI and data binding
  - `filterEvents(): ArrayList<EventHolder.Companion.Event>` -returns the filtered events from the Google Calendar API by the current selected date
  - `initAdapter()` - binds the filtered events to the UI
  
  
### DIAGRAM

//Todo:

#### **Model**

In an application with a good layered architecture, this model would only be the gateway to the domain layer or business logic. See it as the provider of the data we want to display in the view. Model’s responsibilities include using APIs, caching data, managing databases and so on.

#### **View**

The View, usually implemented by an Activity, will contain a reference to the presenter. The only thing that the view will do is to call a method from the Presenter every time there is an interface action.

#### **Presenter**

The Presenter is responsible to act as the middle man between View and Model. It retrieves data from the Model and returns it formatted to the View. But unlike the typical MVC, it also decides what happens when you interact with the View.
