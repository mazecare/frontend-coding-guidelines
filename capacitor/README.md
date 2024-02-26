# Capacitor Guidelines

This Document covers the information for developing a cross-platform app using [Capacitor](https://capacitorjs.com/). The project using this platform usually consists of three different apps within the same codebase: Web, Android and IOS.

## General Information

### Next JS + Ionic + Capacitor

- **MUST KNOW**, use the Ionic component for the Header and Footer to make the mobile app work properly on both iOS and Android. In this case, to preserve the safe area at the top (notch and status bar) and the bottom area for iOS devices.
- **MUST KNOW**, during development('next dev'), Capacitor will never detect the app as native even on Android Simulator or Xcode Simulator, condition for native can ONLY detected when running 'next export'.
- The very first approach when building a mobile app using web technology (with our stack whether it's React or Vue), we shall use the UI components that are meant for building mobile apps. In our case the one that is provided by the Ionic Frameworks. Then we can modify and style from that. Don't create our own first, unless you want to go back and fix the code later. With the components that are provided by Ionic, it will automatically translate to each platform; iOS and Android. Just take a look what are the necessary components, (maybe Header, Footer, Content, Floating Button, NavBar) then modify from there. Because we're building mobile apps (well, still is a Webview), but we gotta follow their rules and have this kind of approach.
- When using the Ionic web component, there's a little customization that can be done. Because Ionic is aiming to look as native as possible for each platform. For example the look of Apple App Store and Google Play Store.
- The app must be able to run purely client-side and [use Next.js's Export command](https://nextjs.org/docs/pages/building-your-application/deploying/static-exports), which means no Server Side Rendering in this code base. There is likely a way to SSR and a fully static Next.js app in tandem but it requires a Babel plugin or would involve a more elaborate mono repo setup with code sharing that is out of scope for this project.
- Additionally, Next.js routing is not really used much in this app beyond a catch-all route to render the native app shell and engage the Ionic React Router. This is primarily because Next.js routing is not set up to enable native-style transitions and history state management like the kind Ionic uses.

### Next JS + Konsta UI + Capacitor

- **MUST KNOW**, use the correct layout from the Konsta UI component for the Header and Footer to make the mobile app work properly on both iOS and Android to preserve the safe area at the top (notch and status bar) and the bottom area for iOS devices.
- Another point is almost the same as above.

## Development Approach

### Mobile Development Tips

- Use UI components that are already provided by the library that support Mobile Apps. (KonstaUI or Ionic)
- Always use the latest dependency version.
- Always check the latest documentation, [here](https://capacitorjs.com/).
- Make sure to check the CSS compatibility for older Mobile Devices, because Capacitor runs on Webview, check the Webview version of each OS, Android Webview and IOS Webview.
- Use appRestoredResult listener for plugins such as Camera to prevent data loss if the app is being killed by mobile OS.
- Disable the scrollbar on Android if it breaks the UI by hiding it from the native code, use this.

```java
public class MainActivity extends BridgeActivity {
    @Override public void onStart() {
        super.onStart();
        bridge.getWebView().setVerticalScrollBarEnabled(false);
    }
}
```

### Important Capacitor Official Plugin

- [Storage](https://capacitorjs.com/docs/apis/preferences): useful to store tokens and any other useful information on mobile devices, [recommended](https://capacitorjs.com/docs/guides/storage) solution to store local data.
- [Camera](https://capacitorjs.com/docs/apis/camera): useful to take a photo or open a gallery.
- [Network](https://capacitorjs.com/docs/apis/network): useful to check current network connections.
- [Splash Screen](https://capacitorjs.com/docs/apis/splash-screen): useful to configure the splash screen of the app.
- [Status Bar](https://capacitorjs.com/docs/apis/status-bar): useful to set the transparency of the phone to match with the app theme.
- [Push Notifications](https://capacitorjs.com/docs/apis/push-notifications): useful to set the mobile push notifications.

### Tools

- [Capacitor Assets](https://capacitorjs.com/docs/guides/splash-screens-and-icons): use this to generate mobile assets.

### Debugging

- Use browser inspector, [GUIDE](https://capacitorjs.com/docs/vscode/debugging)

### Mobile File Changes Based On Feature

| Feature             | Plugin                                 | Android             | Ios                      | Docs                                                           |
| ------------------- | -------------------------------------- | ------------------- | ------------------------ | -------------------------------------------------------------- |
| Ios Web RTC         | cordova-plugin-iosrtc                  | AndroidManifest.xml | Info.plist               |                                                                |
|                     |                                        |                     | Podfile                  |                                                                |
| Google Auth         | @codetrix-studio/capacitor-google-auth | MainActivity.java   | Info.plist               |                                                                |
|                     |                                        | strings.xml         | GoogleService-Info.plist |                                                                |
| Facebook Auth       | @capacitor-community/facebook-login    | MainActivity.java   | AppDelegate.swift        |                                                                |
|                     |                                        | AndroidManifest.xml | Info.plist               |                                                                |
|                     |                                        | strings.xml         |                          |                                                                |
| Disable Orientation |                                        |                     |                          | [LINK](https://capacitorjs.com/docs/guides/screen-orientation) |

### Publishing

- Always update the release version for both platforms on each release.
- Make sure to define a clear description for IOS Plugin permission.

### Other Useful Information

- [Setting up push notification](https://enappd.com/blog/firebase-push-notification-in-ionic-react-capacitor/111)
- [Starter Template For Ionic](https://github.com/mlynch/nextjs-tailwind-ionic-capacitor-starter)
- [Capacitor Forums](https://forum.ionicframework.com/)
- [Next JS Export](https://nextjs.org/docs/pages/building-your-application/deploying/static-exports)
