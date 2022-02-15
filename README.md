

# react-native-geocoder --> forked to work with the latest react-native
Made changes to work with gradle 7. 

Pro tip: Autolinking these days will get you pretty far


## Install
```
npm install --save react-native-geocoder && react-native-link
```
I dont think react-native-link is necessary but I've added it just to be safe
## iOS
Autolinking is nice
```
cd ios && pod install && cd ..
```

## Android
1. In `android/setting.gradle`

```gradle
...
include ':react-native-geocoder', ':app'
project(':react-native-geocoder').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-geocoder/android')
```

3. In `android/app/build.gradle` (compile is no more so use implementation)

```gradle
...
dependencies {
    ...
    implementation project(':react-native-geocoder')
}
```
4. register module (in MainApplication.java)

```java
import com.devfd.RNGeocoder.RNGeocoderPackage; // <--- import
/*
Autolinking may automatically detect RNGeocoderPackage. If you get an error similar to the one found here 
https://github.com/devfd/react-native-geocoder/issues/96 
then comment out packages.add( new RNGeocoderPackage() );
*/
public class MainActivity extends ReactActivity {
  ......

  @Override
        protected List<ReactPackage> getPackages() {
          @SuppressWarnings("UnnecessaryLocalVariable")
          List<ReactPackage> packages = new PackageList(this).getPackages();
          // Packages that cannot be autolinked yet can be added manually here, for example:
          // packages.add(new MyReactNativePackage());
          packages.add( new RNGeocoderPackage() );
          return packages;
        }

  ......

}

```
## That's all folks
I've made minimum changes to the original repo. In fact the changes were so small that I decided to push all the changes from the web the minute I got the geocoder working in my project. For documentation check out [original repo](https://github.com/devfd/react-native-geocoder)
