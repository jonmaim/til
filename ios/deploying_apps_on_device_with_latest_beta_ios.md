# Deploying apps on device with latest beta iOS

Keeping up with latest beta iOS is great for catching new bugs on your development apps before your users. 

However it means also keeping up with beta Xcode as well. This is the error you'll get if your Xcode is not the latest beta one:

![device support files needed](/ios/device_support_files_needed.png)

Each new Xcode is several GBs to be downloaded, which makes the process not lean and cumbersome.

Fortunately, you actually don't need to download and install a new Xcode each time a new beta iOS is available, you only need the latest device support files which are only a few MBs to download. 

Some nice folks are publishing these files for us to include in our current non-beta Xcode: [https://github.com/iGhibli/iOS-DeviceSupport/tree/master/DeviceSupport](https://github.com/iGhibli/iOS-DeviceSupport/tree/master/DeviceSupport)

Find your beta version number or look in the pull requests if it is not included yet, somebody might have already found them.

Unzip the folder locally in `/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/`. 

Restart Xcode and voila!
