# Wrapping BASS
> This documentation is an Early preview.

Let's get into some details of ManagedBass' approach in wrapping up Un4seen Bass and its AddOns.
A wrapper (like ManagedBass) is needed for using BASS and AddOns with .Net because they are written in unmanaged code (C/C++/Delphi).

---
## Garbage Collector (GC)
GC is an important feature of a managed environment including .Net which manages memory for a program.
It keeps track of references to objects and frees the allocated memory when the object is no longer referenced by any part of the program.
This ensures that there are no memory leaks and references are always valid.
It may also move objects to new location in memory to reduce fragmentation.
This feature is great for a programmer who has to work only with managed code, but when interoperating with unmanaged code this poses some problems which are discussed in follwing sections.

---

## Library
A single Bass library is wrapped by a `static` class.
All BASS functions are provided as static methods and Configurations are provided as static properties. 

`partial` class declaration is used to keep the code clean.

---
## Function
Platform Invoke Services (PInvoke) is used to call the functions in unmanaged BASS library.

`System.Runtime.InteropServices.DllImport` is applied on a method to be mapped with Bass.

The `EntryPoint` property allows simplifying the Method Names.
Redundant use of *BASS_XYZ_* in every function name is removed.

e.g. PInvoking `BASS_StreamFree` defined in bass.dll
```csharp
[DllImport(DllName, EntryPoint = "BASS_StreamFree")]
public static extern bool StreamFree(int Handle);
``` 

where every class contains a DllName const, (here `DllName = "bass"`).
Note that the file extension and lib prefix are not put.
These are automatically resolved by the runtime as:
- "bass.dll" on Windows
- "libbass.so" on Linux and Android
- "libbass.dylib" on Mac

`DllName = "__Internal"` is used for iOS.

---
## Strings as Method Parameters
ManagedBass uses Unicode for most strings wherever applicable to be consistent with .Net environment.

This is done by setting `CharSet` to `CharSet.Unicode` and passing `BassFlags.Unicode` flag in the Flags parameter.

e.g. PInvoking `BASS_StreamCreateFile` defined in bass.dll
```csharp
[DllImport(DllName, CharSet = CharSet.Unicode)]
static extern int BASS_StreamCreateFile(bool Memory, string File, long Offset, long Length, BassFlags Flags);

public static int CreateStream(string File, long Offset, long Length, BassFlags Flags)
{
    return BASS_StreamCreateFile(false, File, Offset, Length, Flags | BassFlags.Unicode);
}
```

## Strings as Method Return values or struct members
Declared as an `IntPtr` and one of `Marshal.PtrToStringAnsi`, `Marshal.PtrToStringUni` or `Extensions.PtrToStringUtf8` is used as appropriate to convert that to string. 

---
## Plugins
Plugins have their own Shared projects which are referenced by the platforms where they are supported.

---
## Structures
Unlike Bass.Net, ManagedBass uses structs instead of classes wherever possible to wrap native structures.

The structs are marked with `StructLayout` attribute with `LayoutKind.Sequential`.

Most members are exposed as Properties instead of directly as fields.

---
## Constants
Constants are represented by enums.

The enums containing Constants used as flags are marked with `Flags` attribute.

---
## Callbacks
Callbacks are marshalled as Delegates.

Some functions hold reference to `Delegates`/`FileProcedures` automatically and free them when the Stream is freed.
This eliminates the error common with Bass.Net arising because you forget to hold a reference to a delegate and it is Garbage Collected.
This feature is supported by the following functions:
- All `CreateStream` functions
- `Bass.ChannelSetDSP`
- `Bass.ChannelSetSync`
- `Bass.RecordStart`