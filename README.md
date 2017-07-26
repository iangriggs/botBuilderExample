# BotBuilder Example

This tutorial walks through building a bot by using:

  - Microsoft LUIS (Language Understanding Intelligent Service)
  - The Bot Builder SDK for Node.js
  - Bot Framework Emulator for testing the bot

## Get Started
  - Create an account for use with [LUIS](https://www.luis.ai)
  - [Node.js](https://nodejs.org/en/) (working with 6.10) installed
  - clone or download this repo
  - From a command prompt or terminal, navigate to the repo folder
  - type `npm install`

### The Code

The main code for running your bot can be found in the `app.js` file.
Most of the code have comments describing what each part does.

The code basically allows you to do the following:

  - Sets up a local web service to listen for user messages
  - Connects to LUIS in order to find out what the user wants to know.
  - Responds back to the user with hopefully what the user asked for.

If we test the bot now (descibed in the below sections), then we wont get very far as the intents are never matched.
You would always get the default response: `Sorry, I did not understand ${session.message.text}. Type help if you need assistance.`

In order to get this all working with LUIS we need to first create a LUIS app.

### LUIS

In this example we have already two dialogs in place that match intents for `help` and `joke`.
We want to be able to use a [LUIS](https://www.luis.ai/applications) app in order to match these intents.

  - Create a new LUIS app
    - Name: JokeBot
    - Description: For telling jokes
    - Key to use: Leave blank
    - Click Create!

You will be directed to your new application, but, you have no intents yet.

#### Intents

Intents are the building blocks of your app; they link user requests with the actions that should be taken by your app.

So lets get started by creating your first intent:

  - Create an Intent
    - either by clicking on the intents menu on the left hand side, or 
    - the pop up that appears when you first create your app.
    - click Add intent
      - Name: joke
      - click save

We now have our first intent created, but now we need to include some utterances to train the intent.
(Utterances are sentences representing examples of user queries or commands that your application is expected to receive and interpret.)

We can start by adding a few utterances like:

  - tell me a joke
  - joke
  - give me a joke
  - what jokes do you know

These will appear in the table as `Not trained`, but we'll get to that.
Next, you want to `Save` your utterances and then select `Train & Test` on the menu found on the left hand side.

Train you application and after it has finished you should be able to test your utterances.

Type: `tell me a joke` in the input and your should get something back similar to:

```
Top scoring intent
joke (1)
Other intents
None (0.09)
```

We should now create another intent to match `help`

Following the same steps as previously create and intent with a name of `help`

We can start by adding a few utterances like:

  - help me
  - I need help
  - what can you do

Train you application again and after it has finished you should be able to test your utterances.

#### Publish

If your happy with your intent, we can select `Publish App` from the menu on the left hand side.

  - Select the BootStrapKey as the Endpoint Key
  - Change the Endpoint slot to `staging` under Publish settings
  - Hit Publish!

You should now have an endpoint URL that we can copy and use inside our code!

Example:

```
https://region.api.cognitive.microsoft.com/luis/v2.0/apps/made-up-code-?subscription-key=somekeyto use&staging=true&verbose=true&timezoneOffset=0&q=
```

## Update the code

  - TODO: add about the .env file here..

## Test your bot

Test your bot by using the Bot Framework Emulator to see it in action. The emulator is a desktop application that lets you test and debug your bot on localhost.

First, you'll need to [download](https://emulator.botframework.com/) and install the emulator. After the download completes, launch the executable and complete the installation process.

To listen to your bot, the default endpoint url would be: `http://127.0.0.1:3978/api/messages` and you can click `connect`.

### Start your bot

After installing the emulator, navigate to your bot's directory in a console window and start your bot:

 - type `node app.js`
