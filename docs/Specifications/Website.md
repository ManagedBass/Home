# Website
The website hosted on GitHub pages provides API documentation for Windows version of [ManagedBass][MB] and [ManagedBass.PInvoke][MB.PInvoke].

The website is generated using [DocFX][DocFX] which augments markdown files into the API documentation.
This allows to add examples, supported flags etc. in the website while keeping the source code clean.

The data to build the website is hosted on [ManagedBass.DocFX][MB.DocFX] repository.
This website is hosted on GitHub pages repository: [ManagedBass.GitHub.io][MB.Page], but nothing is pushed manually into that.

## Build Process
An AppVeyor script is used to update the website: [ManagedBass.GitHub.io][MB.Site] on every push to the [ManagedBass.DocFX][MB.DocFX] repository.

1. Source code is pushed to [ManagedBass.DocFX][MB.DocFX] (**NOT to [ManagedBass.GitHub.io][MB.Page]**)
2. AppVeyor build is triggered by webhooks
   - [DocFX][DocFX] is downloaded.
   - [ManagedBass][MB], [ManagedBass.PInvoke][MB.PInvoke] and [ManagedBass.GitHub.io][MB.Page] repositories are cloned.
   - docfx.exe is extracted and run.
   - Content in [ManagedBass.GitHub.io][MB.Page] is replaced by that from generated _site folder.
   - Changes are commited and pushed to [ManagedBass.GitHub.io][MB.Page].
3. Site gets published on GitHub pages.

The process roughly takes 5mins.

## DocFX Template
The default template seemed inadequate, so it was customized as neccessary.

## JS Frameworks
- jQuery
- Bootstrap
- Highlight.js
- Lunr.js

[MB]: https://github.com/ManagedBass/ManagedBass
[MB.PInvoke]: https://github.com/ManagedBass/ManagedBass.PInvoke
[MB.DocFX]: https://github.com/ManagedBass/ManagedBass.DocFX
[MB.Page]: https://github.com/ManagedBass/ManagedBass.GitHub.io
[MB.Site]: https://ManagedBass.GitHub.io
[DocFX]: http://dotnet.github.io/docfx