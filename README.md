# Commands

- [Git](#git)
- [.NET Core](#net-core)
- [NuGet](#nuget)
- [Visual Studio](#visual-studio)

## Git

```bash
# find which branches contain a commit
git branch --contains <commit>
```

```bash
# revert last commit and keep modified files
git reset --soft HEAD^
```

```bash
# cherry-pick command will allows you to pick any commit from any branch and apply it to any other branch.
git cherry-pick <commit-hash>
```

## .NET Core

```bash
# test a certain project in release mode
dotnet test src\project\project.csproj -c Release
```

```bash
# publish a project into a certain dist folder with certain version, in release mode
dotnet publish src\project -c Release -o ..\dist\ /p:Version=0.0.1
```

```bash
# publish an exe with a single file
dotnet publish src\project -c Release -o ..\dist\ /p:Version=0.0.1 /p:PublishSingleFile=true /p:PublishTrimmed=true /p:PublishReadyToRun=true
```

```bash
# publish a nuget package using dotnet nuget
dotnet nuget push -s http://your.nuget.com/v3/index.json package.version.nupkg -k key
```

```bash
# build a project assembly into a specific folder with a certain version
# useful if you set the project properties to generate a nuget package
dotnet build .\src\Company.Product.Project\ -c Release -o ..\..\dist\ /p:Version=$version
```

```bash
# copy content from csproj
  <ItemGroup>
    <Content Include="**\*.json;**\*.js;" Exclude="bin\**\*;obj\**\*" CopyToOutputDirectory="PreserveNewest" />
  </ItemGroup>
```

```bash
# default configuration for Web App
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <IsPackable>false</IsPackable>
    <LangVersion>latest</LangVersion>
    <IncludeSymbolsInSingleFile>true</IncludeSymbolsInSingleFile>
  </PropertyGroup>
```

## NuGet

```bash
# packs a nuget from a nuspec with a certain version in release mode
nuget pack dist\project.nuspec -Version 0.0.1-alpha-SHA1 -Properties Configuration=Release -OutputDirectory .\dist\
```

```bash
# publish a nuget package using nuget
nuget push package.nupkg -Source http://nuget.rezult.io/v3/index.json
```

```bash
# delete a specific NuGet package version from a source
nuget delete Package.Name 1.2.3 -ApiKey ApiKeyGoesHere -Source http://nuget.rezult.io  
```

## Visual Studio

```bash
# path for template class files
# for professional edition
C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE\ItemTemplates\CSharp\Code\1033\Class\Class.cs

## for community edition
C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\ItemTemplates\CSharp\Code\1033\Class\Class.cs
```

```csharp
// Class.cs template
#region Copyright
//-------------------------------------------------------------------------------------
// <copyright file="$safeitemrootname$.cs">
//     Copyright (c) $year$ $registeredorganization$. All rights reserved.
//     Originally created by $username$ at $time$ in $machinename$.
// </copyright>
//-------------------------------------------------------------------------------------
#endregion Copyright

using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace $rootnamespace$
{
    public class $safeitemrootname$
    {
        public $safeitemrootname$()
        {
        }
    }
}
```