# unity-sdk

## Table of Content

### Integration

- [Quick start guide](#qs-add-trackier-sdk)
  - [Add Unity SDK to your app ](#qs-add-sdk)
- [Integrate and Initialize the Trackier SDK](#qs-implement-trackier-sdk)
  - [Retrieve your SDK key](#qs-retrieve-dev-key)
  - [Initialize the SDK](#qs-initialize-trackier-sdk)
- [Events Tracking](#qs-track-event)
  - [Retrieve Event Id from dashboard](#qs-retrieve-event-id)
  - [Built-in Events](#qs-built-in)
  - [Customs Events](#qs-customs-events)
  - [Revenue Event Tracking](#qs-track-event-with-currencey)
  - [Pass the custom params in events](#qs-add-custom-parms-event)
- [Deeplinking](#qs-deeplink) 

## <a id="qs-add-trackier-sdk"></a>Quick start guide

We have created a example app for the Unity SDK integration. 

Please check the [Example](https://github.com/trackier/flutter-sdk/tree/master/example) directory for know to how the `Trackier SDK` can be integrated.

### <a id="qs-add-sdk"></a>Add Unity SDK to your app

Unity SDK is very easy to integrate in your app. Just need to follow some steps

To integrate the Trackier SDK into your Unity project, follow these steps.

Get the SDK
As of version 1.0.1 you can download the latest version from our [releases page](https://github.com/trackier/unity-sdk/releases).

Add the SDK to your project
Open your project in the Unity Editor, go to Assets → Import Package → Custom Package and select the downloaded Unity package file.
 
<img width="1000" alt="Screenshot 2022-06-10 at 3 46 48 PM" src="https://user-images.githubusercontent.com/34488320/108677807-34c22f80-7510-11eb-804b-c4795633fd23.jpg">

 
### <a id="qs-implement-trackier-sdk"></a>Integrate and Initialize the Trackier SDK

### <a id="qs-retrieve-dev-key"></a>Retrieve your SDK key

For initialising the Trackier SDK. First, We need to generate the SDK key from the Trackier MMP panel.

Following below are the steps to retrieve the SDK key:-

- Login your Trackier Panel
- Select your application and click on Action button and login as
- In the Dashboard, Click on the` SDK Integration` option on the left side of panel. 
- under on the SDK Integration, You will be get the SDK Key.

After follow all steps, Your SDK key look like the below screenshot

Screenshot[1]

<img width="1000" alt="Screenshot 2022-06-10 at 3 46 48 PM" src="https://user-images.githubusercontent.com/16884982/173044860-a540706c-ad10-4174-aaf0-7cf9290fc949.png">

### <a id="qs-initialize-trackier-sdk"></a>Integrate the Trackier SDK in the Unity Application.

 
Integrate the SDK into your app

Initialize Trackier SDK :-
After importing package successfully, you would be seeing a Trackier named folder in which you will find Trackier.cs file.
 
In the following line add your app_token.

```c#

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using com.trackier.sdk;

namespace com.sampleapp
{
    public class Script : MonoBehaviour
    {
        // Start is called before the first frame update
        void Start()
        {
            /*While Initializing the SDK, You need to pass the two arguments in the TrackierSDKConfig.
            you need to pass the Trackier SDK api key in the argument */

            /* Initialize SDK */
            TrackierUnity.start("xxxx-xx-4505-bc8b-xx");
        }

        // Update is called once per frame
        void Update()
        {

        }
    }
}

```

Screenshot[2]

<img width="1000" alt="Screenshot 2022-07-28 at 9 33 39 AM" src="https://user-images.githubusercontent.com/16884982/181418407-06d38609-6794-4f73-a131-ae5e82df6bc5.png">

 
## <a id="qs-track-event"></a>Events Tracking

<a id="qs-retrieve-event-id"></a>Trackier events trackings enable to provides the insights into how to user interacts with your app. 
Trackier SDK easily get that insights data from the app. Just follow with the simple events integration process

Trackier provides the `Built-in events` and `Customs events` on the Trackier panel.

####  <a id="qs-built-in"></a> **Built-in Events** - 

Predefined events are the list of constants events which already been created on the dashboard. 

You can use directly to track those events. Just need to implements events in the app projects.

Screenshot[3]

<img width="1000" alt="Screenshot 2022-06-10 at 1 23 01 PM" src="https://user-images.githubusercontent.com/16884982/173018185-3356c117-8b9f-46d1-bfd5-c41653f9ac9e.png">

### Example code for calling Built-in events
```c#
  /*
 * Event Tracking
  <------------->
 * The below code is the example to pass a event to the Trackier SDK.
 * This event requires only 1 Parameter which is the Event ID.
 * Below are the example of built-in events function calling
 * The arguments - "TrackierEvent.LOGIN" passed in the Trackier event class is Events id
 *
 */

 public class Script : MonoBehaviour
    {
        // Start is called before the first frame update
        void Start()
        {
            /*While Initializing the SDK, You need to pass the two arguments in the TrackierSDKConfig.
            you need to pass the Trackier SDK api key in the argument */

            /* Initialize SDK */
            TrackierUnity.start("xxxx-xx-4505-bc8b-xx");

            /* Event Track */
             /*
            * Event Tracking
            <------------->
            * The below code is the example to pass a event to the Trackier SDK.
            * This event requires only 1 Parameter which is the Event ID.
            * Below are the example of built-in events function calling
            * The arguments - "sEMWSCTXeu" passed in the Trackier event class is Events id
            */
            TrackierEvent trackierEvent = new TrackierEvent("sEMWSCTXeu"); //pass your eventid here
            trackierEvent.param1 = "param";
            TrackierUnity.trackierEvent(trackierEvent);
        }

        // Update is called once per frame
        void Update()
        {

        }
    }

```

Note:- Argument in Trackier event class is event Id.

You can integrate inbuilt params with the event. In-built param list are mentioned below:-

orderId, revenue, currency, param1, param2, param3 ,param4, param5, param6, param7, param8, param9, param10.

Below are the screenshot of following example

Screenshot[4]




#### <a id="qs-customs-events"></a> **Customs Events** - 

Customs events are created by user as per their required business logic. 

You can create the events in the Trackier dashboard and integrate those events in the app project.

Screenshot[5]

<img width="1000" alt="Screenshot 2022-06-29 at 4 09 37 PM" src="https://user-images.githubusercontent.com/16884982/176417552-a8c80137-aa1d-480a-81a3-ea1e03172868.png">

#### Example code for calling Customs Events.

```c#

 public class Script : MonoBehaviour
    {
        // Start is called before the first frame update
        void Start()
        {
            /*While Initializing the SDK, You need to pass the two arguments in the TrackierSDKConfig.
            you need to pass the Trackier SDK api key in the argument */

            /* Initialize SDK */
            TrackierUnity.start("xxxx-xx-4505-bc8b-xx");

            /* Event Track */
             /*
            * Event Tracking
            <------------->
            * The below code is the example to pass a event to the Trackier SDK.
            * This event requires only 1 Parameter which is the Event ID.
            * Below are the example of built-in events function calling
            * The arguments - "sEMWSCTXeu" passed in the Trackier event class is Events id
            */
            TrackierEvent trackierEvent = new TrackierEvent("sEMWSCTXeu"); //pass your eventid here
            trackierEvent.param1 = "param";
            TrackierUnity.trackierEvent(trackierEvent);
        }

        // Update is called once per frame
        void Update()
        {

        }
    }

```
Below are the screenshot of above code snippet

Screenshot[6]

<img width="1000" alt="Screenshot 2022-07-28 at 9 54 36 AM" src="https://user-images.githubusercontent.com/16884982/181420054-2bc86669-ea5a-48ca-9727-b84cc956914d.png">


### <a id="qs-track-event-with-currencey"></a>Revenue Event Tracking

Trackier allow user to pass the revenue data which is generated from the app through Revenue events. It is mainly used to keeping record of generating revenue from the app and also you can pass currency as well.

```c#
    
    public class Script : MonoBehaviour
    {
        // Start is called before the first frame update
        void Start()
        {
            /*While Initializing the SDK, You need to pass the two arguments in the TrackierSDKConfig.
            you need to pass the Trackier SDK api key in the argument */

            /* Initialize SDK */
            TrackierUnity.start("xxxx-xx-4505-bc8b-xx");

            /* Event Track */
             /*
            * Event Tracking
            <------------->
            * The below code is the example to pass a event to the Trackier SDK.
            * This event requires only 1 Parameter which is the Event ID.
            * Below are the example of built-in events function calling
            * The arguments - "sEMWSCTXeu" passed in the Trackier event class is Events id
            */
            TrackierEvent trackierEvent = new TrackierEvent("sEMWSCTXeu"); //pass your eventid here
            trackierEvent.param1 = "param";
            trackierEvent.revenue = 8.0; //pass your revenue here
            trackierEvent.currency = "Inr"; //pass your currency here
            TrackierUnity.trackierEvent(trackierEvent);
        }

        // Update is called once per frame
        void Update()
        {

        }
    }

```
       
### <a id="qs-add-custom-parms-event"></a>Pass the custom params in events

```c#

IDictionary<int, object> eventCustomParams = new Dictionary<int, object>();
numberNames.Add(customParam1,XXXXX); 
numberNames.Add(customParam2,XXXXX);
trackierEvent.ev = eventCustomParams;
TrackierUnity.TrackEvent(trackierEvent);
	
```
 ### <a id="qs-deeplink"></a>Deeplinking 

Deep linking is a techniques in which the user directly redirect to the specific pages of the application by click on the deeplink url.

There are two types deeplinking

* ***Normal deeplinking*** - Direct deep linking occurs when a user already has your app installed on their device. When this is the case, the deep link will redirect the user to the screen specified in the link.

* ***Deferred deeplinking*** - Deferred deep linking occurs when a user does not have your app installed on their device. When this is the case, the deep link will first send the user to the device app store to install the app. Once the user has installed and opened the app, the SDK will redirect them to the screen specified in the link.

Please check below the Deeplinking scenario 

<img width="705" alt="Screenshot 2022-06-22 at 10 48 20 PM" src="https://user-images.githubusercontent.com/16884982/175099075-349910ce-ce7b-4a71-868c-11c34c4331cd.png">


### Normal Deep linking

If a user already has your app on their device, it will open when they interact with a tracker containing a deep link. You can then parse the deep link information for further use. To do this, you need to choose a desired unique scheme name.

You can set up a specific activity to launch when a user interacts with a deep link. To do this:

* Assign the unique scheme name to the activity in your AndroidManifest.xml file.
* Add the intent-filter section to the activity definition.
* Assign an android:scheme property value with your preferred scheme name.

For example, you could set up an activity called FirstActivity to open like this:
#### AndroidManifest.xml 

```

        <activity
            android:name=".Activity.FirstProduct"
            android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.VIEW" />
            <category android:name="android.intent.category.DEFAULT" />
            <category android:name="android.intent.category.BROWSABLE" />
            <data
                android:host="trackier.u9ilnk.me"
                android:pathPrefix="/product"
                android:scheme="https" />
        </intent-filter>
        </activity>

```

```
https://trackier.u9ilnk.me/product?dlv=FirstProduct&quantity=10&pid=sms
```


### Deferred deep linking

Deferred deep linking happened, when a user does not have your app installed on their device. When the user clicks a trackier URL, the URL will redirect them to the Play Store to download and install your app. When the user opens the app for the first time, the SDK will read the deeplink content.

For get deeplink content information, set a callback method on the TrackierConfig object. This will receive the parameters where the content of the URL is delivered. Set this method on the config object by calling the method setDeferredDeeplinkDelegate:

Below are the example of the code :-

```c#
using UnityEngine;
using System.Collections;
using com.trackier.sdk;
using System;

public class NewMonoBehaviour : MonoBehaviour
{
	// Use this for initialization
	void Start()
	{
        TrackierConfig trackierConfig = new TrackierConfig("abcf2270-xxxxxxxxxx-34903c6e1d53", "development");
        trackierConfig.setDeferredDeeplinkDelegate(DeferredDeeplinkCallback); // Pass for setting the deferred deeplinking 
        TrackierUnity.initialize(trackierConfig);
        Debug.Log("AppKey Initialized");

    }

	// Update is called once per frame
	void Update()
	{
			
	}

    private void DeferredDeeplinkCallback(string deeplinkURL)
    {
        Debug.Log("Deferred deeplink reported!");

        if (deeplinkURL != null)
        {
            Debug.Log("Deeplink URL: " + deeplinkURL); // Getting the deeplink url.
        }
        else
        {
            Debug.Log("Deeplink URL is null!");
        }
    }
}

``` 
