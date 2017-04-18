# Getting Started - Xamarin.iOS
> This page is in the process of being written. Information here may be inaccurate or inadequate.

1. Install the NuGet package

   ```powershell
   Install-Package ManagedBass
   ```

2. Download bass libraries for iOS from [here](http://www.un4seen.com/forum/?topic=10910.0) and place in project directory.

3. Add libbass.a as **Native Reference**.

4. In the project Options, under **iOS Build**, set:
  - `Link Behaviour` = **Link All**
  - `Additional mtouch arguments` to:
```
-gcc_flags "-L$(ProjectDir) -lbass -framework CFNetwork -framework AudioToolbox -framework SystemConfiguration -framework Accelerate -force_load $(ProjectDir)/libbass.a"
```
  - The mtouch arguments may need to be set for every configuration.


5. Repeat the previous step for any addons you require.
  - Add **CoreMIDI** framework when using BassMidi.
  - The Additional mtouch arguments should also include `-lstdc++` when using BassFx or BassApe.

6. If you supply callback functions, make it `static` and apply `MonoPInvokeCallback` on them.

```csharp
using ObjCRuntime;

Bass.ChannelSetDSP(Channel, Proc);

// static method required by Xamarin.iOS
[MonoPInvokeCallback(typeof(DSPProcedure))]
static void Proc(int Handle, int Channel, IntPtr Buffer, int Length, IntPtr User)
{
    // Do Processing
}
```

> [Here](https://github.com/ManagedBass/Xamarin.iOS.Player) is a very simple example of an iOS audio player app using ManagedBass.
  Thanks to Brian Pieslak.
