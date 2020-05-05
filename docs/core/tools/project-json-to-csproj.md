---
title: Comparaison entre project.json et csproj
description: Consultez le mappage entre éléments project.json et csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: feaa7e9cde7e1aa4dfe94d699b14a018fc728f27
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794622"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="b9396-103">Mappage entre propriétés project.json et csproj</span><span class="sxs-lookup"><span data-stu-id="b9396-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="b9396-104">Par [Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="b9396-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="b9396-105">Pendant le développement des outils .NET Core, une modification de conception importante a été effectuée pour ne plus prendre en charge les fichiers *project.json* et passer les projets .NET Core au format MSBuild/csproj à la place.</span><span class="sxs-lookup"><span data-stu-id="b9396-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="b9396-106">Cet article explique comment les paramètres dans *project.json* sont représentés au format MSBuild/csproj. De cette façon, vous découvrez comment utiliser le nouveau format ainsi que les modifications apportées par les outils de migration quand vous mettez à niveau votre projet vers la dernière version des outils.</span><span class="sxs-lookup"><span data-stu-id="b9396-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="b9396-107">Format csproj</span><span class="sxs-lookup"><span data-stu-id="b9396-107">The csproj format</span></span>

<span data-ttu-id="b9396-108">Le nouveau format, \*.csproj, est un format basé sur XML.</span><span class="sxs-lookup"><span data-stu-id="b9396-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="b9396-109">L’exemple suivant montre le nœud racine d’un projet .NET Core utilisant le `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="b9396-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="b9396-110">Pour les projets web, le SDK utilisé est `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="b9396-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="b9396-111">Propriétés communes de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="b9396-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="b9396-112">name</span><span class="sxs-lookup"><span data-stu-id="b9396-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="b9396-113">N'est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b9396-113">No longer supported.</span></span> <span data-ttu-id="b9396-114">Dans csproj, cette propriété est déterminée par le nom du fichier projet, qui correspond généralement au nom du répertoire.</span><span class="sxs-lookup"><span data-stu-id="b9396-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="b9396-115">Par exemple, `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="b9396-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="b9396-116">Par défaut, le nom de fichier du projet spécifie également la valeur des propriétés `<AssemblyName>` et `<PackageId>`.</span><span class="sxs-lookup"><span data-stu-id="b9396-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="b9396-117">`<AssemblyName>` a une valeur différente de `<PackageId>` si la propriété `buildOptions\outputName` est définie dans project.json.</span><span class="sxs-lookup"><span data-stu-id="b9396-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="b9396-118">Pour plus d’informations, consultez [Autres options communes de génération](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="b9396-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="b9396-119">version</span><span class="sxs-lookup"><span data-stu-id="b9396-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="b9396-120">Utilisez les propriétés `VersionPrefix` et `VersionSuffix` :</span><span class="sxs-lookup"><span data-stu-id="b9396-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="b9396-121">Vous pouvez également utiliser la propriété `Version`, mais elle peut remplacer les paramètres de version pendant l’empaquetage :</span><span class="sxs-lookup"><span data-stu-id="b9396-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="b9396-122">Autres options communes de niveau racine</span><span class="sxs-lookup"><span data-stu-id="b9396-122">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="b9396-123">frameworks</span><span class="sxs-lookup"><span data-stu-id="b9396-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="b9396-124">Un framework cible</span><span class="sxs-lookup"><span data-stu-id="b9396-124">One target framework</span></span>

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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="b9396-125">Plusieurs frameworks cibles</span><span class="sxs-lookup"><span data-stu-id="b9396-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="b9396-126">Utilisez la propriété `TargetFrameworks` pour définir votre liste de frameworks cibles.</span><span class="sxs-lookup"><span data-stu-id="b9396-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="b9396-127">Utilisez un point-virgule pour séparer plusieurs valeurs de framework.</span><span class="sxs-lookup"><span data-stu-id="b9396-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="b9396-128">dependencies</span><span class="sxs-lookup"><span data-stu-id="b9396-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9396-129">Si la dépendance est un **projet** et non un package, le format est différent.</span><span class="sxs-lookup"><span data-stu-id="b9396-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="b9396-130">Pour plus d'informations, consultez la section [type de dépendance](#dependency-type).</span><span class="sxs-lookup"><span data-stu-id="b9396-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="b9396-131">Métapackage NETStandard.Library</span><span class="sxs-lookup"><span data-stu-id="b9396-131">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="b9396-132">Métapackage Microsoft.NETCore.App</span><span class="sxs-lookup"><span data-stu-id="b9396-132">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="b9396-133">Notez que la valeur de `<RuntimeFrameworkVersion>` dans le projet migré est déterminée par la version du SDK que vous avez installée.</span><span class="sxs-lookup"><span data-stu-id="b9396-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="b9396-134">Dépendances de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="b9396-134">Top-level dependencies</span></span>

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

### <a name="per-framework-dependencies"></a><span data-ttu-id="b9396-135">Dépendances par framework</span><span class="sxs-lookup"><span data-stu-id="b9396-135">Per-framework dependencies</span></span>

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

### <a name="imports"></a><span data-ttu-id="b9396-136">importations</span><span class="sxs-lookup"><span data-stu-id="b9396-136">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="b9396-137">type de dépendance</span><span class="sxs-lookup"><span data-stu-id="b9396-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="b9396-138">type : project</span><span class="sxs-lookup"><span data-stu-id="b9396-138">type: project</span></span>

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
> <span data-ttu-id="b9396-139">Ce type brise la façon dont `dotnet pack --version-suffix $suffix` détermine la version de la dépendance d’une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="b9396-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="b9396-140">type : build</span><span class="sxs-lookup"><span data-stu-id="b9396-140">type: build</span></span>

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

#### <a name="type-platform"></a><span data-ttu-id="b9396-141">type : platform</span><span class="sxs-lookup"><span data-stu-id="b9396-141">type: platform</span></span>

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

<span data-ttu-id="b9396-142">Il n’existe aucun équivalent dans csproj.</span><span class="sxs-lookup"><span data-stu-id="b9396-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="b9396-143">runtimes</span><span class="sxs-lookup"><span data-stu-id="b9396-143">runtimes</span></span>

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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="b9396-144">Applications autonomes (déploiement autonome)</span><span class="sxs-lookup"><span data-stu-id="b9396-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="b9396-145">Dans project.json, la définition d’une section `runtimes` signifie que l’application était autonome pendant la génération et la publication.</span><span class="sxs-lookup"><span data-stu-id="b9396-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="b9396-146">Dans MSBuild, tous les projets sont *portables* pendant la génération, mais peuvent être publiés de façon autonome.</span><span class="sxs-lookup"><span data-stu-id="b9396-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="b9396-147">Pour plus d’informations, consultez [Déploiements autonomes](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="b9396-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="b9396-148">outils</span><span class="sxs-lookup"><span data-stu-id="b9396-148">tools</span></span>

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
> <span data-ttu-id="b9396-149">La section `imports` n’est pas prise en charge dans csproj.</span><span class="sxs-lookup"><span data-stu-id="b9396-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="b9396-150">Les outils qui nécessitent des importations ne fonctionnent pas avec le nouveau `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="b9396-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="b9396-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="b9396-151">buildOptions</span></span>

<span data-ttu-id="b9396-152">Voir aussi [Fichiers](#files).</span><span class="sxs-lookup"><span data-stu-id="b9396-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="b9396-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="b9396-153">emitEntryPoint</span></span>

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

<span data-ttu-id="b9396-154">Si `emitEntryPoint` est `false`, la valeur de `OutputType` est convertie en `Library`, ce qui est la valeur par défaut :</span><span class="sxs-lookup"><span data-stu-id="b9396-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="b9396-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="b9396-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="b9396-156">L’élément `keyFile` se développe en trois propriétés dans MSBuild :</span><span class="sxs-lookup"><span data-stu-id="b9396-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="b9396-157">Autres options communes de génération</span><span class="sxs-lookup"><span data-stu-id="b9396-157">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="b9396-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="b9396-158">packOptions</span></span>

<span data-ttu-id="b9396-159">Voir aussi [Fichiers](#files).</span><span class="sxs-lookup"><span data-stu-id="b9396-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="b9396-160">Options communes de pack</span><span class="sxs-lookup"><span data-stu-id="b9396-160">Common pack options</span></span>

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

<span data-ttu-id="b9396-161">Il n’existe aucun équivalent de l’élément `owners` dans MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b9396-161">There is no equivalent for the `owners` element in MSBuild.</span></span>
<span data-ttu-id="b9396-162">Pour `summary`, vous pouvez utiliser la propriété `<Description>` MSBuild, même si la valeur de `summary` n’est pas migrée automatiquement vers cette propriété, car cette propriété est mappée à [`description`](#other-common-root-level-options) l’élément.</span><span class="sxs-lookup"><span data-stu-id="b9396-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="b9396-163">Scripts</span><span class="sxs-lookup"><span data-stu-id="b9396-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="b9396-164">Leur équivalent dans MSBuild sont les [cibles](/visualstudio/msbuild/msbuild-targets) :</span><span class="sxs-lookup"><span data-stu-id="b9396-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="b9396-165">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="b9396-165">runtimeOptions</span></span>

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

<span data-ttu-id="b9396-166">Tous les paramètres de ce groupe, sauf la propriété « System.GC.Server », sont placés dans un fichier appelé *runtimeconfig.template.json* dans le dossier du projet, avec les options élevées à l’objet racine pendant le processus de migration :</span><span class="sxs-lookup"><span data-stu-id="b9396-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="b9396-167">La propriété « System.GC.Server » est migrée dans le fichier csproj :</span><span class="sxs-lookup"><span data-stu-id="b9396-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="b9396-168">Toutefois, vous pouvez définir toutes ces valeurs dans le csproj ainsi que les propriétés MSBuild :</span><span class="sxs-lookup"><span data-stu-id="b9396-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="b9396-169">partagés</span><span class="sxs-lookup"><span data-stu-id="b9396-169">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="b9396-170">Non pris en charge dans csproj.</span><span class="sxs-lookup"><span data-stu-id="b9396-170">Not supported in csproj.</span></span> <span data-ttu-id="b9396-171">Vous devez inclure à la place des fichiers de contenu dans votre fichier *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="b9396-171">You must instead create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="b9396-172">Pour plus d’informations, consultez [Inclusion de fichiers de contenu](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="b9396-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="b9396-173">files</span><span class="sxs-lookup"><span data-stu-id="b9396-173">files</span></span>

<span data-ttu-id="b9396-174">Dans *project.json*, la build et le pack peuvent être étendus pour effectuer la compilation et l’incorporation à partir de dossiers différents.</span><span class="sxs-lookup"><span data-stu-id="b9396-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="b9396-175">Dans MSBuild, cela s’effectue à l’aide d’[éléments](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="b9396-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="b9396-176">L’exemple suivant illustre une conversion courante :</span><span class="sxs-lookup"><span data-stu-id="b9396-176">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="b9396-177">Plusieurs [modèles d’utilisation des caractères génériques (globbing)](https://en.wikipedia.org/wiki/Glob_(programming)) par défaut sont ajoutés automatiquement par le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9396-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="b9396-178">Pour plus d’informations, consultez [Valeurs des éléments de compilation par défaut](https://aka.ms/sdkimplicititems).</span><span class="sxs-lookup"><span data-stu-id="b9396-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="b9396-179">Tous les éléments MSBuild `ItemGroup` prennent en charge `Include`, `Exclude` et `Remove`.</span><span class="sxs-lookup"><span data-stu-id="b9396-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="b9396-180">La disposition du package à l’intérieur du fichier .nupkg peut être modifiée avec `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="b9396-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="b9396-181">À l’exception de `Content`, la plupart des groupes d’éléments impliquent explicitement l’ajout de `Pack="true"` dans le package.</span><span class="sxs-lookup"><span data-stu-id="b9396-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="b9396-182">`Content` est placé dans le dossier *content* dans un package, car la propriété MSBuild `<IncludeContentInPack>` est définie sur `true` par défaut.</span><span class="sxs-lookup"><span data-stu-id="b9396-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="b9396-183">Pour plus d’informations, consultez [Inclusion de contenu dans un package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="b9396-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="b9396-184">`PackagePath="%(Identity)"` est une méthode rapide pour définir un chemin de package sur le chemin du fichier relatif au projet.</span><span class="sxs-lookup"><span data-stu-id="b9396-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="b9396-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="b9396-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="b9396-186">xUnit</span><span class="sxs-lookup"><span data-stu-id="b9396-186">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="b9396-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="b9396-187">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b9396-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9396-188">See also</span></span>

- [<span data-ttu-id="b9396-189">Vue d’ensemble générale des modifications de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="b9396-189">High-level overview of changes in CLI</span></span>](cli-msbuild-architecture.md)
