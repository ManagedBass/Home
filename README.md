# ManagedBass | Home
[![Chat on Gitter](https://img.shields.io/gitter/room/MathewSachin/ManagedBass.svg?style=flat-square)](https://gitter.im/MathewSachin/ManagedBass)  
Welcome to the Home Repository for ManagedBass.  
[(c) 2016 Mathew Sachin](LICENSE.md). All Rights Reserved.

ManagedBass is a Free Open-Source Cross-Platform .Net wrapper for the un4seen BASS audio library.

Bass and its Add-Ons can be downloaded at http://un4seen.com/  
ManagedBass is targeted for **Any CPU**, but bass Libraries(.dll/.so/.dylib/.a) are separate for x86, x64, ARM, etc.  
Download the versions you need.

See the [Sample Repositories](docs/Samples.md) for examples.

## Support Us
ManagedBass is a free alternative to the paid Bass.Net library and is made and maintained in personal time.
If you feel generous, you could donate to the [Gratipay team](https://gratipay.com/ManagedBass) or [Mathew Sachin on PayPal](https://www.paypal.me/MathewSachin) to show your support.

## ToDo

### Split per AddOn (v1.0)
The Next version of ManagedBass is under development at https://github.com/ManagedBass/ManagedBass.vNext  
The idea is to split the library into multiple NuGet packages depending on the AddOns required.

Much of the development is complete. Here are the finalising works to be done:
- Check validity of platform specifiers in NuSpec
  - `net45` for Desktops (Windows/Linux/Mac) - *Checked for Windows*
  - `Xamarin.iOS` for iOS (*Checked*)
  - `portable-MonoAndroid+wpa81` for Android and Windows Store - *Checked for Android* 
- Move ManagedBass code to `Legacy` repository
- Merge into ManagedBass repository
- Abandon ManagedBass.PInvoke repository
- Upload packages
- Update Website
- Update Samples
- If something like `DllMap` may work, then separate library for iOS can be eliminated in most cases

### Website
- Add more valid parameters documentation. e.g. Supported Flags
- Add more examples ported from BASS documentation

### App Store Certification
- Windows Store (*Tested*)  
  Currently requires all AddOns libraries to be present for certification.
  Package splitting would improve the experience.
- Apple Store
- Google Play Store