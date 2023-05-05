# react-native-mjdunion

[![npm version](https://badge.fury.io/js/react-native-mjdunion.svg)](https://badge.fury.io/js/react-native-mjdunion)

京东联盟SDK

iOS Version: 3.5.0

Android Version: 3.5.0

## 开始

`$ npm install react-native-mjdunion --save`

## 其他配置

### ios

1. 将下载的京东联盟iOS SDK 中的`JDSDK.bundle`引入到项目中
2. URL Schemes 添加 sdkback + 京东联盟appKey
3. LSApplicationQueriesSchemes 添加

```xml
<key>LSApplicationQueriesSchemes</key>
<array>
  <string>openapp.jdmobile</string>
  <string>jdlogin</string>
  <string>openapp.jdpingou</string>
  <string>openjdlite</string>
</array>
```

### Android

1. 替换模块中的安全图片`android/app/src/main/res/raw/safe.jpg`
2. 打开 android/app/build.gradle ，在 defaultConfig 下添加:

   ```js
   manifestPlaceholders = [
   KeplerScheme  : "xxxxxx" // 京东联盟SDK中AndroidManifest.xml 中的值
   ]
   ```

3. 配置混淆`-keep class com.kepler.jd.**{ public <fields>; public <methods>; public *; }`

## 使用

```javascript
import * as mJdunion from 'react-native-mjdunion';

let param = {
  isOpenByH5: false,
  processColor: '#ed0000',
  backTagID: '',
  openType: 'push',
  actId: '',
  ext: '',
  position: '',
  customParams: {},
};

// 初始化
let resInit = await mJdunion.initSDK({
  appKey: '',
  appSecret: '',
  appAndroidID: '', // 可为空
  appOaid: '',
})

// 打开京东app
let res = await mJdunion.showItemByUrl(params)

// 打开京喜app
let res = await mJdunion.showJXItemByUrl(params)

// 打开京喜特价app
let res = await mJdunion.showJXLiteItemByUrl(params)
```
