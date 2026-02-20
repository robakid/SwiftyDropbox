# Modifications

If you're interested in modifying the SDK codebase, you should take the following steps:

1. Clone the GitHub repository to your local filesystem
2. Run `git submodule init` and then `git submodule update`
3. Navigate to `TestSwifty_[iOS|macOS]`
4. Check the CocoaPods version installed (via `pod --version`) is same as "locked" in `TestSwifty_[iOS|macOS]/Podfile.lock`
5. Run `pod install`
6. Open `TestSwifty_[iOS|macOS]/TestSwifty_[iOS|macOS].xcworkspace` in Xcode
7. Implement your changes to the SDK source code

To ensure your changes have not broken any existing functionality, you can run a series of integration tests:

1. Create a new app on [https://www.dropbox.com/developers/apps/](https://www.dropbox.com/developers/apps/), with "Full Dropbox" access. Note the App key
2. Open `Info.plist` and configure the "URL types > Item 0 (Editor) > URL Schemes > Item 0" key to `db-<APP_KEY>`
3. Open `AppDelegate.swift` and replace `"FULL_DROPBOX_APP_KEY"` with the App key as well
4. Run the test app on your device and follow the on-screen instructions

To run and develop against the unit tests instead of the integration tests, open the root of the cloned repository in Xcode. Please run the integration tests after development.
