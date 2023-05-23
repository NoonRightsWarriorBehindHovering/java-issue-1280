To run the example:

```sh
# First setup environment that a browser is installed (Could be done manually too)
mvn -e compile exec:java -Dexec.mainClass=org.example.ExampleReproducible
# Remove FFMPEG (if installed)
rm -rf ~/.cache/ms-playwright/ffmpeg-1008/
# Run without install step
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
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- resources:3.3.0:resources (default-resources) @ examples ---
[INFO] skip non existing resourceDirectory /workspaces/java-issue-1280/src/main/resources
[INFO] 
[INFO] --- compiler:3.1:compile (default-compile) @ examples ---
[INFO] Nothing to compile - all classes are up to date
[INFO] 
[INFO] --- exec:3.1.0:java (default-cli) @ examples ---
Skipping browsers download because `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD` env variable is set
/tmp/playwright-java-12653187037731474849/package/lib/server/chromium/crPage.js:378
      this._firstNonInitialNavigationCommittedReject(new Error('Page closed'));
                                                     ^

Error: Page closed
    at CRSession.<anonymous> (/tmp/playwright-java-12653187037731474849/package/lib/server/chromium/crPage.js:378:54)
    at Object.onceWrapper (node:events:627:28)
    at CRSession.emit (node:events:525:35)
    at /tmp/playwright-java-12653187037731474849/package/lib/server/chromium/crConnection.js:211:39

Node.js v18.16.0
[WARNING] 
com.microsoft.playwright.PlaywrightException: Failed to read message from driver, pipe closed.
    at com.microsoft.playwright.impl.PipeTransport.poll (PipeTransport.java:75)
    at com.microsoft.playwright.impl.Connection.processOneMessage (Connection.java:200)
    at com.microsoft.playwright.impl.ChannelOwner.runUntil (ChannelOwner.java:109)
    at com.microsoft.playwright.impl.Connection.sendMessage (Connection.java:126)
    at com.microsoft.playwright.impl.ChannelOwner.sendMessage (ChannelOwner.java:102)
    at com.microsoft.playwright.impl.ChannelOwner.sendMessage (ChannelOwner.java:98)
    at com.microsoft.playwright.impl.BrowserImpl.closeImpl (BrowserImpl.java:84)
    at com.microsoft.playwright.impl.BrowserImpl.lambda$close$0 (BrowserImpl.java:71)
    at com.microsoft.playwright.impl.LoggingSupport.lambda$withLogging$0 (LoggingSupport.java:36)
    at com.microsoft.playwright.impl.LoggingSupport.withLogging (LoggingSupport.java:47)
    at com.microsoft.playwright.impl.ChannelOwner.withLogging (ChannelOwner.java:87)
    at com.microsoft.playwright.impl.LoggingSupport.withLogging (LoggingSupport.java:35)
    at com.microsoft.playwright.impl.BrowserImpl.close (BrowserImpl.java:71)
    at org.example.ExampleReproducible.main (ExampleReproducible.java:34)
    at org.codehaus.mojo.exec.ExecJavaMojo$1.run (ExecJavaMojo.java:279)
    at java.lang.Thread.run (Thread.java:829)
Caused by: java.io.EOFException
    at com.microsoft.playwright.impl.ReaderThread.readIntLE (PipeTransport.java:110)
    at com.microsoft.playwright.impl.ReaderThread.readMessage (PipeTransport.java:139)
    at com.microsoft.playwright.impl.ReaderThread.run (PipeTransport.java:125)
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.694 s
[INFO] Finished at: 2023-05-23T08:03:12Z
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.codehaus.mojo:exec-maven-plugin:3.1.0:java (default-cli) on project examples: An exception occurred while executing the Java class. Failed to read message from driver, pipe closed.: EOFException -> [Help 1]
org.apache.maven.lifecycle.LifecycleExecutionException: Failed to execute goal org.codehaus.mojo:exec-maven-plugin:3.1.0:java (default-cli) on project examples: An exception occurred while executing the Java class. Failed to read message from driver, pipe closed.
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2 (MojoExecutor.java:347)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute (MojoExecutor.java:330)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:213)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:175)
    at org.apache.maven.lifecycle.internal.MojoExecutor.access$000 (MojoExecutor.java:76)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run (MojoExecutor.java:163)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute (DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:160)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:105)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:73)
    at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build (SingleThreadedBuilder.java:53)
    at org.apache.maven.lifecycle.internal.LifecycleStarter.execute (LifecycleStarter.java:118)
    at org.apache.maven.DefaultMaven.doExecute (DefaultMaven.java:261)
    at org.apache.maven.DefaultMaven.doExecute (DefaultMaven.java:173)
    at org.apache.maven.DefaultMaven.execute (DefaultMaven.java:101)
    at org.apache.maven.cli.MavenCli.execute (MavenCli.java:827)
    at org.apache.maven.cli.MavenCli.doMain (MavenCli.java:272)
    at org.apache.maven.cli.MavenCli.main (MavenCli.java:195)
    at jdk.internal.reflect.NativeMethodAccessorImpl.invoke0 (Native Method)
    at jdk.internal.reflect.NativeMethodAccessorImpl.invoke (NativeMethodAccessorImpl.java:62)
    at jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke (DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke (Method.java:566)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced (Launcher.java:282)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launch (Launcher.java:225)
    at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode (Launcher.java:406)
    at org.codehaus.plexus.classworlds.launcher.Launcher.main (Launcher.java:347)
Caused by: org.apache.maven.plugin.MojoExecutionException: An exception occurred while executing the Java class. Failed to read message from driver, pipe closed.
    at org.codehaus.mojo.exec.ExecJavaMojo.execute (ExecJavaMojo.java:349)
    at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo (DefaultBuildPluginManager.java:126)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2 (MojoExecutor.java:342)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute (MojoExecutor.java:330)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:213)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:175)
    at org.apache.maven.lifecycle.internal.MojoExecutor.access$000 (MojoExecutor.java:76)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run (MojoExecutor.java:163)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute (DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:160)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:105)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:73)
    at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build (SingleThreadedBuilder.java:53)
    at org.apache.maven.lifecycle.internal.LifecycleStarter.execute (LifecycleStarter.java:118)
    at org.apache.maven.DefaultMaven.doExecute (DefaultMaven.java:261)
    at org.apache.maven.DefaultMaven.doExecute (DefaultMaven.java:173)
    at org.apache.maven.DefaultMaven.execute (DefaultMaven.java:101)
    at org.apache.maven.cli.MavenCli.execute (MavenCli.java:827)
    at org.apache.maven.cli.MavenCli.doMain (MavenCli.java:272)
    at org.apache.maven.cli.MavenCli.main (MavenCli.java:195)
    at jdk.internal.reflect.NativeMethodAccessorImpl.invoke0 (Native Method)
    at jdk.internal.reflect.NativeMethodAccessorImpl.invoke (NativeMethodAccessorImpl.java:62)
    at jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke (DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke (Method.java:566)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced (Launcher.java:282)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launch (Launcher.java:225)
    at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode (Launcher.java:406)
    at org.codehaus.plexus.classworlds.launcher.Launcher.main (Launcher.java:347)
Caused by: com.microsoft.playwright.PlaywrightException: Failed to read message from driver, pipe closed.
    at com.microsoft.playwright.impl.PipeTransport.poll (PipeTransport.java:75)
    at com.microsoft.playwright.impl.Connection.processOneMessage (Connection.java:200)
    at com.microsoft.playwright.impl.ChannelOwner.runUntil (ChannelOwner.java:109)
    at com.microsoft.playwright.impl.Connection.sendMessage (Connection.java:126)
    at com.microsoft.playwright.impl.ChannelOwner.sendMessage (ChannelOwner.java:102)
    at com.microsoft.playwright.impl.ChannelOwner.sendMessage (ChannelOwner.java:98)
    at com.microsoft.playwright.impl.BrowserImpl.closeImpl (BrowserImpl.java:84)
    at com.microsoft.playwright.impl.BrowserImpl.lambda$close$0 (BrowserImpl.java:71)
    at com.microsoft.playwright.impl.LoggingSupport.lambda$withLogging$0 (LoggingSupport.java:36)
    at com.microsoft.playwright.impl.LoggingSupport.withLogging (LoggingSupport.java:47)
    at com.microsoft.playwright.impl.ChannelOwner.withLogging (ChannelOwner.java:87)
    at com.microsoft.playwright.impl.LoggingSupport.withLogging (LoggingSupport.java:35)
    at com.microsoft.playwright.impl.BrowserImpl.close (BrowserImpl.java:71)
    at org.example.ExampleReproducible.main (ExampleReproducible.java:34)
    at org.codehaus.mojo.exec.ExecJavaMojo$1.run (ExecJavaMojo.java:279)
    at java.lang.Thread.run (Thread.java:829)
Caused by: java.io.EOFException
    at com.microsoft.playwright.impl.ReaderThread.readIntLE (PipeTransport.java:110)
    at com.microsoft.playwright.impl.ReaderThread.readMessage (PipeTransport.java:139)
    at com.microsoft.playwright.impl.ReaderThread.run (PipeTransport.java:125)
[ERROR] 
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
```

</details>
