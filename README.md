# Commands

- [Git](#git)
- [Dotnet Core](#dotnet-core)
- [Nuget](#nuget)

## Git

```bash
# find which branches contain a commit
git branch --contains <commit>
```

```bash
# revert last commit and keep modified files
git reset --soft HEAD^
```

## Dotnet Core

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

## Nuget

```bash
# packs a nuget from a nuspec with a certain version in release mode
nuget pack dist\project.nuspec -Version 0.0.1-alpha-SHA1 -Properties Configuration=Release -OutputDirectory .\dist\
```

```bash
# publish a nuget package using nuget
nuget push package.nupkg -Source http://nuget.rezult.io/v3/index.json
```
