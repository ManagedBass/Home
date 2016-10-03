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
- BassZXTune

# BassEnc Plugins
The following Plugins add more encoding formats to BassEnc.
- BassEnc_Ogg
- BassEnc_Opus

# Currently not wrapped
Will only be wrapped if someone contributes
- BassTags
- BassWADSP
- BassVST
- BassSFX
- BassWA
- BassDShow
- BassXMMS

# Platorm Availability
AddOn    | Windows | Linux | Mac | Android | iOS | WindowsStore
---------|---------|-------|-----|---------|-----|--------------
AAC      | X       | X     |     | X       |     |
AC3      | X       | X     | X   |         |     |
ADX      | X       |       |     |         |     |
AIX      | X       |       |     |         |     |
ALAC     | X       | X     |     | X       |     |
APE      | X       | X     | X   | X       | X   |
ASIO     | X       |       |     |         |     |
CD       | X       | X     |     |         |     |
DSD      | X       | X     | X   | X       | X   |
ENC      | X       | X     | X   | X       | X   |
ENC_OGG  | X       | X     | X   | X       | X   |
ENC_OPUS | X       | X     | X   | X       | X   |
FLAC     | X       | X     | X   | X       | X   |
FX       | X       | X     | X   | X       | X   | X
HLS      | X       | X     | X   | X       | X   |
MIDI     | X       | X     | X   | X       | X   | X
MIX      | X       | X     | X   | X       | X   | X
MPC      | X       | X     | X   | X       | X   |
OFR      | X       |       |     |         |     |
OPUS     | X       | X     | X   | X       | X   |
SPX      | X       | X     | X   |         |     |
TTA      | X       | X     | X   | X       | X   |
WASAPI   | X       |       |     |         |     |
WINAMP   | X       |       |     |         |     |
WMA      | X       |       |     |         |     |
WV       | X       | X     | X   | X       | X   |
ZXTune   | X       | X     | X   | X       |     |