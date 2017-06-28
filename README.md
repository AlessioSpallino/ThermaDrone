# ThermaDrone
## What is this?
  - ThermaDrone is an **Android** application that enables you to automate your DJI Product. You can control flight, setting waypoints on the map and setting configuration to let your drone fly following pre-imposted path, speed and altitude.
  - The application is part of a project that was implemented during the "ICT Innovation" course (2016/2017) at the University of Trento.
  - This simple **Android** application can be used with a user with ID from 1 to 7. The goal is to help people to control their everyday physical activity and to help on choosing better food. The user has the possibility to update the personal measure and to set some goals. Inside the tab n°4 ("Action!") of the application the user has the possibility to set a countdown that will suggest the time of daily workout
 
## Architecture of the application

There are 5 layers of the architecture + Android application (Developed with Android Studio):


**Local Database Service:** (https://github.com/LifeStyleBuddy/local-db-service/wiki) This is a SOAP service. It communicates with the local database directly. The local Db is a simple SQLITE database. The next image shows the ER Diagram of the database:

![](https://github.com/LifeStyleBuddy/LifeStyleBuddy/blob/master/ERSchema.png)

**Adapter Service:** (https://github.com/LifeStyleBuddy/LSB-adapter/wiki) RESTful web service. This service interacts with the external APIs, such as EDAMAM API and PIXABAY API. It retrieves motivational pictures, lunch and dinner recipes. And sends them to the next layer of web service.

**Storage Service:** (https://github.com/LifeStyleBuddy/LSB-storage/wiki) RESTful web service. This service gets information from the Local DB and Adapter layers and sends it to the other layers. It can be considered as a central middleman service of the application.

**Business Logic Service:** (https://github.com/LifeStyleBuddy/LSB-businesslogic/wiki) RESTful web service. This layer receives requests from the UI layer and it gets data from the storage layer and processes it to send results back. Here is where the data are combined to let the client understand them better.

**Process Centric Service:** (https://github.com/LifeStyleBuddy/LSB-processcentric/wiki) RESTful web service. This service serves all the POST requests coming directly from a user (from application interface). This layer is doing nothing but redirecting a POST request to a proper underlying service or a set of services. This is an orchestration layer of the application.

**Image below shows the architecture of LifeStyleBuddy:**
![](https://github.com/LifeStyleBuddy/LifeStyleBuddy/blob/master/ArchSDE.png)


## The Android Application
At this youtube link: https://youtu.be/C6Z7YHyCFks is possible to see a very fast and clear tutorial on how this application works.
This Android application can be used with ID's from **1 to 7**. 
The following images will explain the functionality in a schematic way:

![](https://github.com/LifeStyleBuddy/LifeStyleBuddy/blob/master/AppSDE.png)

Inside the tab "profile" and "goals" it's possible to change measure/goals. It is very simple, just choose from the spinner which type of data you want to change, add the value
on the right and then click the button "SUBMIT". From the next login our data will be updated!
The tab number 4, "Action!", is where the workout starts. The app will suggest a time of workout and we can accept it or change it; in every case, once the button
start is clicked, a new motivational image will be opened on the bottom of the page.

##Technologies used in the project

- The application was developed in Java with the help of Android studio

- IntelliJ IDEA 15 was used as an IDE for the project.

- Database SQLite was used to store data at the local database level.

- GitHub was used a a code hosting, for this project the separate organization was created and can be reached by this link https://github.com/LifeStyleBuddy

- Heroku: all five layers (services) of the application are deployed on Heroku which is a PAAS product. Free account has been used.

- Wiki page was used to describe the APIs documentation.

- JSON format was used for RESTful services due to its readability and lightness.

- Apache Ant was used to build the Java application.

- Apache Ivy - dependency manager

## Possible improvements
- In this type of architecture only two external API are used. For sure adding more of them would be a good improvement, mostly connect a fitness band API will increase a lot the value of the product.
- Inside the third tab the user have the possibility to search for recipes. A possible improvement could be to give more informations about the food. This part was not implemented well because there were problems inside the business logic layer, sometimes the response was "500 internal server error" only because the list of ingredients was very long. based on this i decided to not take the ingredients value.



### HOW TO USE
At this youtube link: https://youtu.be/C6Z7YHyCFks is possible to see a very fast and clear tutorial on how this application work.
Is it possible also to try the application in every Android phone. You just have to download the APK file from here:
- https://github.com/LifeStyleBuddy/LifeStyleBuddy/blob/master/sdeFinalProject.apk
then send it to your phone (email, direct connection,telegram ...) and double click on it for the installation. 
