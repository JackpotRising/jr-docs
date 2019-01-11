# Native iOS Integration

* iOS 9.1+
* [Cocoapods](https://cocoapods.org)
* [Jackpot Rising Developer Account](https://developer.jackpotrising.com/#/)
* Location Services

An example project can be [found on Github](https://github.com/JackpotRising/swift-example).

---
 
Installation
 
Start typing markdown here...
 

Stehttps://dash.readme.io/project/jackpot-rising/v3.0/docs/ios-installationp 1
     
Initialize the Podfile inside of the project root directory
Initialize the Podfile inside of the project root directory 
 

Start typing markdown here...
 
 
Shell
rename · delete 

pod init

Start typing markdown here...
 
 
Custom HTML / CSS JavaScript will stripped, CSS will be scoped

<div></div>
<hr>
<style></style>

Start typing markdown here...
 
 
   

Step 2
     
Edit the newly created Podfile and add this into it
Edit the newly created Podfile and add this into it 
 

Start typing markdown here...
 
 
Shell
rename · delete 

platform :ios, '9.0'
  target 'My-Game' do // My-Game should be the name of your project in Xcode
  pod 'JackpotRising'
end

Start typing markdown here...
 
 
Custom HTML / CSS JavaScript will stripped, CSS will be scoped

<div></div>
<hr>
<style></style>

Start typing markdown here...
 
 
   

Step 3
     
Save the Podfile and then install the pod
Save the Podfile and then install the pod 
 

Start typing markdown here...
 
 
Shell
rename · delete 

pod install

Start typing markdown here...
 
 
Custom HTML / CSS JavaScript will stripped, CSS will be scoped

<div></div>
<hr>
<style></style>

Start typing markdown here...
 
 
   

Step 4
     
Open Xcode 
 
Custom HTML / CSS JavaScript will stripped, CSS will be scoped

<div></div>
<hr>
<style></style>

Start typing markdown here...
 
 
   

Optional Step 5
     
For updating the SDK in the future you can do this
For updating the SDK in the future you can do this 
 

Start typing markdown here...
 
 
Shell
rename · delete 

pod update JackpotRising

---

   

Step 1
     
Initialize the SDK as soon as your application opens
Initialize the SDK as soon as your application opens 
 

The SDK is based on a singleton pattern, meaning there is only 1 instance of the SDK that should and will exist during the application lifecycle. But to use the SDK you must first initialize it with your project's credentials provided on the Developer Dashboard and set up the target mode.
The SDK is based on a singleton pattern, meaning there is only 1 instance of the SDK that should and will exist during the application lifecycle. But to use the SDK you must first initialize it with your project's credentials provided on the Developer Dashboard and set up the target mode. 
 
Swift
rename · delete 

override func viewDidLoad() {
    super.viewDidLoad()
        
    // Do any additional setup after loading the view, typically from a nib.
    
    JackpotRising.sharedInstance.initWithClientCredentials("YOUR-CLIENT-ID", clientSecret: "YOUR-CLIENT-SECRET")
    JackpotRising.sharedInstance.delegate = self
    JackpotRising.sharedInstance.pointingURL = .production
    JackpotRising.sharedInstance.testMode = true // This is for enabling/disabling GPS check. Set this to true when ready for release
    JackpotRising.sharedInstance.apiMode = .test // This is for setting test mode for contests. Set this to production when ready for release
    
}

 - pointingURL should always be _production_ for 3rd party developers such as yourself. We have a staging mode that we use internally here at Jackpot Rising HQ which works off an entirely separate database, login, and credential system.
 - testMode determines whether you're in test mode for your tournament or production, which is an option to test in the background outside the scope of normal players. Your tournaments will not be live for actual money while in test mode though - set that to production when you're ready for a production release!
 - testMode toggles the Geolocation check that is required for Jackpot Rising to work in production. Enable test mode if you're working outside of permitted locations and disable it when you are making a public production build ready for players to download
 - pointingURL should always be _production_ for 3rd party developers such as yourself. We have a staging mode that we use internally here at Jackpot Rising HQ which works off an entirely separate database, login, and credential system.
 - testMode determines whether you're in test mode for your tournament or production, which is an option to test in the background outside the scope of normal players. Your tournaments will not be live for actual money while in test mode though - set that to production when you're ready for a production release!
 - testMode toggles the Geolocation check that is required for Jackpot Rising to work in production. Enable test mode if you're working outside of permitted locations and disable it when you are making a public production build ready for players to download 
 
   

Step 2
     
Set up delegate to receive callbacks from the SDK
Set up delegate to receive callbacks from the SDK 
 

You'll want to make sure to set up a delegate to receive the callbacks from the SDK to be aware of when it opens or closes, the player starts a tournament attempt, and (optionally) when to play an Ad from your ad network of choice.
You'll want to make sure to set up a delegate to receive the callbacks from the SDK to be aware of when it opens or closes, the player starts a tournament attempt, and (optionally) when to play an Ad from your ad network of choice. 
 
Swift
rename · delete 

import UIKit
import AVKit
import AVFoundation
import JackpotRising
​
class ViewController: UIViewController, UITextFieldDelegate, JackpotRisingDelegate {
​
    func contestStarted(_ data: [String : Any]) {
        print(data)
        // This is where you want to initiate your gameplay from!
    }
    
    func fetchLocationStatus(_ status: Bool) {
        print(status)
    }
    
    func initialPopupCancelled(){
        print("SDK cancelled")
    }
    
    func sdkClosed() {
        print("SDK closed")
    }
    
    func sdkFailedToInitialize(_ message: String) {
        print(message)
    }
    
    func playAd() {
        print("play contest ad")
        // Play your own ad network and then call contestAdWatched with the success or failure flag
        // The tournament won't actually start until you make the call back to the SDK after ad has been presented to the player, and the player taps the SDK overlay's button to start the game - where contestStarted() will be called
    }
​
    override func viewDidLoad() {
        super.viewDidLoad()
        
        // Do any additional setup after loading the view, typically from a nib.
    
        JackpotRising.sharedInstance.initWithClientCredentials("YOUR-CLIENT-ID", clientSecret: "YOUR-CLIENT-SECRET")
        JackpotRising.sharedInstance.delegate = self
        JackpotRising.sharedInstance.pointingURL = .production
        JackpotRising.sharedInstance.testMode = true // This is for enabling/disabling GPS check. Set this to true when ready for release
        JackpotRising.sharedInstance.apiMode = .test // This is for setting test mode for contests. Set this to production when ready for release
        
    }
​
}

Start typing markdown here...
 
 
   

Step 3
     
Link the delegate to the SDK so it can call into your code
Link the delegate to the SDK so it can call into your code 
 

Don't forget to also attach this delegate to the Jackpot Rising SDK so it knows where to call back to! Assuming we're assigning this in the same ViewController class that inherits the delegate:
Don't forget to also attach this delegate to the Jackpot Rising SDK so it knows where to call back to! Assuming we're assigning this in the same ViewController class that inherits the delegate: 
 
Text
rename · delete 

JackpotRising.sharedInstance.delegate = self

---


Start typing markdown here...
 
 
   

Create a Play for Real Money button and assign it to a function to show the SDK
     
You can use one of our buttons if you would like. Refer to the FAQ
You can use one of our buttons if you would like. Refer to the FAQ 
 

Start typing markdown here...
 
 
Swift
rename · delete 

@IBAction func startSDKAction(_ sender: AnyObject) {
    JackpotRising.sharedInstance.showSDK()
}

To respond to a player's entry attempt into an tournament so you can start your game, see the [Initialization section](http://docs.jackpotrising.com/v2.0/docs/initialization) which includes a basic example of the callback delegate for contestStarted().
To respond to a player's entry attempt into an tournament so you can start your game, see the [Initialization section](http://docs.jackpotrising.com/v2.0/docs/initialization) which includes a basic example of the callback delegate for contestStarted(). 
 

---


Message Title
     
Call the submitScore method when the game/level ends
Call the submitScore method when the game/level ends 
 

Start typing markdown here...
 
 
Swift
rename · delete 

@IBAction func submitScore(_ sender: AnyObject) {
    if JackpotRising.sharedInstance.isContestRunning() {
        JackpotRising.sharedInstance.submitScore(Int(uxTxtScore.text ?? "") ?? 0)
    }
}

---


Compiling Settings
 
* Open the info.plist file
* Add the following key:value
* Open the info.plist file
* Add the following key:value 
 
Text
rename · delete 

Privacy - Location When In Use Usage Description : Location required to compete in Jackpot Rising Tournaments

