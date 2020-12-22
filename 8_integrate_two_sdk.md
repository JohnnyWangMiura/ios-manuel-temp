
# How to integrate [CN] Pangle SDK and [Outside CN] Pangle SDK in the same project

Starting from version 3.4.0.0, pangle iOS SDK will be divided into `[CN] Pangle SDK` and `[Outside CN] Pangle SDK`.

The SDK is divided into three General libraries, one CN library and one Outside_CN library.

| -| - |
|---------------------|------------------------------------------------------------|
| General libraries   | BUAdSDK.bundle、BUAdSDK.framework、BUFoundation.framework  |
| Outside_CN library  | BUVAAuxiliary.framework                                    |
| CN library          | BUCNAuxiliary.framework                                    |



## Import Outside_CN Pangle SDK
When you wanna only import `Outside_CN Pangle SDK` separately, you need to import the `General libraries` and `Outside_CN library`：BUAdSDK.bundle、BUAdSDK.framework、BUFoundation.framework、BUVAAuxiliary.framework

## Import CN Pangle SDK
When you wanna only import `CN Pangle SDK` separately, you need to import import the `General libraries` and `CN library`：BUAdSDK.bundle、BUAdSDK.framework、BUFoundation.framework、BUCNAuxiliary.framework

## Import both CN Pangle SDK and Outside_CN Pangle SDK
All five files need to be imported：BUAdSDK.bundle、BUAdSDK.framework、BUFoundation.framework、BUVAAuxiliary.framework、BUCNAuxiliary.framework

If you import both `CN Pangle SDK` and `Outside_CN Pangle SDK`, `setTerritory` is required (mark the user as CN or Outside CN), it should be done before initializing Pangle SDK.

**Note**：
- **This method must be called before initializing Pangle SDK.**
- Pangle will not return ads when the territory is incorrect. (for example, you Set Territory to BUAdSDKTerritory_CN  but the user's IP is outside of China Mainland, same the other way round.)

```objective-c
///This property should be set when both BUVAAuxiliary.framework and BUCNAuxiliary.framework are imported in your project, otherwise it does not need to be set. You must set Territory before set APPID.
///@param territory : Regional value: 1.BUAdSDKTerritory_CN  2.BUAdSDKTerritory_NO_CN
[BUAdSDKManager setTerritory: (BUAdSDKTerritory)territory];
```
