# Distribution
ManagedBass is distributed as a NuGet package.
Also, being open-source you can build it yourself (requires Visual Studio 2015 with Xamarin).
The Linux part needs to be built manually in any case since there is no NuGet support for Linux as of June 2016.

The following platforms are supported:
- Windows (.Net)
- Linux (Mono/.Net Core)
- Mac (Mono/Xamarin.Mac/.Net Core)
- Android (Xamarin.Android)
- iOS (Xamarin.iOS)
- UWP (.Net Core)

The iOS part has been fixed to work fine from v0.2.1.

Also, there is a Portable Class Library which could target all the above platforms (except iOS).
> NOTE: Some issues have been reported with .Net Native.

[Bait and Switch](http://log.paulbetts.org/the-bait-and-switch-pcl-trick/) PCL trick is employed through the NuGet package.

The native BASS libraries are NOT included and need to be downloaded separately as per platform and processor architecture from http://un4seen.com.  
Place the native BASS libraries in the project output directory.