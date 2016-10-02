# HelloBASS
A simple console application for playing an Mp3.

```csharp
using System;
using ManagedBass;

namespace HelloBASS
{
    class Program
    {
        static void Main(string[] args)
        {
            // Init BASS using the default output device
            if (Bass.Init())
            {
                // Create a stream from a file
                var stream = Bass.CreateStream("FILE.mp3");
                
                if (stream != 0)
                    Bass.ChannelPlay(stream); // Play the stream

                // Error creating the stream
                else Console.WriteLine("Error: {0}!", Bass.LastError);

                // Wait till user presses a key
                Console.WriteLine("Press any key to exit");
                Console.ReadKey();

                // Free the stream
                Bass.StreamFree(stream);

                // Free current device.
                Bass.Free();
            }
            else Console.WriteLine("BASS could not be initialized!");
        }
    }
}
```