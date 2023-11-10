# TIDBYT-WS1Devices
View your Workspace ONE UEM total devices and their status on your Tidbyt.


If you own a TIDBYT you will be able to install this app.  Feel free to fork this off and make new apps targeting Workspace ONE UEM.
Hopefully you will find this app, its embeded comments, and instructions useful enough to create your own apps.  If you do, or you just have some feedback, please email me at ibanyan@gmail.com

I plan to submit this app to TIDBYT so that it is available in their app store.  The version here is exactly the same, just without the part that integrates ith the TIDBYT mobile app.
You may decide not to use the app from the official store because of security concerns.  Thats OK because luckily TIDBYT lets you push your own apps.

The way you can use this app is by writing a small and simple script that re-pushes it on a cadence (say once an hour).
[I'll include a few examples of scripts here in the future when time permits, or if anyone else would like to share some, I'll include them here]

You will need PIXLET. You can get it here: https://tidbyt.dev/docs/build/installing-pixlet
PIXLET will be used to compile (or as it is called render) the app, and send it to your TIDBYT.

Prep:
Get your TIDBYT's device ID and API key.
- Open the TIDBYT app on your phone, tap the cog icon, and tap General.
- Tap Get API key
- Tap Copy to Clipboard for each one at a time and paste them both in a text editor.

Get your Workspace ONE UEM API user credentials and the tenant code
- The tenant code is the AirWatchAPI Key in the REST API screen.
- The API admin user's credentials. You may need to create a new admin user with at least the API role unless you have one already created.
- Today this app only supports Basic authentication.
- Basic username and password already converted to Base64 (Postman can help with this).

Your tenant's API URL.
- This is your tenant URL but changing cn to as.
- For example the regular console URL could be https://cn135.awmdm.com and the API URL would be https://as135.awmdm.com

Your tenant's root OG ID number.
- To find this, look at the number at the end of the URL after navigating to OG Details page.

One-time Setup.
- Edit the file WSONEDevices.star and paste in the required info from your tenant.
- Save the file.

Send the app to your TIDBYT.
- Open Terminal and change to the folder where your saved the edited file WSONEDevices.star
- Type: pixlet render WSONEDevices.star
- A new file called WSONEDevices.wepb should appear in the folder.
- Type: pixlet push --installation-id WSONEDevices --api-token your_TIDBYT_API_token "your_TIDBYT_Device_ID" WSONEDevices.webp

Pushing the app to your TIDBYT one time will display the information frozen in time.  It will never update.
To get it to update, you'll need to write a short script to render the app and push it to your TIDBYT on a schedule, say once an hour.
Your script will need to execute these to lines repeatedly:
- pixlet render WSONEDevices.star
- pixlet push --installation-id WSONEDevices --api-token your_TIDBYT_API_token "your_TIDBYT_Device_ID" WSONEDevices.webp

Once this app makes it to the TIDBYT public app store, you'll be able to simply install it and it will update on its own.
