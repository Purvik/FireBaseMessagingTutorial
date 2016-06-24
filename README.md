# FireBaseMessagingTutorial
A Tutorial on how you can integrate FireBase in your Android Application and enable Notification from FCM Console. FireBase provides various functions like Notification, Database, Analytics, AdMob and much more. In contrast with the GCM (Google Cloud Messaging), FireBase messaging has some easy feature to send notification to the devices running with your application. 

Here in this project, 

** First, FireBase dependencies need to be integrate in project, require to add Root level build.gradle & then app level build.gradle file.

    In root level build.gradle file add in dependencies,
        classpath  'com.google.gms:google-services:3.0.0' //Add Services to your Project
      
      and
      
      in app level build.gradle file add in dependencies,
        compile 'com.google.firebase:firebase-messaging:9.0.0' //FireBase library for messaging
        
        and 
        
        at the end of the file add,
        apply plugin: 'com.google.gms.google-services'  
        
** Two Services:

    1. MyFirebaseInstanceIDService which extends FirebaseInstanceIdService
        Takes care of generating Token and register that token to the server
        
    2. MyFirebaseMessagingService which extends FirebaseMessagingService
        Takes care of handling receiving message from server, bifercating data from RemoteMessage and generating Notification along with that data.
    
** AndroidManifest Modification,
    Require to add Services in manifest file with specific action via intent-filter to handle it.
    
    <service
            android:name=".MyFirebaseMessagingService">
            <intent-filter>
                <action android:name="com.google.firebase.MESSAGING_EVENT"/>
            </intent-filter>
        </service>
 
        <service
            android:name=".MyFirebaseInstanceIDService">
            <intent-filter>
                <action android:name="com.google.firebase.INSTANCE_ID_EVENT"/>
            </intent-filter>
        </service>
        
        
To Application level - That's it...Run your Application!! 

Now you have to register your project with Package id to the firebase console: https://console.firebase.google.com/

Go to Notification from Dashbord's left panel and Find out Refreshed Token from Logs of your running project & copy it. 

Go for Single Device and paste your refreshed token. Provide message details -> confirm it and send message. Wait to get notification on your device.

That's it. :)
