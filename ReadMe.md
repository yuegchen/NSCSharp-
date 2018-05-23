To compile, you have to do 

"mcs NSCorrected.cs NSUtilities.cs 

mcs NSBob.cs NSUtilities.cs 

mcs NSAlice.cs NSUtilities.cs 

mcs NSServer.cs NSUtilities.cs"

In NSUtilities.cs, there are abstractions we used for cryptographic operations.
In NSAlice.cs, NSServer.cs and NSBob.cs, I wrote each role using udpclient.
In NSCorrected.cs, I created three sperate processes to run the three roles.

I record the cpu time before and after running the protocol in a loop. The difference of the cpu time before  divides the number of iterations is the CPU time of a single execution of the protocol.

This program sometimes run into concurrency bugs when it runs for a loop like 1000 iterations. I could't figure out the reasons or solve it. I tried to replace my encryption and decryption methods to methods I found on Internet and post my problem on stackoverflow, but those didn't really solve the problem. 

I followed this udpclient post on stakeoverflow: https://stackoverflow.com/questions/20038943/simple-udp-example-to-send-and-receive-data-from-same-socket and I used send() abstraction from https://docs.microsoft.com/en-us/dotnet/framework/network-programming/asynchronous-client-socket-example.

I used some of the abstractions from Microsoft but didn't use the whole thing. Because I wrote all the stuff in udpclient, it will require too much effort to use the whole structure and the MS sample code is just a simple callback Server-Client, I wonder it is difficult to adopt it to a complicate protocol like this.

To test and run the code, type "mono NSCorrected.exe" on the console. You can change the number of iterations in the NSUtilities.cs, but you have to recompile before running again.