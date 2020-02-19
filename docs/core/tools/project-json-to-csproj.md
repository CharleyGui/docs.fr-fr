---
title: Comparaison entre project.json et csproj
description: Consultez le mappage entre éléments project.json et csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: abe515007b47b415ac33e3350a29edced1784d68
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451103"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mappage entre propriétés project.json et csproj

Par [Nate McMaster](https://github.com/natemcmaster)

Pendant le développement des outils .NET Core, une modification de conception importante a été effectuée pour ne plus prendre en charge les fichiers *project.json* et passer les projets .NET Core au format MSBuild/csproj à la place.

Cet article explique comment les paramètres dans *project.json* sont représentés au format MSBuild/csproj. De cette façon, vous découvrez comment utiliser le nouveau format ainsi que les modifications apportées par les outils de migration quand vous mettez à niveau votre projet vers la dernière version des outils.

## <a name="the-csproj-format"></a>Format csproj

Le nouveau format, \*.csproj, est un format basé sur XML. L’exemple suivant montre le nœud racine d’un projet .NET Core utilisant le `Microsoft.NET.Sdk`. Pour les projets web, le SDK utilisé est `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Propriétés communes de niveau supérieur

### <a name="name"></a>name

```json
{
  "name": "MyProjectName"
}
```

N'est plus pris en charge. Dans csproj, cette propriété est déterminée par le nom du fichier projet, qui correspond généralement au nom du répertoire. Par exemple : `MyProjectName.csproj`.

Par défaut, le nom de fichier du projet spécifie également la valeur des propriétés `<AssemblyName>` et `<PackageId>`.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>` a une valeur différente de `<PackageId>` si la propriété `buildOptions\outputName` est définie dans project.json.
Pour plus d’informations, consultez [Autres options communes de génération](#other-common-build-options).

### <a name="version"></a>version

```json
{
  "version": "1.0.0-alpha-*"
}
```

Utilisez les propriétés `VersionPrefix` et `VersionSuffix` :

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

Vous pouvez également utiliser la propriété `Version`, mais elle peut remplacer les paramètres de version pendant l’empaquetage :

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Autres options communes de niveau racine

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a>frameworks

### <a name="one-target-framework"></a>Un framework cible

```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a>Plusieurs frameworks cibles

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Utilisez la propriété `TargetFrameworks` pour définir votre liste de frameworks cibles. Utilisez un point-virgule pour séparer plusieurs valeurs de framework.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>dependencies

> [!IMPORTANT]
> Si la dépendance est un **projet** et non un package, le format est différent.
> Pour plus d'informations, consultez la section [type de dépendance](#dependency-type).

### <a name="netstandardlibrary-metapackage"></a>Métapackage NETStandard.Library

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a>Métapackage Microsoft.NETCore.App

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

Notez que la valeur de `<RuntimeFrameworkVersion>` dans le projet migré est déterminée par la version du SDK que vous avez installée.

### <a name="top-level-dependencies"></a>Dépendances de niveau supérieur

```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a>Dépendances par framework

```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a>importations

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a>type de dépendance

#### <a name="type-project"></a>type : project

```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> Ce type brise la façon dont `dotnet pack --version-suffix $suffix` détermine la version de la dépendance d’une référence de projet.

#### <a name="type-build"></a>type : build

```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a>type : platform

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

Il n’existe aucun équivalent dans csproj.

## <a name="runtimes"></a>runtimes

```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a>Applications autonomes (déploiement autonome)

Dans project.json, la définition d’une section `runtimes` signifie que l’application était autonome pendant la génération et la publication.
Dans MSBuild, tous les projets sont *portables* pendant la génération, mais peuvent être publiés de façon autonome.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Pour plus d’informations, consultez [Déploiements autonomes](../deploying/index.md#publish-self-contained).

## <a name="tools"></a>outils

```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> La section `imports` n’est pas prise en charge dans csproj. Les outils qui nécessitent des importations ne fonctionnent pas avec le nouveau `Microsoft.NET.Sdk`.

## <a name="buildoptions"></a>buildOptions

Voir aussi [Fichiers](#files).

### <a name="emitentrypoint"></a>emitEntryPoint

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Si `emitEntryPoint` est `false`, la valeur de `OutputType` est convertie en `Library`, ce qui est la valeur par défaut :

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a>keyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

L’élément `keyFile` se développe en trois propriétés dans MSBuild :

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a>Autres options communes de génération

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a>packOptions

Voir aussi [Fichiers](#files).

### <a name="common-pack-options"></a>Options communes de pack

```json
{
  "packOptions": {
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

Il n’existe aucun équivalent de l’élément `owners` dans MSBuild.
Pour `summary`, vous pouvez utiliser la propriété MSBuild `<Description>`, même si la valeur de `summary` n’est pas migrée automatiquement vers cette propriété, étant donné que cette propriété est mappée à l’élément [`description`](#other-common-root-level-options).

## <a name="scripts"></a>Scripts

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Leur équivalent dans MSBuild sont les [cibles](/visualstudio/msbuild/msbuild-targets) :

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a>runtimeOptions

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

Tous les paramètres de ce groupe, sauf la propriété « System.GC.Server », sont placés dans un fichier appelé *runtimeconfig.template.json* dans le dossier du projet, avec les options élevées à l’objet racine pendant le processus de migration :

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

La propriété « System.GC.Server » est migrée dans le fichier csproj :

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Toutefois, vous pouvez définir toutes ces valeurs dans le csproj ainsi que les propriétés MSBuild :

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a>shared

```json
{
  "shared": "shared/**/*.cs"
}
```

Non pris en charge dans csproj. Vous devez inclure à la place des fichiers de contenu dans votre fichier *.nuspec*.
Pour plus d’informations, consultez [Inclusion de fichiers de contenu](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>files

Dans *project.json*, la build et le pack peuvent être étendus pour effectuer la compilation et l’incorporation à partir de dossiers différents.
Dans MSBuild, cela s’effectue à l’aide d’[éléments](/visualstudio/msbuild/common-msbuild-project-items). L’exemple suivant illustre une conversion courante :

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> Plusieurs [modèles d’utilisation des caractères génériques (globbing)](https://en.wikipedia.org/wiki/Glob_(programming)) par défaut sont ajoutés automatiquement par le SDK .NET Core.
> Pour plus d’informations, consultez [Valeurs des éléments de compilation par défaut](https://aka.ms/sdkimplicititems).

Tous les éléments MSBuild `ItemGroup` prennent en charge `Include`, `Exclude` et `Remove`.

La disposition du package à l’intérieur du fichier .nupkg peut être modifiée avec `PackagePath="path"`.

À l’exception de `Content`, la plupart des groupes d’éléments impliquent explicitement l’ajout de `Pack="true"` dans le package. `Content` est placé dans le dossier *content* dans un package, car la propriété MSBuild `<IncludeContentInPack>` est définie sur `true` par défaut.
Pour plus d’informations, consultez [Inclusion de contenu dans un package](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"` est une méthode rapide pour définir un chemin de package sur le chemin du fichier relatif au projet.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xUnit

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a>MSTest

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble générale des modifications de l’interface CLI](../tools/cli-msbuild-architecture.md)
