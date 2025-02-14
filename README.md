# Keyboard Observing ⌨️
### A Combine-based solution for observing and avoiding the keyboard in SwiftUI.

![Swift Support](https://img.shields.io/badge/Swift-5.1-orange.svg) 
![Platform](https://img.shields.io/badge/Platforms-iOS-lightgray.svg?style=flat)
[![SwiftPM Compatible](https://img.shields.io/badge/SwiftPM-Compatible-brightgreen.svg)](https://swift.org/package-manager/)

## About

This package give you the ability to observe changes to keyboard state using the `Keyboard` `ObservableObject` type.

It also provides a `KeyboardObservingView` that adjusts it's content to avoid the keyboard.

![Demo](./images/demo.gif)


## Requirements

- iOS 13.0+
- Xcode 11+
- Swift 5.1+

## Getting Started


### 1. Add a Keyboard to your environment

In your SceneDelegate.swift file, add a `Keyboard` property, and add it to your scene's environment.

```
import KeyboardObserving

class SceneDelegate: UIResponder, UIWindowSceneDelegate {

  var window: UIWindow?

  // A Keyboard that will be added to the environment.
  var keyboard = Keyboard()


  func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
    // Use this method to optionally configure and attach the UIWindow `window` to the provided UIWindowScene `scene`.
    // If using a storyboard, the `window` property will automatically be initialized and attached to the scene.
    // This delegate does not imply the connecting scene or session are new (see `application:configurationForConnectingSceneSession` instead).

    // Use a UIHostingController as window root view controller
    if let windowScene = scene as? UIWindowScene {
      let window = UIWindow(windowScene: windowScene)
      window.rootViewController = UIHostingController(
        rootView: YourRootView()
          // Adds the keyboard to the environment
          .environmentObject(keyboard)
      )
      self.window = window
      window.makeKeyAndVisible()
    }
  }
}
```

### 2. Create your View

Add your view's content inside of a `KeyboardObservingView` .

```
import KeyboardObserving

struct YourView: View {

  var body: some View {
    KeyboardObservingView {
      // Your content goes here!
    }
  }
}
```
