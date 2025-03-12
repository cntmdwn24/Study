# flutter_native_splash

**flutter_native_splash**는 Flutter 앱의 네이티브 스플래시 화면을 쉽게 설정할 수 있게 도와주는 Flutter 패키지입니다. 이 패키지를 사용하면, 앱의 로딩 화면(스플래시 화면)을 네이티브(Android/iOS) 방식으로 설정할 수 있어, 앱이 시작될 때 원하는 이미지나 로고를 표시할 수 있습니다.

[flutter_native_splash 패키지 링크](https://pub.dev/packages/flutter_native_splash)

### 설치방법

1. **터미널에서 패키지 설치**  
    아래 명령어를 터미널에 입력하여 `flutter_native_splash` 패키지를 자동으로 추가합니다.
    ```bash
    flutter pub add flutter_native_splash
    ```

2. **패키지 설치 완료 후**  
    프로젝트의 루트 디렉토리 `flutter_native_splash.yaml` 파일을 생성합니다.  
    `flutter_native_splash.yaml` 에 아래 코드를 입력합니다.
    
    ```bash
    flutter_native_splash:

    # This package generates native code to customize Flutter's default white native splash screen
    # with background color and splash image.
    # Customize the parameters below, and run the following command in the terminal:
    # flutter pub run flutter_native_splash:create
    # To restore Flutter's default white splash screen, run the following command in the terminal:
    # flutter pub run flutter_native_splash:remove

    # color or background_image is the only required parameter.  Use color to set the background
    # of your splash screen to a solid color.  Use background_image to set the background of your
    # splash screen to a png image.  This is useful for gradients. The image will be stretch to the
    # size of the app. Only one parameter can be used, color and background_image cannot both be set.
    color: "#FFFFFF"
    #background_image: "assets/background.png"

    # Optional parameters are listed below.  To enable a parameter, uncomment the line by removing
    # the leading # character.

    # The image parameter allows you to specify an image used in the splash screen.  It must be a
    # png file and should be sized for 4x pixel density.
    image: assets/images/img_logo.png

    # This property allows you to specify an image used as branding in the splash screen. It must be
    # a png file. Currently, it is only supported for Android and iOS.
    #branding: assets/dart.png

    # Specify your branding image for dark mode.
    #branding_dark: assets/dart_dark.png

    # To position the branding image at the bottom of the screen you can use bottom, bottomRight,
    # and bottomLeft. The default values is bottom if not specified or specified something else.
    #
    # Make sure this content mode value should not be similar to android_gravity value and
    # ios_content_mode value.
    #branding_mode: bottom

    # The color_dark, background_image_dark, and image_dark are parameters that set the background
    # and image when the device is in dark mode. If they are not specified, the app will use the
    # parameters from above. If the image_dark parameter is specified, color_dark or
    # background_image_dark must be specified.  color_dark and background_image_dark cannot both be
    # set.
    #color_dark: "#042a49"
    #background_image_dark: "assets/dark-background.png"
    #image_dark: assets/splash-invert.png

    # The android, ios and web parameters can be used to disable generating a splash screen on a given
    # platform.
    #android: false
    #ios: false
    #web: false

    # The position of the splash image can be set with android_gravity, ios_content_mode, and
    # web_image_mode parameters.  All default to center.
    #
    # android_gravity can be one of the following Android Gravity (see
    # https://developer.android.com/reference/android/view/Gravity): bottom, center,
    # center_horizontal, center_vertical, clip_horizontal, clip_vertical, end, fill, fill_horizontal,
    # fill_vertical, left, right, start, or top.
    android_gravity: center
    #
    # ios_content_mode can be one of the following iOS UIView.ContentMode (see
    # https://developer.apple.com/documentation/uikit/uiview/contentmode): scaleToFill,
    # scaleAspectFit, scaleAspectFill, center, top, bottom, left, right, topLeft, topRight,
    # bottomLeft, or bottomRight.
    ios_content_mode: center
    #
    # web_image_mode can be one of the following modes: center, contain, stretch, and cover.
    #web_image_mode: center

    # To hide the notification bar, use the fullscreen parameter.  Has no effect in web since web
    # has no notification bar.  Defaults to false.
    # NOTE: Unlike Android, iOS will not automatically show the notification bar when the app loads.
    #       To show the notification bar, add the following code to your Flutter app:
    #       WidgetsFlutterBinding.ensureInitialized();
    #       SystemChrome.setEnabledSystemUIOverlays([SystemUiOverlay.bottom, SystemUiOverlay.top]);
    fullscreen: true

    # If you have changed the name(s) of your info.plist file(s), you can specify the filename(s)
    # with the info_plist_files parameter.  Remove only the # characters in the three lines below,
    # do not remove any spaces:
    #info_plist_files:
    #  - 'ios/Runner/Info-Debug.plist'
    #  - 'ios/Runner/Info-Release.plist'
    ```

## 패키지 실행
프로젝트의 터미널에 아래 코드를 입력합니다.
```bash
flutter pub run flutter_native_splash:create
```
### 변경사항이 있을 때
```bash
flutter pub run flutter_native_splash:remove
```
```bash
flutter pub run flutter_native_splash:create
```

## 스플래시 화면을 더 오래 띄우고 싶을 때
스플래시 화면을 더 오래 띄우고 싶으면 `main.dart` 파일을 조금 수정해주면 된다
```bash
void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  await Future.delayed(const Duration(seconds: 2));
  
  runApp(MyApp());
}
```