

# Initialize Pangle SDK

## Interface
Currently, the interface provides the following class methods.

```objective-c
@property (nonatomic, copy, readonly, class) NSString *SDKVersion;
​
/// Register the App key that’s already been applied before requesting an ad from Pangle Plarform.                                                       @param appID : the unique identifier of the App
+ (void)setAppID:(NSString *)appID;

///This property should be set when integrating non-China areas at the same time, otherwise it does not need to be set.you‘d better set Territory first,  if you need to set them.                                                      @param territory : Regional value: 1.BUAdSDKTerritory_CN  2.BUAdSDKTerritory_NO_CN
+ (void)setTerritory:(BUAdSDKTerritory)territory;

 ///Configure development mode.                                            @param level : default BUAdSDKLogLevelNone
+ (void)setLoglevel:(BUAdSDKLogLevel)level;

///Set the COPPA of the user, COPPA is the short of Children's Online Privacy Protection Rule, the interface only works in the United States.              @params Coppa 0 adult, 1 child
+ (void)setCoppa:(NSUInteger)Coppa;
​
/// Set the user's keywords, such as interests and hobbies, etc.
/// Must obtain the consent of the user before incoming.
+ (void)setUserKeywords:(NSString *)keywords;
​
/// set additional user information.
+ (void)setUserExtData:(NSString *)data;
​
///Fields to indicate SDK whether the user grants consent for personalized ads, the value of GDPR : 0 User has granted the consent for personalized ads, SDK will return personalized ads; 1: User doesn't grant consent for personalized ads, SDK will only return non-personalized ads.
+ (void)setGDPR:(NSInteger)GDPR;
​​
/// Notice that Developers must open GDPR Privacy for the user before setAppID.
+ (void)openGDPRPrivacyFromRootViewController:(UIViewController *)rootViewController confirm:(BUConfirmGDPR)confirm;
​
/// get appID
+ (NSString *)appID;
​
/// get GDPR
+ (NSInteger)GDPR;
```

​
## Pass Appid to initialize Pangle SDK
You must initialize Pangle SDK before loading Pangle ads. This needs to be done only once, ideally at app launch (in AppDelegate method)

```objective-c
//pass appid to initialize pangle sdk
[BUAdSDKManager setAppID:@"xxxxxx"];
```


**Warning: Ads may be preloaded by the Pangle Ads SDK or mediation partner SDKs after initial. If you need to obtain consent from users in the European Economic Area (EEA) or users under age, please ensure you do so before initializing the Pangle Ads SDK.**

See SDK Demo Project or [GitHub](https://github.com/bytedance/Bytedance-UnionAD/blob/master/Example/BUDemo/AppDelegate.m) for more details.

## Redirect Readme

All the rootViewController parameters in Ad APIs must be provided to process ad redirects. In the SDK, all redirects use the present method. Therefore, make sure that the passed rootViewController parameters are not null and do not have other present controllers. Otherwise the present will fail because presentedViewController already exists.

## GDPR
Pangle provides a tool for publishers to request consent for personalized ads as well as to handle certain requirements. Publishers can use the following method to handle these requests by showing a single a form, as all of the configuration happens in the Funding Choices UI.

```objective-c
+ (void)openGDPRPrivacyFromRootViewController:(UIViewController *)rootViewController confirm:(BUConfirmGDPR)confirm;
```

Publishers could also make a tool themselves to request consent.

## COPPA
Pangle also compliances with Children’s Online Privacy Protection Act (COPPA), Pangle SDK provides setCoppa method for publishers. At the moment, Pangle won't return ads for Children (Under the age of 13).
