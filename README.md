# Shared - Reusable .NET Class Library

A reusable .NET class library packaged as a NuGet package and distributed through Azure Artifacts.

This project demonstrates how to develop, build, package, publish, and consume a shared library across multiple independent .NET projects using Azure DevOps Pipelines and Azure Artifacts.

## Project Overview

The main objective is to create a centralized reusable library that can be consumed by multiple applications without duplicating code.

### Key Features

- Reusable .NET Class Library
- NuGet package generation
- Automated build and packaging
- Package publishing to Azure Artifacts
- Package consumption across independent projects
- CI/CD automation using Azure DevOps Pipelines

## Technology Stack

- C#
- .NET 10
- Visual Studio 2026
- NuGet
- Azure DevOps Server
- Azure Artifacts
- Git

## Project Structure

```text
Shared/
│
├── src/
│   └── Shared/
│       ├── Class1.cs
│       └── Shared.csproj
│
├── Shared.slnx
├── .gitignore
└── README.md
```

## Workflow

1. Develop reusable functionality in the Shared library.
2. Build the project using .NET CLI.
3. Generate a NuGet package.
4. Publish the package to Azure Artifacts.
5. Configure other independent projects to access the package feed.
6. Install and use the Shared package through NuGet.

## Build the Project

```bash
dotnet restore
dotnet build
```

## Create a NuGet Package

```bash
dotnet pack -c Release
```

The generated `.nupkg` file will be available in the build output directory.

## Package Consumption

Other .NET projects can consume this library by adding a PackageReference to their project file:

```xml
<ItemGroup>
    <PackageReference Include="Shared" Version="1.0.0" />
</ItemGroup>
```

The package version should match the version published to the NuGet feed.

## CI/CD

Azure DevOps Pipelines are used to automate the following stages:

- Restore dependencies
- Build the library
- Package the library
- Publish the NuGet package to Azure Artifacts

## Learning Objectives

This project demonstrates practical experience with:

- Multi-project development
- NuGet package management
- Azure Artifacts
- CI/CD pipeline implementation
- Reusable software components
- Dependency management across independent repositories

---

**Note:** This is a personal learning and demonstration project using sample configurations and data.