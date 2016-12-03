# Getting Started - Windows Store

1. Install the NuGet package

   ```powershell
   Install-Package ManagedBass.PInvoke
   ```

2. Download bass libraries for Windows Store from [here](http://www.un4seen.com/forum/?topic=16665.0).

3. Include the bass libraries in your project for the architectures you want to support in respective folders: `Assets\libs\<Architecture>`.
   - arm - `Assets\libs\arm\bass.dll`
   - x64 - `Assets\libs\x64\bass.dll`
   - x86 - `Assets\libs\x86\bass.dll`

4. Edit the project (`.csproj`) file.
   Add the following section to it:
```xml
<ItemGroup Condition="'$(Platform)' == 'x86'">
    <Content Include="Assets\libs\x86\bass.dll">
        <Link>bass.dll</Link> <!--VERY IMPORTANT-->
        <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
</ItemGroup>
<ItemGroup Condition="'$(Platform)' == 'x64'">
    <Content Include="Assets\libs\x64\bass.dll">
        <Link>bass.dll</Link>
        <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
</ItemGroup>
<ItemGroup Condition="'$(Platform)' == 'ARM'">
    <Content Include="Assets\libs\ARM\bass.dll">
        <Link>bass.dll</Link>
        <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </Content>
</ItemGroup>
```
5. Repeat the steps 3 and 4 for any addons you require.
