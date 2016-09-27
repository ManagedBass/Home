# Getting Started - Xamarin.Android

1. Install the NuGet package

   ```powershell
   Install-Package ManagedBass.PInvoke
   ```

2. Download bass libraries for Android from [here](http://www.un4seen.com/forum/?topic=13225.0).

3. Include the bass libraries in your project for the architectures you want to support in respective folders: `lib\<Architecture>`.
   - armeabi - `lib\armebabi\libbass.so`
   - armeabi-v7a - `lib\armeabi-v7a\libbass.so`
   - x86 - `lib\x86\libbass.so`

4. Repeat the previous step for any addons you require.

5. Right Click the libraries and set:
   - `Copy to Output Directory` = **Always**  
   - `Build Action` = **AndroidNativeLibrary**

6. Set `Permissions` as per your requirement in the `AndroidManifest`, e.g. `RecordAudio`.