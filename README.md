# watsonwork-sentiment analyzer
**Writes a message back if there is someone with very negative or very positive comments**

### Demonstrates the following specific Watson Work Services capabilities

1. How to listen to events in a Watson Work Space, specifically it knows how to process message annotation added events and thus requires that apps registered are enabled with those events.
2. How to authenticate using the appID + secret to obtain an access token
3. How to call graphQL api to obtain name and email of the user who wrote the message being analyzed
4. How to interpret the analysis based on sentiment using a score of 80% on either happiness or sadness
5. How to write a message back into the conversation announcing the sentiment of the person who wrote the message that was analyzed

### To utilize with BlueMix:

1. Clone project into a directory on your computer
2. Edit the manifest.yml file and replace watsonwork-sentiment with any app name of your choosing that is available in your Bluemix environment
3. Similarly, edit the package.json to replace the name watsonwork-sentiment with your app name
4. If desired, edit the public/index.html.  This is an informational screen only as there is no web functionality required
5. Make sure you are enabled with the latest CLI program from Bluemix
6. Issue cf push to create a new app in Bluemix with the above characteristics and get it started
7. Register a new app in http://developer.watsonwork.ibm.com/
  1. Enter name and description and add a webhook
  2. Leave webhook disabled and pick any name as it will only be used for your reference
  3. Select intent to listen to the `message-annotation-added` events
  4. Utilize the callback url of <your_bluemix_app_host>/webhook_callback unless you modified the code
  5. Save the app which will present with a window with 3 key pieces of information you will need to save:
    1. APP_ID
    2. APP_SECRET
    3. WEBHOOK_SECRET
8. Go to Bluemix and create runtime environment variables with the above names holding the corresponding values
9. Restart your app in Bluemix by clicking the restart button so it consumes the new environment
10. Go back to the http://developer.watsonwork.ibm.com/apps registration and edit your app and enable the webhook.
11. At this point you should see a window indicating the webhook has been enabled.  The log file for the app in Bluemix environment should also display confirmation that it processed the verification event as explained in http://developer.watsonwork.ibm.com/ section "Preparing your App to run"
12. Create a space and add this app to it.  You can test it by typing something like "great - thanks!" and pressing Enter.
