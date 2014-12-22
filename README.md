Adjust Pugin for Email attribution
=======================================
To add the `Email Sha1 plugin`, first move the file `plugin/plugin_email.java` to the folder `Adjust/src/com/adjust/sdk/plugin/`.

The `Email Sha1 plugin` allows to collect the SHA-1 of the device's primary email. To access this information, you need to add the following permission to the AndroidManifest.xml of your app:

```
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
```

Optionally, you can add a string to be concatenated with the email before is hashed with the SHA-1 algorithm. Add the string in a meta-data tag inside the application tag, as follows:
```
<meta-data android:name="AdjustVulcunSalt" android:value="vulcun salt example" />
```
