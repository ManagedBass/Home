# Floating-point Channels
Channels can be made to use 32-bit floating-point sample data.
When a channel uses floating-point sample data, BASS takes full advantage of the extra resolution when generating the decoded sample data; it does not simply convert 16-bit data to floating-point.

The main advantage of floating-point channels, aside from the increased resolution/quality, is that they are not clipped until output.
This makes them particularly good for DSP/FX, because the quality is not degraded as the data passes through a chain of DSP/FX.
So even if the output device is not capable of outputting the channel in its full quality, the quality is still improved.

Floating-point sample data ranges from -1 to +1, but as mentioned above, it is not clipped to this range until output, so it is possible that `DSPProcedure` callback functions or `Bass.ChannelGetData` calls could receive data outside of this range.

When a floating-point channel is played, it is converted to whatever resolution the output device supports in the final mix.

**Platform-specific**  
Floating-point channels are not supported when using VxD drivers (on Windows 98/95), except for "decoding channels".
Windows Vista (and later) audio is natively floating-point, so for optimum performance (not to mention quality), BASS channels should also be floating-point.
That particularly applies to formats that are decoded in floating-point anyway, ie. lossy formats like MP3 and OGG.
It also applies to Linux and OSX, where BASS's mix format is floating-point.

Floating-point channels are not supported on Android or Windows CE. That includes "decoding channels".


**Example**  
Check for 32-bit floating-point channel support.

```csharp
int floatable; // floating-point channel support?

// try creating a floating-point stream
floatable = Bass.CreateStream(44100, 1, BassFlags.Float) != 0;

// floating-point channels are supported! (free the test stream)
if (floatable)
    Bass.StreamFree(floatable);
```
