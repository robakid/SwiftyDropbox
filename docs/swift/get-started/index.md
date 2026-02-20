# Get Started

## Register your application

Before using this SDK, you should register your application in the [Dropbox App Console](https://dropbox.com/developers/apps). This creates a record of your app with Dropbox that will be associated with the API calls you make.

## Obtain an OAuth 2.0 token

All requests need to be made with an OAuth 2.0 access token. An OAuth token represents an authenticated link between a Dropbox app and a Dropbox user account or team.

Once you've created an app, you can go to the App Console and manually generate an access token to authorize your app to access your own Dropbox account.
Otherwise, you can obtain an OAuth token programmatically using the SDK's pre-defined auth flow. For more information, see [Handling the authorization flow](../configure-your-project#handling-the-authorization-flow).
