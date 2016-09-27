# AddOns
AddOns add more functionality to BASS.

Tracked in [this](https://github.com/ManagedBass/ManagedBass.PInvoke/projects/2) project.

The following AddOns (excluding Plugins) are supported:
- BassAsio
- BassCd
- BassEnc
- BassFx
- BassMidi
- BassMix
- BassWasapi
- BassWinamp
- BassWma

# Plugins
A Plugin plugs into standard BASS functions like sample or stream creation to provide support for more audio formats.
BASS has built in support for various audio codecs like MPEG, OGG, WAV, AIFF, etc.
A Plugin is loaded using `Bass.PluginLoad` method and unloaded using `Bass.PluginFree`.

The following AddOns support the BASS Plugin system.
- BassAac
- BassAc3
- BassAdx
- BassAix
- BassAlac
- BassApe
- BassCd
- BassDsd
- BassFlac
- BassHls
- BassMidi
- BassMpc
- BassOfr
- BassOpus
- BassSpx
- BassTta
- BassWma
- BassWv

# BassEnc Plugins
The following Plugins add more encoding formats to BassEnc.
- BassEnc_Ogg
- BassEnc_Opus

# Currently not wrapped
Will only be wrapped if someone contributes
- Bass Tags
- Bass ZXTune
- Bass WADSP
- Bass VST
- Bass SFX
- Bass WA
- Bass DShow
- Bass XMMS