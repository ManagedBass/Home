# Migrating from Bass.Net

This post is targeted for those migrating from Bass.Net to ManagedBass.

Licensing
----------------------------------------------------------------------------------
Bass.Net needs to be licensed for commercial/non-commercial use and a Registration Key needs to be applied to suppress popups.

No such headaches with ManagedBass. It's free to use and open-sourced under the MIT License.

> Bass and AddOns still need to be licensed.

Methods
---------------------------------------------------------------------------------
Redundant use of *BASS_XYZ_* in every function name is removed.

e.g. `Bass.BASS_StreamFree` in Bass.Net is named as `Bass.StreamFree`.

and `BassWasapi.BASS_WASAPI_Init` in Bass.Net is named as `BassWasapi.Init`.

For some particular cases like the example below **Polymorphism** is used to simplify code.

e.g. `Bass.BASS_StreamCreate()`, `Bass.BASS_StreamCreateFile()`, `Bass.BASS_StreamCreateFileUser()`, `Bass.BASS_StreamCreateURL()` in Bass.Net are named as `Bass.CreateStream()`.

Structures
---------------------------------------------------------------------------------
ManagedBass uses structs (with `[StructLayout(LayoutKind.Sequential)]` attribute) instead of classes for BASS structures because they are easy to Marshal.

Distribution
---------------------------------------------------------------------------------
ManagedBass is distributed on NuGet.
Alternatively, since its Open-Source you could build it yourself.

There are separate NuGet packages for every AddOn based on .Net Standard 1.4.

Configurations
---------------------------------------------------------------------------------
Bass.Net uses *Bass.Get/SetConfig* methods while ManagedBass also provides static **Properties** on respective classes.

Delegates
---------------------------------------------------------------------------------
An instance of a callback delegate passed to a BASS function in Bass.Net needs to be manually referenced to prevent it from being Garbage-Collected.

This also applies in most cases to ManagedBass.

But, for some scenarios like `CreateStream` methods, `Bass.ChannelSetDSP` and `Bass.ChannelSetSync`, the delegates are automatically held alive by ManagedBass for your convenience.

Effects
---------------------------------------------------------------------------------
Effects are implemented as classes with full functionality encapsulated. You can use them without touching the BASS functions.

Alternatively, if you want to do that manually the effect functions are available in the Bass class and the marshalling classes are named as *EFFECTNAME*Parameters.