#udemy #firebase #android #kotlin 

>[!tip] Firebase
>- mobile and web application development platform
>- establish 2011 by *Firebase Company*
>- 2014 bought by Google
>- currently used with 18 services over 1.5 milion  apps
>- ==advantages== 
>> - can work on Android, iOS, Web App
>> - Real Time Database Service
>> - automates  authentication transactions
>> - serves developers in Push Notification , File Storage, ...
>- ==disadvantages==:
>>- limited data querying/filtering capabilities
>>- Android centered
>>- less support for iOS


# LOGIC:
- tranditional way:
	- client app --http api-->your server,
		- your server -- sdk --> database,
		- your server -- sdk --> cloud,
		- your server -- sdk --> ... .

- firebase way:
	- client app -- skd --> ... (database, cloud, ....)


>[!definition] Firebase Realtiem Database
>The Firebase Realtime Database lets you **build**:
>- rich, 
>- collaborative 
>applications by allowing secure access to the database directly from client-side code. 
>
>Data is persisted locally, and even while offline, realtime events continue to fire, giving the end user a responsive experience.
>
>s **a cloud-hosted NoSQL database** that lets you store and sync data between your users in realtime. NEW: Cloud Firestore enables you to store, sync and query app data at global scale.


# Products of Firebase
## Authentication

## Realtime Database
It is a cloud hosted database that is stored as JSON and synchronized in real time to every connected client.
All of your clients share one real time database instance and automatically receive updates with the newest data


## Cloud Firestore
it is a flexible, scalable database for mobile  web and server development .
It keeps your data in sync across client apps through real time listeners and offers offline support 


## Cloud Storage
It is built for app developers who need to store and serve user generated content (photos, videos)

## Machine Learning
It is a mobile SDK that brings Google's machine learning expertise to Android  and Apple Maps in a powerful, yet easy to use package.

Firebase ML provides convenient APIs that helo you use your custom TensorFlow Lite models in   your mobile app. 

## Hosting
It provides fast and secure hosting for your web app.

## Cloud Functions
It is a serverless framework that lets you automatically run back in code in response to events triggered by Firebase and HDB requests.

## Release and Monitor
We can improve app quality in less time with less effort, we can simplify testing, triaging and troublesshooting







