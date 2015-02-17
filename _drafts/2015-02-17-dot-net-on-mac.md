---
layout: post
title: .Net on Mac
description: |
  ?
---

## Installing Homebrew

[Homebrew](http://brew.sh/)

```ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"```

```brew doctor```

```brew update```

## Intalling Mono

[Mono](http://www.mono-project.com/)

Ensure you have Mono development tools 3.0 or later installed:

```brew install mono```

Ensure your mono instance has root SSL certificates:

```mozroots --import --sync```

Output:

```
Mozilla Roots Importer - version 3.12.0.0
Download and import trusted root certificates from Mozilla's MXR.
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD licensed.

Downloading from 'http://mxr.mozilla.org/seamonkey/source/security/nss/lib/ckfw/builtins/certdata.txt?raw=1'...
Importing certificates into user store...
140 new root certificates were added to your trust store.
Import process completed.
```

## Building ScriptCs

[ScriptCs](https://github.com/scriptcs/scriptcs)

```git clone https://github.com/scriptcs/scriptcs.git```

```cd scriptcs/```

Execute the build script:

```./build.sh```

Output:

```
grimlock:scriptcs tnt$ ./build.sh
+ mozroots --import --sync --quiet
+ mono ./.nuget/NuGet.exe restore ./ScriptCs.sln
Installing 'xunit.runners 1.9.2'.
Successfully installed 'xunit.runners 1.9.2'.
Installing 'PowerArgs 2.0.5'.
Installing 'Newtonsoft.Json 6.0.3'.
Installing 'StyleCop.MSBuild 4.7.49.0'.
Installing 'AutoFixture 3.18.8'.
Installing 'Common.Logging 2.1.2'.
Installing 'AutoFixture.AutoMoq 3.18.8'.
Installing 'AutoFixture.Xunit 3.18.8'.
Installing 'Moq 4.2.1402.2112'.
Installing 'Should 1.1.20'.
Installing 'xunit.extensions 1.9.2'.
Installing 'xunit 1.9.2'.
Installing 'Microsoft.Web.Xdt 2.1.0'.
Installing 'LiteGuard.Source 0.8.0'.
Installing 'Roslyn.Compilers.Common 1.2.20906.2'.
Installing 'Roslyn.Compilers.CSharp 1.2.20906.2'.
Installing 'Nuget.Core 2.8.2'.
Installing 'Autofac 3.3.1'.
Installing 'Autofac.Mef 3.0.3'.
Installing 'ICSharpCode.NRefactory 5.3.0'.
Installing 'Mono.Cecil 0.9.5.4'.
Installing 'Mono.CSharp 3.6.1'.
Installing 'Xbehave 1.1.0'.
Successfully installed 'PowerArgs 2.0.5'.
Successfully installed 'Newtonsoft.Json 6.0.3'.
Successfully installed 'AutoFixture 3.18.8'.
Successfully installed 'Common.Logging 2.1.2'.
Successfully installed 'StyleCop.MSBuild 4.7.49.0'.
Successfully installed 'AutoFixture.Xunit 3.18.8'.
Successfully installed 'AutoFixture.AutoMoq 3.18.8'.
Successfully installed 'Should 1.1.20'.
Successfully installed 'xunit.extensions 1.9.2'.
Successfully installed 'xunit 1.9.2'.
Successfully installed 'Moq 4.2.1402.2112'.
Successfully installed 'Microsoft.Web.Xdt 2.1.0'.
Successfully installed 'LiteGuard.Source 0.8.0'.
Successfully installed 'Roslyn.Compilers.Common 1.2.20906.2'.
Successfully installed 'Autofac 3.3.1'.
Successfully installed 'Nuget.Core 2.8.2'.
Successfully installed 'Roslyn.Compilers.CSharp 1.2.20906.2'.
Successfully installed 'Autofac.Mef 3.0.3'.
Successfully installed 'Mono.CSharp 3.6.1'.
Successfully installed 'ICSharpCode.NRefactory 5.3.0'.
Successfully installed 'Xbehave 1.1.0'.
Successfully installed 'Mono.Cecil 0.9.5.4'.
+ mkdir -p artifacts
+ xbuild ./ScriptCs.sln /property:Configuration=Release /nologo /verbosity:normal

Build started 17/02/2015 8:49:12 PM.
__________________________________________________
Project "/Users/tnt/Development/scriptcs/ScriptCs.sln" (default target(s)):

... SNIP ...

Done building project "/Users/tnt/Development/scriptcs/ScriptCs.sln".

Build succeeded.
	 0 Warning(s)
	 0 Error(s)

Time Elapsed 00:00:04.2530550
+ mono ./packages/xunit.runners.1.9.2/tools/xunit.console.clr4.exe test/ScriptCs.Tests.Acceptance/bin/Release/ScriptCs.Tests.Acceptance.dll /xml artifacts/ScriptCs.Tests.Acceptance.dll.TestResult.xml /html artifacts/ScriptCs.Tests.Acceptance.dll.TestResult.html
xUnit.net console test runner (64-bit .NET 4.0.30319.17020)
Copyright (C) 2013 Outercurve Foundation.

xunit.dll:     Version 1.9.2.1705
Test assembly: /Users/tnt/Development/scriptcs/test/ScriptCs.Tests.Acceptance/bin/Release/ScriptCs.Tests.Acceptance.dll

46 total, 0 failed, 0 skipped, took 17.106 seconds
```

## Testing ScriptCs

```cd src/ScriptCs/bin/Release/```

```mono scriptcs.exe```





## Coda

**I really hope** you find this blog post useful.
It might seem at first that there is a lot to do to get your blog set up with Jekyll,
but it's worth it as the end product is very transparent and easy to hack on.

Feel free to drop me a
[line](mailto:tod@todthomson.com)
or a
[tweet](https://twitter.com/todthomson)
if you have any feedback, suggestions or if anything doesn't work for you as described.
I'm more than happy to help.

Until next time.... _[Make Mine Jekyll](http://en.wikipedia.org/wiki/Comic_book_letter_column)!_