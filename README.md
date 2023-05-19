To run the example:

```sh
PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 mvn -e compile exec:java -Dexec.mainClass=org.example.ExampleReproducible
```

<details>
<summary>
The output
</summary>

```
$ PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 mvn -e compile exec:java -Dexec.mainClass=org.example.ExampleReproducible
[INFO] Error stacktraces are turned on.
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------< org.example:examples >------------------------
[INFO] Building Playwright Client Examples 1.34.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ examples ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/yurys/sandbox/java-issue-1280/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ examples ---
[INFO] Nothing to compile - all classes are up to date
[INFO] 
[INFO] --- exec-maven-plugin:3.1.0:java (default-cli) @ examples ---
Skipping browsers download because `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD` env variable is set
/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/chromium/crPage.js:378
      this._firstNonInitialNavigationCommittedReject(new Error('Page closed'));
                                                     ^

Error: Page closed
    at CRSession.<anonymous> (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/chromium/crPage.js:378:54)
    at Object.onceWrapper (node:events:627:28)
    at CRSession.emit (node:events:525:35)
    at /private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/chromium/crConnection.js:211:39

Node.js v18.16.0
[WARNING] 
com.microsoft.playwright.PlaywrightException: Error {
  message='Executable doesn't exist at /Users/yurys/Library/Caches/ms-playwright/ffmpeg-1008/ffmpeg-mac
╔════════════════════════════════════════════════════════════════════════════════════════════╗
║ Looks like Playwright was just installed or updated.                                       ║
║ Please run the following command to download new browsers:                                 ║
║                                                                                            ║
║     mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="install" ║
║                                                                                            ║
║ <3 Playwright Team                                                                         ║
╚════════════════════════════════════════════════════════════════════════════════════════════╝
  name='Error
  stack='Error: Executable doesn't exist at /Users/yurys/Library/Caches/ms-playwright/ffmpeg-1008/ffmpeg-mac
╔════════════════════════════════════════════════════════════════════════════════════════════╗
║ Looks like Playwright was just installed or updated.                                       ║
║ Please run the following command to download new browsers:                                 ║
║                                                                                            ║
║     mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="install" ║
║                                                                                            ║
║ <3 Playwright Team                                                                         ║
╚════════════════════════════════════════════════════════════════════════════════════════════╝
    at executablePathOrDie (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/registry/index.js:305:15)
    at Object.executablePathOrDie (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/registry/index.js:481:43)
    at FrameSession._createVideoRecorder (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/chromium/crPage.js:793:68)
    at FrameSession._initialize (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/chromium/crPage.js:410:18)
    at async CRBrowserContext.newPage (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/browserContext.js:356:25)
    at async BrowserContextDispatcher.newPage (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/dispatchers/browserContextDispatcher.js:182:55)
    at async DispatcherConnection.dispatch (/private/var/folders/t3/_mbh6z155sz1cr7prkpn9lsh0000gn/T/playwright-java-4904821401431033217/package/lib/server/dispatchers/dispatcher.js:312:22)
}
    at com.microsoft.playwright.impl.WaitableResult.get (WaitableResult.java:54)
    at com.microsoft.playwright.impl.ChannelOwner.runUntil (ChannelOwner.java:111)
    at com.microsoft.playwright.impl.Connection.sendMessage (Connection.java:126)
    at com.microsoft.playwright.impl.ChannelOwner.sendMessage (ChannelOwner.java:102)
    at com.microsoft.playwright.impl.ChannelOwner.sendMessage (ChannelOwner.java:98)
    at com.microsoft.playwright.impl.BrowserContextImpl.newPageImpl (BrowserContextImpl.java:351)
    at com.microsoft.playwright.impl.BrowserContextImpl.lambda$newPage$13 (BrowserContextImpl.java:344)
    at com.microsoft.playwright.impl.LoggingSupport.withLogging (LoggingSupport.java:47)
    at com.microsoft.playwright.impl.ChannelOwner.withLogging (ChannelOwner.java:87)
    at com.microsoft.playwright.impl.BrowserContextImpl.newPage (BrowserContextImpl.java:344)
    at com.microsoft.playwright.impl.BrowserContextImpl.newPage (BrowserContextImpl.java:44)
    at org.example.ExampleReproducible.main (ExampleReproducible.java:29)
    at org.codehaus.mojo.exec.ExecJavaMojo$1.run (ExecJavaMojo.java:279)
    at java.lang.Thread.run (Thread.java:1623)

```

</details>
