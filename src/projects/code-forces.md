---
title: 'Codeforces'
description: 'Codeforces is an unofficial Android version of Codeforces web. This app is made to integrate all the available Codeforces API into this app. This way the users can have a mobile version of their handle and can get key information on the go.'
date: '2018-06-30'
categories:
  - sveltekit
  - svelte
published: true
repo: https://github.com/Chromicle/Codeforces
---

[![Travis CI](https://travis-ci.com/chromicle/codeforces.svg?branch=master)](https://travis-ci.com/chromicle/codeforces)


## About

Codeforces is an unofficial Android version of Codeforces web. This app is made to integrate all the available Codeforces API into this app. This way the users can have a mobile version of their handle and can get key information on the go.


## How it Works?

On the [Codeforces](https://codeforces.com/) official web page, they provide various API which we access to get data in machine-readable JSON format. Then by using HttpURLConnection values of each column are parsed and set into the model to display the data. 

When the app is opened, the user is required to enter his preferred handle (Username). After submitting the handle, all the contest that the Handel is associated it is displayed. Upon opening, this screen user can perform the following operation -

* On clicking on the contest, it will redirect the user to the official contest page on the Codeforces.com
* User can filter the contest based on the positive and negative.
* User can view its profile.  


## Libraries Used
- [Architecture Components](https://developer.android.com/topic/libraries/architecture/)
- [DebugDB](https://github.com/amitshekhariitbhu/Android-Debug-Database)
- [GSON](https://github.com/google/gson)
- [MaterialDrawer](https://github.com/mikepenz/MaterialDrawer)
- [Logger](https://github.com/orhanobut/logger)
- [Picasso](https://square.github.io/picasso/)

## API's Used
- [Codeforces User rating](https://codeforces.com/api/user.rating?handle=sandeshghanta)
- [Codeforcees User Info](https://codeforces.com/api/user.info?handles=sandeshghanta)



## Screenshots
<table>
     <tr>
          <td><img height="500" src="https://raw.githubusercontent.com/jaindiv26/Codeforces/master/screenshots/Screenshot_2019-11-18-17-47-19-033_com.example.android.codeforces.png" /><br /><b>Home Screen</b></td>
          <td><img height="500" src="https://raw.githubusercontent.com/jaindiv26/Codeforces/master/screenshots/Screenshot_2019-11-18-17-47-34-861_com.example.android.codeforces.png" /><br /><b>Contest History Screen</b></td>
          <td><img height="500" src="https://raw.githubusercontent.com/jaindiv26/Codeforces/master/screenshots/Screenshot_2019-11-18-17-47-42-152_com.example.android.codeforces.png" /><br /><b>User Info</b></td>
     </tr>
</table>

## Workflow of app
```
.......
codeforces
 ┣ Activities
 ┃ ┣ HomeFeedActivity.java
 ┃ ┣ MainActivity.java
 ┃ ┣ ProfileActivity.java
 ┃ ┗ WebViewActivity.java
 ┣ Adapter
 ┃ ┗ ContestsAppearedAdapter.java
 ┣ BottomSheet
 ┃ ┗ SortBottomSheetView.java
 ┣ Listeners
 ┃ ┣ ContestItemClickListener.java
 ┃ ┗ SortClickListener.java
 ┣ Model
 ┃ ┗ Contest.java
 ┣ Utils
 ┃ ┣ RatingAsync.java
 ┃ ┣ RatingLoader.java
 ┃ ┗ StringUtils.java
 ┗ Constants.java
 ```
 
 ## Getting Started

These instructions will get you a copy of the project up and be running on your local machine for development and testing purposes.


### Prerequisites

[Android Studio](https://developer.android.com/studio), with a recent version of the Android SDK.

### Setting up your development environment

- Download and install Git.

- Fork the [Codeforces project](https://github.com/Chromicle/Codeforces)

- Clone your fork of the project locally. At the command line:
    ```
    $ git clone https://github.com/YOUR-GITHUB-USERNAME/Codeforces.git
    ```

If you prefer not to use the command line, you can use Android Studio to create a new project from version control using 
```
https://github.com/YOUR-GITHUB-USERNAME/Codeforces.git
```

Open the project in the folder of your clone from Android Studio and build the project. If there are any missing dependencies, install them first by clicking on the links provided by the Android studio. Once the project is built successfully, run the project by clicking on the green arrow at the top of the screen.



## PR Instruction

This project uses [Travis CI](https://travis-ci.org/Chromicle/codeforces) for checking pull requests. So before committing your changes, open Terminal via android studio and run the following commands:

For Windows:  
- `gradlew clean` then  
- `gradlew assembleDebug assembleRelease` then  
- `gradlew check` then
- `gradlew build` finally
- `gradlew spotlessCheck`




NOTE: Currently sever is not working but update the features in the app
Currently I am updating the resources for CSE and ECE departments only and that too for semester 3 only. Once I get all the resources, I will update in all departments.
You can freely contribute to the project on the note that 'contributing guidelines' of the project are followed.
New ideas and suggestions are welcomed.
Happy Coding :)