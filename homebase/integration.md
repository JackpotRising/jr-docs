# Homebase Integration

## Register

## [https://homebase.jackpotrising.com](https://homebase.jackpotrising.com ':target=_blank')

!> Tap the **Register** button and complete all required fields.

---

## Add a Game

Login to [Homebase](https://homebase.jackpotrising.com ':target=_blank')

![Screenshot](media/game/001.png)

Tap the *Add Game* button at the top-left of the page, then provide all required information.

![Screenshot](media/game/002.png)

#### 1. Details

Jackpot Rising can use this within the SDK to brand your game on the Jackpot Rising app store.

![Screenshot](media/game/003.png)

!> You can select multiple *Genres* or *Platforms* by holding down **Control/Command**

#### 2. Platforms

Configure options for each enabled platform. You will be prompted for any additional details per each.

![Screenshot](media/game/004.png)

> Ex: Selecting iOS will prompt you for your game's "iOS store link" and its "iOS bundle"

#### 3. Media

Provide your game's media, including: a video trailer, icon, and backsplash that will be used to brand your game.

![Screenshot](media/game/005.png)

**How To Embed a YouTube Trailer**
* Navigate to your YouTube video in a browser
* Tap the SHARE option below the video
* Copy the Video ID from the sharable URL (highlighted in red below)
* Create your embed URL using the Video ID like so: `https://www.youtube.com/embed/{videoid}`
* Add the embed URL into the YouTube field on Homebase

![Screenshot](media/game/006.png)

**Image Size Requirements**
* Icon: 512x512
* Backsplash (Horizontal): 1200x300
* Backsplash (Vertical): 300x1200

#### 4. Notificiations

In order to get the most out of running Jackpot Rising tournaments, it is crucial to keep your players informed. You may optionally integrate a [OneSignal](https://onesignal.com/ ':target=_blank') account to enable Push Notifications within the platform.

![Screenshot](media/game/007.png)

?> Get your OneSignal App ID from the [OneSignal Dashboard](https://documentation.onesignal.com/docs/accounts-and-keys#section-keys-ids ':target=_blank')

**Notification Examples**

* New tournament added
* Tournament ending soon
* Player was knocked out of the money
* Tournament completed

> By default, only the "new tournaments" notification is enabled for players. We limit the number of notifications that go out, so you do not have to worry about your players being spammed!

#### 5. Currency (optional)

If you plan to use a custom game currency in place of real money, you may provide your assets here.

![Screenshot](media/game/008.png)

---

## Generate SDK Credentials

Each game has a unique set of SDK credentials that help authenticate and connect your game to the Jackpot Rising platform. Follow the instructions below to retrieve your SDK credentials.

Start by tapping the **Games** navigation section.

![Screenshot](media/game/009.png)

Select your game by tapping the **Details** button

![Screenshot](media/game/010.png)

Generate your Developement and Production SDK keys from the section picture below.

![Screenshot](media/game/011.png)

> Keep your credentials handy! You'll need them when you start integrating your game in Unity or other platforms

---

## Create a Tournament

Create a tournament for your game. This includes large variety of configurable options.

#### 1. Core Settings

![Screenshot](media/tournament/001.png)

**Live Tournament vs Test Mode**

!> Note: Games must be built with a Test Mode flag enabled to make Test tournaments visible.

There are several key differences between Live Tournaments and Test Mode Tournaments:

* Test Mode acts as a sandbox mode for testing tournaments internally or when submitting for approval.
* Test tournaments do not deduct funds from an account or credit card.
* Test tournaments do not use GPS Location, so you can play from any location.
* Players will never see Test Mode tournaments, since they're visibility is limited to Test Mode games

**Tournament Name**

This is a unique identifier for the tournament, visible to players. We recommend avoiding "Tournament" in the name. DO NOT include "Tournament" for recurring tournaments. This will be appended for you automatically.

#### 2. Currency

Set the initial funding for your tournament.

![Screenshot](media/tournament/002.png)

**Currency Mode**

* Real Money - all money in/out will utilize real currency in USD
* Game Currency - this utilizes your game's custom currency (ex: gold coins)

> Game Currency is configured in your Game settings

**Initial Jackpot**

The starting jackpot amount.

#### 3. Tiers & Parameters

Settings for configuring attempts, jackpot splits, customizable game parameters, and rules.

![Screenshot](media/tournament/003.png)

**Free vs Paid Entry**

* Free Entry - does not require a player to pay to participate in a tournament
* Paid Entry - utilizes a progressive system where players pay to make an attempt, however a portion of each attempt increases the total jackpot amount

> The majority of the attempt fee goes to the progressive jackpot, with the rest being split between the developer (you) and Jackpot Rising.

?> See the **Ad Support** guide for more information on using this feature.

**Tiers**

Tiers allow you to split your single tournament's jackpot into mutiple "buckets", which can target players at different skill levels. Higher tiers have a higher attempt fee in but larger jackpot payout, and vice versa. A Beginner tier may also be enabled for new players.

**Parameters**

Paramters allow you to provide unique key/value data to your tournament. This data is provided to your game at the beginning of a tournament attempt. This allows you to tailor your gameplay experience for players per tournament.

**Rules**

Allows you to give more information to your users on what differentiates this tournament from standard play. The rules section is also useful to provide the user with any overviews, instructions, tips, or details on the game/tier/tournament.

#### 4. Payouts

Where you define the payout structure per each tier.

![Screenshot](media/tournament/004.png)

**Distribution**

The number of awardees per tier.

**Condition**

The win condition per tier.

**Percentage Table**

Shows the split for default Ditribution and Condition settings, or allows you to overide and define custom percentage payouts.

!> Please make sure that the actual amount being paid out to each tier is sufficient. If you have too many tiers or payout spots enabled for the current starting jackpot, then you could run into an issue where a payout spot receives less than the attempt fee for that tier! If you run into this issue, then please reduce the number of tiers/payouts or increase the starting jackpot amount.

#### 5. Duration

When setting the duration of your tournament you can create a "set" tournament or a "recurring" tournament.

![Screenshot](media/tournament/005.png)

**Set Mode**

The tournament has a clearly defined start and end date/time

**Recurring Mode**

Recreates the tournament repeated via a defined interval (ex: daily, etc)

> Note the tournament name will be auto-generated for Recurring tournaments

