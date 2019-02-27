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
dotnet publish src\project -c Release -o ..\..\dist\ /p:Version=0.0.1
```

## Nuget

```bash
# packs a nuget from a nuspec with a certain version in release mode
- nuget pack dist\project.nuspec -Version 0.0.1-alpha-SHA1 -Properties Configuration=Release -OutputDirectory .\dist\
```