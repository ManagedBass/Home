# DX8 Effect Implementations
DX8 effects are otherwise known as DirectX Media Object (DMO) effects, and as the name suggests, requires DirectX 8 (or above) to be installed.
BASS provides 2 different implementations of DX8 effects, each with its advantages.
The method used by a channel depends on whether BassFlags.FX is used in its creation.

## With BassFlags.FX
This is the standard way of using DX8 effects.
The main advantage of this method is that effect parameter changes are audible instantaneously.
The main disadvantages are that the channel's sample rate cannot be changed (can with DX9), and it cannot be used with decoding channels or speaker assignment.

## Without BassFlags.FX
The advantages/disadvantages of this method are basically the opposite of the other method;
the channel's sample rate can be changed, but there's a delay in effect parameter changes being audible.
The reason being that, using this method, the effects are applied at the same stage as user DSP functions.
There are also other advantages to this method, as shown in the table below.

Task                  | With FX flag | Without FX flag  
----------------------|--------------|-----------------
Adding & removing     | Channel needs to be stopped when adding or removing an effect. | Can add and remove effects without stopping playback.  
Decoding channels     | Not possible. | Automatically used for decoding channels.  
Speaker assignment    | Not possible. | Can be used with speaker assignment.  
Recording             | Not possible. | Automatically used for recording channels.  
Parameter changes     | Audible instantaneously. | Delayed by the length of the channel's buffer; using a smaller buffer means less delay.  
Channel sample rate   | Can only be changed when using DirectX 9. | Can be changed.  
Effected sample data  | Not available. DSP functions, `Bass.ChannelGetData` and `Bass.ChannelGetLevel` receive the original data (without the effects applied). | The effected data is available to BASS functions.  
Effect chain ordering | Not possible. | The effects can be applied in any order you want, and can be intermingled with DSP functions.  
Channel buffer length | Must be at least 150ms. | No restriction.  
CPU usage             | CPU use is not included in `Bass.CPUUsage`. | CPU use is included in `Bass.CPUUsage`. Also slightly lower CPU usage.  

In both cases, DX8 effects are not supported on channels that are more than stereo, and floating-point support requires DirectX 9.

**Platform-specific**  
Away from Windows, the DX8 effects are emulated by BASS and the "With FX flag" system is unavailable.
Floating-point is supported (8.24 fixed-point on Android and Windows CE), and the PARAMEQ effect also supports more than stereo.
