# Creating an iOS Cordova plugin

Cordova is webview-based multi-platform framework for mobile. A plugin is doing the interface between the browser Javascript engine and the host native language.

## Objective-C code

### .h 

```obj-c
/* UniversalLinks.h */

#import <Cordova/CDV.h>

@interface UniversalLinks : CDVPlugin

- (void)echo:(CDVInvokedUrlCommand*)command;

@end
```

### .m

```obj-c
/* UnivesrsalLinks.m */

#import "UniversalLinks.h"
#import <Cordova/CDV.h>

@implementation UnivesrsalLinks

- (void)echo:(CDVInvokedUrlCommand*)command
{
    CDVPluginResult* pluginResult = nil;
    NSString* msg = [command.arguments objectAtIndex:0];

    if (msg == nil || [msg length] == 0) {
        pluginResult = [CDVPluginResult resultWithStatus:CDVCommandStatus_ERROR];
    } else {
        /* http://stackoverflow.com/questions/18680891/displaying-a-message-in-ios-which-has-the-same-functionality-as-toast-in-android */
        UIAlertView *toast = [
            [UIAlertView alloc] initWithTitle:@""
            message:msg
            delegate:nil
            cancelButtonTitle:nil
            otherButtonTitles:nil, nil];

        [toast show];
        
        dispatch_after(dispatch_time(DISPATCH_TIME_NOW, 3 * NSEC_PER_SEC), dispatch_get_main_queue(), ^{
            [toast dismissWithClickedButtonIndex:0 animated:YES];
        });
        
        pluginResult = [CDVPluginResult resultWithStatus:CDVCommandStatus_OK messageAsString:msg];
    }

    [self.commandDelegate sendPluginResult:pluginResult callbackId:command.callbackId];
}

@end
```

### .js

```javascript
var exec = require('cordova/exec');

exports.echo = function(arg0, success, error) {
    exec(success, error, "UniversalLinks", "echo", [arg0]);
};

exports.echojs = function(arg0, success, error) {
    if (arg0 && typeof(arg0) === 'string' && arg0.length > 0) {
        success(arg0);
    } else {
        error('Empty message!');
    }
};
```
