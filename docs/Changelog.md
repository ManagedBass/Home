# Changelog for ManagedBass.PInvoke

# v0.5.0
* AddOns restricted to platforms on which they are available.
* BassEnc_Opus and BassEnc_Ogg available on Android and iOS.
* Portable project restricted to Bass, BassFx, BassMix and BassMidi in favour of WindowsStore.

## v0.4.5
Fix some memory leaks in automatic reference holding.

## v0.4.3
Added support for `BassEnc_Ogg` and `BassEnc_Opus` AddOns.

## v0.4.2
Made `enum DataFlags` of `int` type.

## v0.4.1
Added `IEffectParameter` overloads for `Bass.FXGetParameters` and `Bass.FXSetParameters`.

## v0.4.0
* Fix typo: `BassFlags.MusicSensitiveRamping`.
* Added public constructors for `BassException`.
* BassCd Plugin system is windows only, since .cda files are Windows only.
* Updated `Bass.RecordStart` period overload documentation.
* Removed `Bass.PluginLoadDirectory` from Android.
* `Bass.IsSlidableAttribute` marked obsolete. See the online API documentation for knowing about Slidable attributes.

## v0.3.2
* Fixed typo: `AsioFuture.GetOutputMeter`.
* Correction: Airplay features moved to Mac version from iOS
* Added const `BassCd.TrackPregap`.
* Added `BassEnc.MimeMp3, MimeAac, MimeOgg` to be used with `BassEnc.CastInit`.

## v0.3.1
**BassMix**
* Added ChannelAttribute.MixerLatency.
* Updated BassMix.ChannelSetMatrix(int, float[,], float) documentation.

**BassEnc v2.4.13**
* Added EncodeServer.Meta.
* Added EncodeFlags.Dither, ConvertFloatAuto.
* Improved BassEnc.CastProxy.

**BassHls**
* Added SyncFlags.HlsSegment.
* Added TagType.HlsExtInf.
* Added FileStreamPosition.HlsSegment.

## v0.3.0
Completed XML Documentation!

* Added `BassMidi.StreamGetMark` overload returning `MidiMarker`.
* Modified the signature of `BassMidi.StreamGetMarks` overload returning `MidiMarker[]`.
* Added `Errors.CastDenied`, `AcmCancel`.
* Added `BassMidi.StreamEvents` `byte[]` overload with Channels parameter.
* Added `BassMidi.StreamGetFonts` overload returning `MidiFont[]`.
* Added `BassMidi.StreamGetFontsEx`.

## v0.2.1
Fixed the iOS Library!

* More Xml Documentation.
* `EncodeProcedureEx` is available only on iOS and Mac.
* Added `BassMidi.StreamEvent` overload taking High and Low parameters.
* Removed Obsolete members.
* FIX: `EncodeClientProcedure` - Changed Headers parameter to `IntPtr`.
* FIX: `WasapiInfo` - Changed MaxVolume, MinVolume and VolumeStep properties to `float`.

## v0.1.1
* More XML Documentation.
* Marked `BassEnc.CastSendMeta` obsolete and added other overloads.
* Marked `BassMidi.FontInit` obsolete and added overload without `BassFlags`.

## v0.1.0
Initial Release.