# About BassFx Algorithms
BassFx provides three seemingly independent effects: tempo, pitch and sample rate control.
These three controls are implemented as combination of two primary effects, sample rate transposing and time-stretching.

Sample rate transposing affects both the audio stream duration and pitch.
It's implemented simply by converting the original audio sample stream to the desired duration by interpolating from the original audio samples.
In BassFx, linear interpolation with anti-alias filtering is used.
Theoretically a higher-order interpolation provide better result than 1st order linear interpolation, but in audio application linear interpolation together with anti-alias filtering performs subjectively about as well as higher-order filtering would.

Time-stretching means changing the audio stream duration without affecting it's pitch.
BassFx uses WSOLA-like time-stretching routines that operate in the time domain.
Compared to sample rate transposing, time-stretching is a much heavier operation and also requires a longer processing "window" of sound samples used by the processing algorithm, thus increasing the algorithm input/output latency.
Typical i/o latency for the BassFx time-stretch algorithm is around 100 ms.

Sample rate transposing and time-stretching are then used together to produce the tempo, pitch and rate controls:
- **Tempo** control is implemented purely by time-stretching. 
- **Rate** control is implemented purely by sample rate transposing. 
- **Pitch** control is implemented as a combination of time-stretching and sample rate transposing.
  For example, to increase pitch the audio stream is first time-stretched to longer duration (without affecting pitch) and then transposed back to original duration by sample rate transposing, which simultaneously reduces duration and increases pitch.
  The result is original duration but increased pitch. 

BassFx uses [SoundTouch](http://www.surina.net/soundtouch/) library for its tempo/pitch processing.