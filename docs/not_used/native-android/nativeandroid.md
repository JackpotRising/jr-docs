# Native Android Integration

Android Currently Offline

Jackpot Rising 3.0 for Android is currently in development. The included Android version is 2.0 and will not work

---


Android Offline
     
Jackpot Rising 3.0 for Android is currently in development. The included Android version is 2.0 and will not work
Jackpot Rising 3.0 for Android is currently in development. The included Android version is 2.0 and will not work 
 

Start typing markdown here...
 
 

Installation
 
1.	Drop the .aar and .jar files included in the zip file into your project’s libs folder. *Note: We are looking into integrating with Gradle repositories as a dependency option*
2.	Import **com.jr.sdk.JR** in your source code
3.	Create a **JRListener** tohttps://dash.readme.io/project/jackpot-rising/v3.0/docs/android-installation receive player and contest activity
4.	Initialize SDK using credentials, production state, and listener object. *See Initialization section for details.*
1.	Drop the .aar and .jar files included in the zip file into your project’s libs folder. *Note: We are looking into integrating with Gradle repositories as a dependency option*
2.	Import **com.jr.sdk.JR** in your source code
3.	Create a **JRListener** to https://dash.readme.io/project/jackpot-rising/v3.0/docs/android-installation receive player and contest activity
4.	Initialize SDK using credentials, production state, and listener object. *See Initialization section for details.*
 

Initialization
 
Start typing markdown here...
 
 
Android
rename · delete 

https://dash.readme.io/project/jackpot-rising/v3.0/docs/android-installation
JR.init(clientId, clientSecret, context, listener, checkLocation, isProduction)https://dash.readme.io/project/jackpot-rising/v3.0/docs/android-installation

**final String clientId**
ClientID provided in the Developer Dashboard for your game project.

**final String clientSecret**
ClientSecret provided in the Developer Dashboard for your game project.

**final Context context**
Context of your application activity that the SDK will overlay on top of. Ideally this should be your main application activity.

**final JRListener listener**
Listener object that is inherited from ***JR.JRListener***. The listener receives contest-specific values and actions from the player in the SDK that your game can use and respond to.

**boolean checkLocation**
Flag for checking GPS location. This is ***REQUIRED*** for production releases, and should **only** be turned off in development testing when working in an unsupported jurisdiction. *For more information, **check our FAQ** on locations that support the platform.*

**boolean isProduction**
Flag for setting SDK state. When ready to bring a live build for real players in contests, make sure this is set to **true** and that you use the Production clientID and clientSecret.
**final String clientId**
ClientID provided in the Developer Dashboard for your game project.

**final String clientSecret**
ClientSecret provided in the Developer Dashboard for your game project.

**final Context context**
Context of your application activity that the SDK will overlay on top of. Ideally this should be your main application activity.

**final JRListener listener**
Listener object that is inherited from ***JR.JRListener***. The listener receives contest-specific values and actions from the player in the SDK that your game can use and respond to.

**boolean checkLocation**
Flag for checking GPS location. This is ***REQUIRED*** for production releases, and should **only** be turned off in development testing when working in an unsupported jurisdiction. *For more information, **check our FAQ** on locations that support the platform.*

**boolean isProduction**
Flag for setting SDK state. When ready to bring a live build for real players in contests, make sure this is set to **true** and that you use the Production clientID and clientSecret. 
 
---


Android Offline
     
Jackpot Rising 3.0 for Android is currently in development. The included Android version is 2.0 and will not work
Jackpot Rising 3.0 for Android is currently in development. The included Android version is 2.0 and will not work 
 

Start typing markdown here...
 
 

Runtime
 
Start typing markdown here...
 
 
Android
rename · delete 

JR.launch(Context context)

Produces an offer pop-up to play for real money, and is the gateway into the platform. From here players will be able to manage their account balance and enter in an active contest you have configured for your game

**context**
The Android Activity that the SDK will overlay. *Android games will typically only have one Activity using a GLSurface. for the entire application lifecycle. Your implementation may vary.* 
Produces an offer pop-up to play for real money, and is the gateway into the platform. From here players will be able to manage their account balance and enter in an active contest you have configured for your game

**context**
The Android Activity that the SDK will overlay. *Android games will typically only have one Activity using a GLSurface. for the entire application lifecycle. Your implementation may vary.*  
 
Android
rename · delete 

JR.submitScore(Context context, double score)

Submits the gameplay score earned by your player into the contest. It will be ignored if they are not engaged in a contest when called.

**context**
The Android Activity that the SDK will overlay. *Android games will typically only have one Activity using a GLSurface. for the entire application lifecycle. Your implementation may vary.*

**score**
The score value or time succeeded (in seconds) by the player during the contest gameplay attempt. 
Submits the gameplay score earned by your player into the contest. It will be ignored if they are not engaged in a contest when called.

**context**
The Android Activity that the SDK will overlay. *Android games will typically only have one Activity using a GLSurface. for the entire application lifecycle. Your implementation may vary.*

**score**
The score value or time succeeded (in seconds) by the player during the contest gameplay attempt.  
 
Android
rename · delete 

int JR.getContestStatus()

Returns integer of contest status. Contest states are as follows:

* 0 – No contest: No contest information could be found from the server.
* 1 – Active: Contest is available to play in right now.
* 2 – Not Started: Contest is scheduled to start soon, but has not started yet.
* 3 – Ended: Active contest has recently passed the end time, and payouts will soon be rewarded
* 4 – Error: This may be the result of a network connectivity problem, incorrect authentication keys, or incorrect test/production state. If you verify you have the correct test/production state and keys but still encounter this error state, please [contact Jackpot Rising for support](https://jackpotrising.zendesk.com/hc/en-us).
Returns integer of contest status. Contest states are as follows:

* 0 – No contest: No contest information could be found from the server.
* 1 – Active: Contest is available to play in right now.
* 2 – Not Started: Contest is scheduled to start soon, but has not started yet.
* 3 – Ended: Active contest has recently passed the end time, and payouts will soon be rewarded
* 4 – Error: This may be the result of a network connectivity problem, incorrect authentication keys, or incorrect test/production state. If you verify you have the correct test/production state and keys but still encounter this error state, please [contact Jackpot Rising for support](https://jackpotrising.zendesk.com/hc/en-us). 
