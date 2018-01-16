# Actions On Google: Actions SDK Sample using Node.js and Cloud Functions for Firebase

This sample shows how to create an app for the Google Assistant using the Actions SDK including integration with dashbot.io

## Setup Instructions

### Steps
1. Create an account on [https://www.dashbot.io](https://www.dashbot.io)
1. Create a google bot on dashbot.io (make note of the API_KEY)
1. Substitute the API_KEY created above for REPLACE_WITH_YOUR_DASHBOT_API_KEY in functions/index.js 
1. Use the [Actions on Google Console](https://console.actions.google.com) to add a new project with a name of your choosing.
1. Choose *Actions SDK* in the *Add actions to your app* section. A dialog pops up: leave it open because you will need it for an upcoming step.
1. Deploy the fulfillment webhook provided in the `functions` folder using [Google Cloud Functions for Firebase](https://firebase.google.com/docs/functions/):
   1. Follow the instructions to [set up and initialize Firebase SDK for Cloud Functions](https://firebase.google.com/docs/functions/get-started#set_up_and_initialize_functions_sdk). Make sure to select the project that you have previously generated in the Actions on Google Console and to reply "N" when asked to overwrite existing files by the Firebase CLI.
   1. Run `firebase deploy --only functions` and take note of the endpoint where the fulfillment webhook has been published. It should look like `Function URL (sayNumber): https://us-central1-YOUR_PROJECT.cloudfunctions.net/sayNumber`
1. Update the action package, `action.json`, replacing the placeholder value `YOUR_ENDPOINT_URL` with the value for Function URL obtained from the previous step.
1. [Install the gactions CLI](https://developers.google.com/actions/tools/gactions-cli) if you haven't already.
1. Go back to the Actions console, copy the command shown in the Actions console, replace `PACKAGE_NAME` with "action.json" and execute it in a shell. The final command should look like `gactions update --action_package action.json --project <YOUR_PROJECT_ID>`
1. Click *OK* in the Actions console to dismiss the *Use Actions SDK to add actions to your Assistant app* dialog.
1. Open the Simulator in the Actions console.
1. Type "Talk to my test app" in the simulator, or say "OK Google, talk to my test app" to any Actions on Google enabled device signed into your developer account.

Note: to use dashbot on firebase when you must have entered a credit card for google cloud (though you can still use it for free)

For more detailed on dashbot, see the [dashbot documentation](https://www.dashbot.io/docs).

For more detailed information on deployment, see the [documentation](https://developers.google.com/actions/sdk/deploy-fulfillment).

### Testing locally

1. Install [ngrok](https://ngrok.com/)
1. Run ngrok ```ngrok http 5000``` 
1. Go back to the Dialogflow console and select *Fulfillment* from the left navigation menu. Enable *Webhook*, set the value of *URL* to the ngrok url from the previous step, then click *Save*.
1. ```cd functions```
1. ```npm install```
1. ```npm start```

## References and How to report bugs
* Actions on Google documentation: [https://developers.google.com/actions/](https://developers.google.com/actions/).
* If you find any issues, please open a bug here on GitHub.
* Questions are answered on [StackOverflow](https://stackoverflow.com/questions/tagged/actions-on-google).

## How to make contributions?
Please read and follow the steps in the [CONTRIBUTING.md](CONTRIBUTING.md).

## License
See [LICENSE.md](LICENSE.md).

## Terms
Your use of this sample is subject to, and by using or downloading the sample files you agree to comply with, the [Google APIs Terms of Service](https://developers.google.com/terms/).

## Google+
Actions on Google Developers Community on Google+ [https://g.co/actionsdev](https://g.co/actionsdev).
