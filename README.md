#Adjust Pugin for Email attribution

The following plugin modifies the Adjust.com tracking SDK for Android which can be found here - https://github.com/adjust/android_sdk

The purpose of this plugin is to enable the Adjust SDK to access the primary email address associated with Google Play on a device. Once the account information is accessed it is encrypted using SHA1 encryption, after which it is sent to Adjust’s servers. The Adjust server will then match up the SHA1 data from the SDK to information in the Adjust system. 

To enable this plugin, you will need to add the `emailsha1.java` file, enable the `GET_ACCOUNTS` permission and create proper references via `Constants.java` file. 

Once the code is updated, compile the APK file and resubmit to Google Play. 

For a more in depth set of instructions regarding implementation of the Adjust.com Android SDK, please refer to the following file - https://github.com/adjust/android_sdk/blob/master/README.md

***Please note that this plugin has only been tested with v.3.6.2 of Adjust’s Android SDK. ***

##Adjust Plugin for Desktop to Mobile Attribution with a hashed email address 

###Step 1

To add the Email SHA1 plugin, first move the file `AdjustPlugin-Integration/emailsha1.java` to the folder `Adjust/src/com/adjust/sdk/plugin/`.

The emailSHA1 plugin allows the app to collect the SHA-1 of the device's primary email. To access this information, you need to add the following permission to the AndroidManifest.xml:
```
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
```

###Step 2
Once the GET_ACCOUNTS permission is enabled, you will need to ensure the app invokes the correct plugin. 

In `Adjust/src/com/adjust/sdk/Constants.java` add the plugin with the full path.
```
List<String> PLUGINS = Arrays.asList("com.adjust.sdk.plugin.emailsha1");
```
###Step 3

Check visibility level of sha1 method for ../Adjust/src/com/adjust/sdk/Util.java unit. It should be set to public as an example below:
```
    public static String sha1(final String text) 
    {
        return hash(text, SHA1);
    }
```
###Step 4

Build and run your android app.

##Testing

Once the app is compiled and re-submitted to the Google Play Store, please provide the tracker link to your MobilePlay contact. 
 
Sample Tracker link:
```
https://app.adjust.io/SIX_DIGIT_TRACKER_CODE
```
 MobilePlay will setup a test campaign for your application and provide a link to test attribution. Please note that your device can only be attributed once per application, to test again the DEVICE ID must be erased from Adjust database. 
 
 Please use the following link to remove your device ID from the database.     
```
https://app.adjust.io/forget_device?app_token=YOUR_APP_TOKEN&gps_adid=YOUR_GOOGLE_ADVERTISER_ID
```
 
##Contact Us:
If you have any questions or issues implementing this plugin please email contactus@mobileplay.com
