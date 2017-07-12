![Blackbox SDK](https://cdn.rawgit.com/blackbox-platform/blackbox-sdk-ios/master/img/blackbox.svg)

[![Build Status](https://travis-ci.org/blackbox-platform/blackbox-sdk-ios.svg?branch=master)](https://travis-ci.org/blackbox-platform/blackbox-sdk-ios)

[Blackbox Platform](https://www.blackbox-platform.com/) is your virtual campaign manager for
Apple Search Ads. It automatically selects keywords to bid on and automatically adjusts your
bid strategy to give you the best results for your money.

Integrating the Blackbox SDK into your app provides the platform with additonal information, enabling it to inform you about the profitability of your search ad campaign, helping it further optimise your bid strategy and providing the best return for your money.


# Getting started

## Setup

• Sign in or register at https://www.blackbox-platform.com/

• Create a new campaign, or find an existing campaign.

• From your campaign's dashboard, select ‘Integrate with Blackbox SDK’.

• Take a note of your API key and add it to your app's Info.plist file as the value for `BBPClientID`

![Xcode plist setup](https://cdn.rawgit.com/blackbox-platform/blackbox-sdk-ios/master/img/plist-setup.png)


## Installing the SDK

**Using CocoaPods (recommended):**

• Add BlackboxSDK to your podfile:

````
target 'MyApp' do
  pod 'BlackboxSDK', '~> 1.0'
end
````
• Run `pod update` to install.


**Manual installation:**

• Download a binary from https://github.com/blackbox-platform/blackbox-sdk-ios/releases/latest

• Drop BlackboxSDK into your xcode project.

• Add `BlackboxSDK.framework` to your project’s ‘Link Binary with libraries’ and ‘Copy files’ build phase, ensuring that ‘Frameworks’ is chosen as the destination.

![Xcode framework setup](https://cdn.rawgit.com/blackbox-platform/blackbox-sdk-ios/master/img/linker-setup.png)


## Recording revenue

You don't need to do anything else to record app installs and launches — BlackboxSDK takes care of that automatically.

If your app accepts payments, you can record revenue events using the SDK's `-recordRevenue:withCurrency:` method:

````
#import <BlackboxSDK/BlackboxSDK.h>

@interface MyViewController ()
@end

@implementation MyViewController

- (IBAction)handleSubmitPayment:(id)sender {
    [[BlackboxSDK sdk] recordRevenue:4.30 withCurrency:BBPCurrencyGBP];
}

@end
````