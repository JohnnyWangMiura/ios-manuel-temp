# Import Pangle SDK

## Method One:
Import
  - `BUAdSDK.framework`
  - `BUFoundation.framework`
  - `BUAdSDK.bundle`
  - `BUVAAuxiliary.framework`

  to the project manually.

<img src="pics/import.png" alt="drawing" width="300"/>


**Note: Updating all frameworks and bundle files is needed when upgrading the SDK.**

​
Please make sure that `Copy Bundle Resource` contains `BUAdSDK.bundle`.

<img src="pics/copy_bundle.png" alt="drawing" width="300"/>

​
## Xcode Compiler Option Settings

### Add Permissions

Add the parameter `-objc` to `Other Linker Flags` in build settings, and the SDK supports `- all_ load`

#### Detailed Steps:

<img src="pics/add_permission.png" alt="drawing" width="300"/>


#### Operating environment configuration
- Support  IOS 9. X and above;
- SDK compilation environment Xcode 11;
- Supporting architecture: x86-64, armv7, arm64,i386

### Add Dependency Libraries

Project needs to find Link Binary With Libraries in `TARGETS` - > `Build Phases`, click "+", and then add the following dependent libraries in order.

- StoreKit.framework
- MobileCoreServices.framework
- WebKit.framework
- MediaPlayer.framework
- CoreMedia.framework
- AVFoundation.framework
- CoreTelephony.framework
- SystemConfiguration.framework
- AdSupport.framework
- CoreMotion.framework
- Accelerate.framework
- libresolv.9.tbd
- libc++.tbd
- libz.tbd
- libsqlite3.tbd
- libbz2.tbd
- libxml2.tbd
- libiconv.tbd
- Security.framework
- Add the `ImageIO.framework` if the above dependency library is still reporting errors.

Detailed Steps:

<img src="pics/add_permission_2.png" alt="drawing" width="300"/>


​
### Add language configuration

​<img src="pics/add_language.png" alt="drawing" width="300"/>
