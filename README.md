Adjust Pugin for Email attribution
=======================================

Step 1
------
To add the `Email Sha1 plugin`, first move the file `AdjustPlugin-Integration/plugin_email.java` to the folder `Adjust/src/com/adjust/sdk/plugin/`.

The `Email Sha1 plugin` allows to collect the SHA-1 of the device's primary email. To access this information, you need to add the following permission to the AndroidManifest.xml of your app:

```
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
```
Step 2
------
In Adjust/src/com/adjust/sdk/Constants.java add the plugin by it’s full path.

````
List<String> PLUGINS = Arrays.asList("com.adjust.sdk.plugin.emailsha1");
````
