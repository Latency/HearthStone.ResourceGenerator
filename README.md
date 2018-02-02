# ResourceGenerator

### HearthStone Artifact Resource Generator

---

## Task-based Asynchronous Pattern ([TAP])

* CREATED BY: &nbsp;&nbsp;&nbsp;&nbsp;[Latency McLaughlin]
* FRAMEWORK: &nbsp;&nbsp;[.NET] v4.5 - v4.7.1, Standard 2.0, & Core v[[2.0]](https://www.microsoft.com/net/download/windows)
* LANGUAGE: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[C#] (v7.0)
* GFX SUBSYS: &nbsp;&nbsp;&nbsp;&nbsp;[Console]
* STATUS: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[![hearthstone MyGet Build Status](https://www.myget.org/BuildSource/Badge/hearthstone?identifier=1f42bc57-a3a3-47ed-8ea2-ad8287333101)](https://www.myget.org/)
* SUPPORTS: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Visual Studio] 2017, 2015, 2013, 2012, 2010, 2008
* UPDATED: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2/1/2018
* VERSION: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.0.0](https://www.nuget.org/packages/ResourceGenerator/2.0.0/)
* TAGS: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[.NET], [NuGet], [MyGet], [API], [C#], [NUnit], [Visual Studio]

### Screenshot

<p align="center">
 <img src="https://github.com/Latency/ResourceGenerator/blob/master//Output.png?raw=true" alt="Output">
</p>

<hr>

## Navigation
* <a href="#introduction">Introduction</a>
* <a href="#overview">Overview</a>
* <a href="#installation">Installation</a>
* <a href="#other">Other Features</a>
* <a href="#references">References</a>
* <a href="#license">License</a>

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
Usage:  ResourceGenerator.exe <path> <folder> <IsOverwriten> [msbuild]
```

### Example #1
```csharp
ResourceGenerator.exe "$(SolutionDir)Resources" Tiles 0
```

path &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= Target directory to generate the resource in.<br>
folder &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= Folder name that is created underneat the root directory <Path>.<br>
IsOverwriten = Boolean value [0 or 1] which forces or bypasses downloading external images via async web request calls.<br>
msbuild &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= String value (optional) ["msbuild"] which is used for bootstrap post-build rules only.  **DO NOT USE**<br>

<h2><a name="other">Other Features</a></h2>

- Unit Tests:<br>
  The unit test uses [NUnit] to help qualify the underlying [API].   Included is a sample that can be ran and tested againsted a variety of mock senario conditions.

<h2><a name="references">References</a></h2>

 [.NET], [NuGet], [API], [C#], [NUnit], [Visual Studio]

<h2><a name="license">License</a></h2>

[MIT License]


[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job.)

   [.NET]: <https://en.wikipedia.org/wiki/.NET_Framework/>
   [API]: <https://en.wikipedia.org/wiki/Application_programming_interface>
   [C#]: <https://en.wikipedia.org/wiki/C_Sharp_(programming_language)>
   [DLL]: <https://en.wikipedia.org/wiki/Dynamic-link_library>
   [Latency McLaughlin]: <https://www.linkedin.com/in/Latency/>
   [MIT License]: <http://choosealicense.com/licenses/mit/>
   [MyGet]: <https://www.myget.org/features>
   [NuGet]: <https://www.nuget.org/>
   [NUnit]: <https://en.wikipedia.org/wiki/NUnit>
   [ORM-Monitor]: <https://github.com/Latency/ORM-Monitor/>
   [ResourceGenerator]: <https://github.com/Latency/ResourceGenerator/>
   [TAP]: <https://msdn.microsoft.com/en-us/library/hh873175(v=vs.110).aspx>
   [TPL]: <https://msdn.microsoft.com/en-us/library/dd460717(v=vs.110).aspx>
   [Visual Studio]: <https://en.wikipedia.org/wiki/Microsoft_Visual_Studio/>