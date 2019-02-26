# Commands

- [Git](#git)
- [Dotnet Core](#dotnet)
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
dotnet test src/project/project.csproj -c Release
```

## Nuget

