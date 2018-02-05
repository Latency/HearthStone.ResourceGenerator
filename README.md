# HearthStone.ResourceGenerator

---

## Task-based Asynchronous Pattern ([TAP])

|              |                      |
|--------------|----------------------|
| CREATED BY:  | [Latency McLaughlin] |
| UPDATED:     | 2/1/2018 |
| FRAMEWORK:   | [.NET]Framework 4.5 - 4.7.1, [.NET]Standard2.0, [.NET]CoreApp2.0 ([Latest](https://www.microsoft.com/net/download/windows)) |
| LANGUAGE:    | [C#] (v7.0) |
| OUTPUT TYPE: | [Console Application] + [API] |
| SUPPORTS:    | [Visual Studio] 2017, 2015, 2013, 2012, 2010, 2008 |
| TAGS:        | [.NET], [NuGet], [MyGet], [API], [C#], [NUnit], [Visual Studio] |
| STATUS:      | [![hearthstone MyGet Build Status](https://www.myget.org/BuildSource/Badge/hearthstone?identifier=9e22fb46-e5c4-4542-aa85-fae0cb369bba)](https://www.myget.org/) |
| LICENSE:     | [![License](https://img.shields.io/badge/HearthStone-License-yellowgreen.svg?style=plastic)](https://github.com/Latency/HearthStone.ResourceGenerator/blob/master/LICENSE) |
| CHAT:        | [![Chat](https://img.shields.io/badge/gitter-join%20chat-lightgrey.svg?style=plastic)](https://gitter.im/HearthSim/Hearthstone-Deck-Tracker?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) |
| VERSION:     | [![Download](https://img.shields.io/myget/hearthstone/v/HearthStone.ResourceGenerator.svg?style=plastic)](https://www.myget.org/F/hearthstone/api/v2/package/HearthStone.ResourceGenerator/2.0.0-rc) |

### Screenshot

<p align="center">
 <img src="https://github.com/Latency/HearthStone.ResourceGenerator/blob/master/Output.png?raw=true" alt="Output">
</p>

<hr>

## Navigation
* <a href="#introduction">Introduction</a>
* <a href="#overview">Overview</a>
* <a href="#installation">Installation</a>

<hr>

<h2><a name="introduction">Introduction</a></h2>

This article introduces an [API] which generates artifacts asynchronously; supporting deadlock protection, timeout, cancellation requests, and checkpointing.

[ResourceGenerator] is compiled as a library packaged for the [MyGet] marketplace.  The project itself, supplies an application driver, and test suite, and source code.

---

This API has several benefits, such as:

-- *[ResourceGenerator] benefits.*
* Supports centralized versioning.
* Reusable code.
* Decrease download time.
* Optomizes performance of asynchronous code.
* Packaged in NuGet format.
* Reduce boilerplate installation and batch file code.

<h2><a name="overview">Overview</a></h2>

* <b>Async / Await support.</b><br>
 Downloads for artifact images via web request calls run in parallel based on card set.  Upon collection of the entire set, post-image processing is performed and images are bundled into resource files.  Each image is rescaled and fixed for 130x34 8bpp PNG which is a compresssed format replacement to Bitmap which is not supported in .NET Core.

* <b>Cancellation Checkpointing</b><br>
 Threading is handled by [TPL] and is wrapped by [ORM-Monitor] which handles the scheduling and asynchronous event dispatch.

<h2><a name="installation">Installation</a></h2>

This library is to be installed from [MyGet]:

There are plug-ins that this project uses as dependency from [NuGet] that are built-in and linked into the [API].

### Usage:
```csharp
ResourceGenerator.exe <path> <folder> <IsOverwriten> [msbuild]
```

### Example #1
```csharp
ResourceGenerator.exe "$(SolutionDir)Resources" Tiles 0
```

| #  |         Argument             |   Type  |                                       Description                                                        |
|----|------------------------------|---------|----------------------------------------------------------------------------------------------------------|
| 1. | Path                         | String  | Target directory to generate the resource in.                                                            |
| 2. | Folder                       | String  | Folder name that is created underneat the root directory <Path>.                                         |
| 3. | IsOverwriten                 | Boolean | Forces downloading external images via async web request calls.                                          |
| 4. | (optional)<br>**DO_NOT_USE** | String  | ["msbuild"] which is used for bootstrap post-build rules only.                                           |

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job.)

   [.NET]: <https://en.wikipedia.org/wiki/.NET_Framework/>
   [Console Application]: <https://en.wikipedia.org/wiki/Console_application>
   [API]: <https://en.wikipedia.org/wiki/Application_programming_interface>
   [C#]: <https://en.wikipedia.org/wiki/C_Sharp_(programming_language)>
   [DLL]: <https://en.wikipedia.org/wiki/Dynamic-link_library>
   [Latency McLaughlin]: <https://www.linkedin.com/in/Latency/>
   [MIT License]: <http://choosealicense.com/licenses/mit/>
   [MyGet]: <https://www.myget.org/features>
   [NuGet]: <https://www.nuget.org/>
   [NUnit]: <https://en.wikipedia.org/wiki/NUnit>
   [ORM-Monitor]: <https://github.com/Latency/ORM-Monitor/>
   [ResourceGenerator]: <https://github.com/Latency/HearthStone.ResourceGenerator/>
   [TAP]: <https://msdn.microsoft.com/en-us/library/hh873175(v=vs.110).aspx>
   [TPL]: <https://msdn.microsoft.com/en-us/library/dd460717(v=vs.110).aspx>
   [Visual Studio]: <https://en.wikipedia.org/wiki/Microsoft_Visual_Studio/>