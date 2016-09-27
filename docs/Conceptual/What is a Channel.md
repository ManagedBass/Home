# What is a Channel?
A "Channel" can be a sample playback channel (HCHANNEL), a sample stream (HSTREAM), a MOD music (HMUSIC), or a recording (HRECORD).
Each "Channel" function can be used with one or more of these channel types.

## The types of channel
Type     | Returned by
---------|--------------
HCHANNEL | `Bass.SampleGetChannel`
HSTREAM  | `Bass.CreateStream` and add-on provided functions
HMUSIC   | `Bass.MusicLoad`
HRECORD  | `Bass.RecordStart`

A sample stream (HSTREAM) or MOD music (HMUSIC) that has been created with the `BassFlags.Decode` flag is sometimes referred to as a "decoding channel".
