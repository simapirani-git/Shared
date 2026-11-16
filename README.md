# Shared - Reusable .NET Class Library

## Introduction

Shared is a reusable .NET class library designed to provide centralized shared components for multiple independent .NET applications.

This project demonstrates how to develop, build, test, package, and distribute a reusable library as a NuGet package using Azure DevOps Artifacts.

The package is consumed by independent application repositories, helping reduce code duplication and simplify dependency management.

## Project Architecture

This project is part of a Multi-Repository architecture consisting of four independent repositories:

| Repository | Description |
|---|---|
| Shared | Reusable .NET class library distributed as a NuGet package |
| Basket | ASP.NET Core Web API |
| Identity | ASP.NET Core Web API |
| Order | ASP.NET Core Web API |

Each repository maintains its own solution, project structure, source code, and Git history.

## Technologies Used

- C#
- .NET 10
- .NET Class Library
- MSTest
- NuGet Package Management
- Azure DevOps Artifacts
- Azure DevOps Classic Pipelines
- Git and GitHub

## Repository Structure

```text
Shared/
│
├── src/
│   ├── Shared/
│   │   ├── Shared.csproj
│   │   └── Class1.cs
│   │
│   └── Shared.Tests/
│       ├── Shared.Tests.csproj
│       ├── MSTestSettings.cs
│       └── Test1.cs
│
├── .gitignore
├── NuGet.Config
├── README.md
└── Shared.slnx
```

## Build and Test

Restore dependencies:

```bash
dotnet restore Shared.slnx
```

Build the solution:

```bash
dotnet build Shared.slnx --no-restore
```

Run unit tests:

```bash
dotnet test Shared.slnx --no-build
```

Create a NuGet package:

```bash
dotnet pack Shared.slnx -c Release
```

## NuGet Package Distribution

The Shared library is packaged and published to Azure DevOps Artifacts.

**Package information:**

- Package name: `Shared`
- Package type: NuGet
- Azure Artifacts feed: `Shared-Feed`
- Example package version: `1.0.0`

Other repositories consume the package through a PackageReference:

```xml
<PackageReference Include="Shared" Version="1.0.0" />
```

Feed authentication and package source configuration are managed separately through NuGet configuration and Azure DevOps service connections.

## CI/CD Pipeline

The project uses an Azure DevOps Classic Pipeline to automate the package lifecycle.

Pipeline workflow:

1. NuGet Restore
2. Build
3. Test
4. Pack
5. Push NuGet Package
6. Publish Build Artifact

This process helps ensure that the shared library is built, tested, and packaged before distribution.

## Learning Objectives

This project demonstrates practical experience with:

- Multi-repository development
- Reusable software components
- NuGet package creation and distribution
- Azure DevOps Artifacts
- Classic CI/CD pipeline implementation
- Unit testing with MSTest
- Dependency management across independent repositories
- Git version control and GitHub repository management

---

**Note:** This is a personal learning and demonstration project using sample configurations and data.
