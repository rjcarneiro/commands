# Commands

- [Git](#git)
- [.NET Core](#net-core)
- [NuGet](#nuget)
- [Visual Studio](#visual-studio)
- [Serilog](#serilog)
- [Windows Terminal](#windows-terminal)

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
# build a projcet with a specific version in release mode
dotnet build src\project\project.csproj -c Release /p:Version=0.0.1
```

```bash
# test a certain project in release mode
dotnet test src\project\project.csproj -c Release
```

```bash
# publish a project into a certain dist folder with certain version, in release mode
dotnet publish src\project.csproj -c Release -o .\dist\ /p:Version=0.0.1
```

```bash
# publish a project using as self contained
dotnet publish ./src/My.csproj /p:Configuration=Release -r win-x64 --self-contained true -o ./dist/ /p:Version=0.0.1
```

```bash
# publish an exe with a single file
dotnet publish src\project.csproj -c Release -o .\dist\ /p:Version=0.0.1 /p:PublishSingleFile=true /p:PublishTrimmed=true /p:PublishReadyToRun=true
```

```bash
# publish a nuget package using dotnet nuget
dotnet nuget push -s http://your.nuget.com/v3/index.json package.version.nupkg -k key
```

```bash
# build a project assembly into a specific folder with a certain version
# useful if you set the project properties to generate a nuget package
dotnet build .\src\Company.Product.Project\ -c Release -o .\dist\ /p:Version=$version
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

```bash
# include AspNetCore framework into class projects
<ItemGroup>
  <FrameworkReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
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
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace $rootnamespace$;

public class $safeitemrootname$
{
    public $safeitemrootname$()
    {
    }
}
```

## Serilog

```bash
# file logging templates for applications
[{Timestamp:HH:mm:ss}/{Level:u3}/{SourceContext}] {Message:lj}{NewLine}{Exception}

# file logging templates for web apps
[{Timestamp:HH:mm:ss}/{Level:u3}/{SourceContext}/{ActionId}/{RequestId}/{ActionName}] {Message:lj}{NewLine}{Exception}
```

## Windows Terminal

```bash
# command to set up powershell profile using Visual Studio Code
code $PROFILE
```

```bash
# my default profile using oh-my-posh
Import-Module -Name Terminal-Icons
Import-Module posh-git

$MyFavoriteThemes = @("wholespace", "unicorn", "thecyberden", "takuya")
$MyFavoriteTheme = $MyFavoriteThemes | Get-Random

oh-my-posh --init --shell pwsh --config $env:POSH_THEMES_PATH/$MyFavoriteTheme.omp.json | Invoke-Expression
#& ([ScriptBlock]::Create((oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\$MyFavoriteTheme.omp.json" --print) -join "`n"))

Enable-PoshTooltips
Set-Location D:\Projects
```
