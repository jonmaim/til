# Deploying apps on device with latest beta iOS

Keeping up with latest beta iOS is great for catching new bugs on your development apps before your users. 

However it means also keeping up with beta Xcodes as well. Each new Xcode is several GBs to be downloaded. This makes the process not lean at all.

Fortunately, you actually don't need a new Xcode, you only need the latest device support files which are only a few MBs to download. 

Some nice folks are publishing these files for us to include in our current Xcode (non-beta): [https://github.com/iGhibli/iOS-DeviceSupport/tree/master/DeviceSupport](https://github.com/iGhibli/iOS-DeviceSupport/tree/master/DeviceSupport)

Find your beta version number or look in the pull requests if it is not included yet, somebody might have already found them.

Unzip the folder locally in `/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/`. 

Restart Xcode and voila!
