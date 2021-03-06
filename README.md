[![](https://img.shields.io/badge/bluemix-powered-blue.svg)](https://bluemix.net)
[![Platform](https://img.shields.io/badge/platform-ios_swift-lightgrey.svg?style=flat)](https://developer.apple.com/swift/)

# Create a virtual assistant for iOS using Watson Assistant

This IBM Cloud Starter Kit will showcase the Watson Assistant service on iOS. We'll walk through setting up Xcode, installing dependencies, and running the application.

By running this code, you'll understand how to:

* Interact with the Watson Assistant service
* Use the Watson Swift SDK
* Integrate Watson Assistant and Swift to create a virtual assistant

![](https://raw.githubusercontent.com/IBM/pattern-utils/master/virtual-assistant-for-ios/architecture.png)

## Flow

1. The user enters a message with an iOS device.
2. The message is sent to the IBM Watson Assistant service, the sent message is displayed on the iOS device.
3. Watson Assistant responds and sends a message back to be displayed on the iOS device.

## Included Components

* [IBM Watson Assistant](https://www.ibm.com/watson/developercloud/conversation.html): Build, test and deploy a bot or virtual agent across mobile devices, messaging platforms, or even on a physical robot.

## Featured technologies

* [Swift](https://www.ibm.com/cloud/swift): Swift is a general-purpose, multi-paradigm, compiled programming language developed by Apple Inc. for iOS, macOS, watchOS, tvOS, and Linux.

## Requirements

* iOS 9.0+
* Xcode 9
* Swift 4.0
* [CocoaPods](https://cocoapods.org/)
    * If not installed, run: `sudo gem install cocoapods`
* [Carthage](https://github.com/Carthage/Carthage): To manage dependencies and build binary frameworks.
    * If not installed, run: `brew update; brew install carthage`

## Steps

> As an alternative to the steps below, you can [create this project as a starter kit on IBM Cloud](https://cloud.ibm.com/developer/appledevelopment/create-app?defaultDeploymentToolchain=&defaultLanguage=IOS_SWIFT&env_id=ibm%3Ayp%3Aus-south&navMode=catalog&starterKit=448c7258-7c69-3cf3-96b2-0660f891185c), which automatically provisions required services, and injects service credentials into a custom fork of this pattern.

1. [Use CocoaPods to create an Xcode workspace](#1-use-cocoapods-to-create-an-xcode-workspace)
2. [Use Carthage to install the Watson Swift SDK](#2-use-carthage-to-install-the-watson-swift-sdk)
3. [Configure Watson Assistant](#3-configure-watson-assistant)

### 1. Use CocoaPods to create an Xcode workspace

For this starter, a pre-configured `Podfile` has been provided. To download and install the required dependencies, run the following command in your project directory:

```bash
$ cd {APP_Name}
$ pod install
```

> NOTE: If the CocoaPods repository was not configured, we'd have to run `pod setup` first.

Now open the Xcode workspace to see what the project looks like. We can also use Xcode to run the application with Xcode's simulator, which we'll do in a few steps.

```bash
$ open {APP_Name}.xcworkspace
```

> NOTE: If you run into any issues during the pod install, it is recommended to run a pod update by running: `pod update; pod install`

### 2. Use Carthage to install the Watson Swift SDK

This starter uses the Watson Swift SDK in order to use the Watson Assistant service, meaning we have to build the dependencies and frameworks. To do so, run the following command:

```bash
$ carthage update --platform iOS
```

For this starter, a pre-configured `Cartfile` has been included. If it was not included, to use the Watson Swift SDK in any applications we would need to specify it in our `Cartfile`:

```ini
github "watson-developer-cloud/swift-sdk"
```

> NOTE: You may have to run `carthage update --platform iOS --no-use-binaries` if the binary is a lower version than your current version of Swift.

Once the build has completed, the frameworks can be found in the **Carthage/Build/iOS/** folder. The Xcode project in this starter already includes framework links to the following frameworks in the directory: `AssistantV1.framework`.

> NOTE: If you build your Carthage frameworks in a separate folder, you will have to drag-and-drop the above frameworks into your project and link them in order to run this starter successfully.

### 3. Configure Watson Assistant

Ensure you have a running Watson Assistant service, if you do not, create one by going to the link below:

  * [**Watson Assistant**](https://cloud.ibm.com/catalog/services/conversation)

Every chatbot needs a dialog, right? To make things easier we've coded this application to look at the available conversations for a specified Watson Assistant service and use the first workspace it finds.

To easily obtain a conversation dialog we can simply launch the Watson Assistant Tool and view the sample conversation that is provided by Watson Assistant. This is enough to get your application running locally.

#### (Optional) 3.1 Specify your own conversation

If you prefer to specify your own conversation you can import or create a new dialog with the Watson Assistant Tool. To do that, follow the [documentation online](https://cloud.ibm.com/docs/services/conversation/dialog-build.html). Once created we need to find the workspace ID. See the image below as a guide to finding the workspace ID.

![](https://raw.githubusercontent.com/IBM/pattern-utils/master/watson-assistant/assistant-workspace-id.gif)

Once we have the workspace ID we'll need to let our application know about it. We need to update `BMSCredentials.plist` by adding a `workspaceID` entry, like below:

![](https://raw.githubusercontent.com/IBM/pattern-utils/master/virtual-assistant-for-ios/workspaceID.png)

## Sample Output

You can now run the application on a simulator or physical device. Try a few queries for yourself:

* _Where are you located?_
* _What are your hours?_
* _I'd like to book an appointment?_

> A quick snapshot of a conversation.

![](https://raw.githubusercontent.com/IBM/pattern-utils/master/virtual-assistant-for-ios/output11.png)

> A full walkthrough of a sample conversation.

![](https://raw.githubusercontent.com/IBM/pattern-utils/master/virtual-assistant-for-ios/output.gif)

## Links

* [Swift Programming Guide](https://cloud.ibm.com/docs/swift/index.html#set_up): Tutorial on Swift app development.
* [Add a Service to Your App](https://cloud.ibm.com/docs/apps/reqnsi.html#add_service): Learn how to add a resource to your cloud-native app.

## Learn More

* [Other Starter Kits](https://cloud.ibm.com/developer/appservice/starter-kits/): Enjoyed this Starter Kit? Check out our other Starter Kits.
* [Architecture Center](https://www.ibm.com/cloud/garage/architectures): Explore Architectures that provide flexible infrastructure solutions.
* [IBM Watson Assistant Docs](https://cloud.ibm.com/docs/services/conversation/getting-started.html#gettingstarted)

## License

This code pattern is licensed under the Apache Software License, Version 2.  Separate third party code objects invoked within this code pattern are licensed by their respective providers pursuant to their own separate licenses. Contributions are subject to the [Developer Certificate of Origin, Version 1.1 (DCO)](https://developercertificate.org/) and the [Apache Software License, Version 2](https://www.apache.org/licenses/LICENSE-2.0.txt).

[Apache Software License (ASL) FAQ](https://www.apache.org/foundation/license-faq.html#WhatDoesItMEAN)
