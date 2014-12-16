AdjustPlugin-Integration
========================

Adjust Integration for SHA1 Plugin

The plugin mechanism allows to add optional functionality to the Adjust SDK without changing the current implementation. Just add one of the plugins from the plugin folder to Adjust/src/com/adjust/sdk/plugin and it's functionality will be automatically added.

+Email_SHA1 To add the Email_Sha1 plugin, first move the file plugin/plugin_email.java to the folder Adjust/src/com/adjust/sdk/plugin/.

The plugin allows to collect the sha-1 of the device's primary email. To access this information, you need to add the following permission to the AndroidManifest.xml of your app:

Optionally, you can add a string to be concatenated with the email before is hashed with the sha-1 algorithm. Add the string in a meta-data tag inside the application tag, as follows:
