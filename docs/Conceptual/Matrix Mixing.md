# Matrix Mixing
Normally when mixing channels, the source channels are sent to the output in the same order;
the left input is sent to the left output, and so on.
Sometimes something a bit more complex than that is required.
For example, if the source has more channels than the output, you may want to "downmix" the source so that all channels are present in the output.
Equally, if the source has fewer channels than the output, you may want to "upmix" it so that all output channels have sound.
Or you may just want to rearrange the channels.
Matrix mixing allows all of these.

A matrix mixer is created on a per-source basis (you can mix'n'match normal and matrix mixing), by using the `BassFlags.MixerMatrix` and/or `BassFlags.MixerDownMix` flag when calling `BassMix.MixerAddChannel`.
The matrix itself is a 2-dimensional array of floating-point mixing levels, with the source channels on one axis, and the output channels on the other.
Some simple examples are shown below.

When using matrix mixing, the source channel's volume attribute still has effect, but the pan attribute does not.
Whenever necessary, panning changes can be achieved by modifying the matrix.

## Example
In = stereo, Out = stereo.
```csharp
float[,] matrix =
{
    {1, 0}, // left out = left in
    {0, 1} // right out = right in
};

BassMix.ChannelSetMatrix(handle, matrix); // apply the matrix
```

In = stereo, Out = swapped stereo.
```csharp
float[,] matrix =
{
    {0, 1}, // left out = right in
    {1, 0} // right out = left in
};

BassMix.ChannelSetMatrix(handle, matrix); // apply the matrix
```

In = stereo, Out = mono.
```csharp
float[,] matrix =
{
    {0.5, 0.5} // mono out = half left + right in
};

BassMix.ChannelSetMatrix(handle, matrix); // apply the matrix
```

In = stereo, Out = quadraphonic (4 channels).
```csharp
float[,] matrix =
{
    {1, 0}, // left front out = left in
    {0, 1}, // right front out = right in
    {1, 0}, // left rear out = left in
    {0, 1} // right rear out = right in
};

BassMix.ChannelSetMatrix(handle, matrix); // apply the matrix
```
