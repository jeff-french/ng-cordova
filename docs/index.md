---
layout: content
title: ngCordova - Document and Examples - by the Ionic Framework Team
---

## Examples and Docs

### AngularJS Module

To use any of the plugin wrappers below, all you need to do is link to the `ng-cordova.js` file in your app. Then, include `ngCordova` as a dependency in your angular module:

```javascript
angular.module('myApp', ['ngCordova'])
```

### `$cordovaCamera`

This service makes it easy to use the [`org.apache.cordova.camera`](https://github.com/apache/cordova-plugin-camera) plugin to take pictures and video
from a device:

```javascript

module.controller('PictureCtrl', function($scope, $cordovaCamera) {

  $scope.takePicture = function() {
    $cordovaCamera.getPicture({

      // See all the possible Camera options from the Camera docs [1]:
      /// https://github.com/apache/cordova-plugin-camera/blob/master/doc/index.md#cameraoptions

    }).then(function(imageData) {

      // Success! Image data is here

    }, function(err) {

      // An error occured. Show a message to the user

    });
  }

});
```

[1] [https://github.com/apache/cordova-plugin-camera/blob/master/doc/index.md#cameraoptions](https://github.com/apache/cordova-plugin-camera/blob/master/doc/index.md#cameraoptions)

### `$cordovaGeolocation`

Grab the current location of the user, or grab continuous location changes:

```javascript
module.controller('PictureCtrl', function($scope, $cordovaGeolocation) {
  $scope.getPosition = function() {
    $cordovaCamera.getCurrentPosition().then(function(position) {
      // Position here: position.coords.latitude, position.coords.longitude
    }, function(err) {});
  }

  $scope.trackPosition = function() {
    $cordovaCamera.watchPosition().then(function() {
      // Not currently used
    }, function(err) {
      // An error occured. Show a message to the user
    }, function(position) {
      // Active updates of the position here
    });
  }

});
```

### `$cordovaBarcodeScanner`

Scan QR codes and bar codes. From the [wildabeast/BarcodeScanner](https://github.com/wildabeast/BarcodeScanner) plugin.


```javascript
module.controller('MyCtrl', function($scope, $cordovaBarcodeScanner) {
  $cordovaBarcodeScanner.scan().then(function(result) {
    // Scanner result
  }, function(err) {
  });
```

### `$cordovaCompass`

Monitor device orientation through the digital compass on a device.

```javascript
module.controller('PictureCtrl', function($scope, $cordovaCompass) {
  $scope.trackHeading = function() {
    // Pass options in [1]
    $cordovaCamera.watchHeading(options).then(function() {
      // Not currently used
    }, function(err) {
      // An error occured. Show a message to the user
    }, function(position) {
      // Active updates of the heading here
    });
  }
});
```

[1] [https://github.com/apache/cordova-plugin-device-orientation/blob/master/doc/index.md#navigatorcompasswatchheading](https://github.com/apache/cordova-plugin-device-orientation/blob/master/doc/index.md#navigatorcompasswatchheading)

### `$cordovaAccelerometer`

Track accelerometer changes as the device is moved, rotated, and shaken.


```javascript
module.controller('MyCtrl', function($scope, $cordovaAccelerometer) {
  $cordovaAccelerometer.getCurrentAcceleration().then(function(result) {

    // Accelerometer data available in result

  }, function(err) {
  
    // An error occured. Show a message to the user?

  });

  $cordovaCamera.watchAcceleration({
  }, function(result) {
  }, function(err) {
  });

  // Clear a watch by watchID
  $cordovaAccelerometer.clearWatch(watchID);
});
```