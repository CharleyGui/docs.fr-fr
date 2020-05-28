---
title: Vue d’ensemble du SDK de projet .NET Core
titleSuffix: ''
description: En savoir plus sur les kits de développement logiciel (SDK) de projet .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 67dede3caabd2967adca22e7563376c761829655
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144237"
---
# <a name="net-core-project-sdks"></a>Kits de développement logiciel (SDK) de projet .NET Core

Les projets .NET Core sont associés à un kit de développement logiciel (SDK). Chaque *Kit de développement logiciel (SDK) de projet* est un ensemble de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild et de [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication de code. Un projet qui fait référence à un kit de développement logiciel (SDK) de projet est parfois appelé *projet de style SDK*.

## <a name="available-sdks"></a>Kits de développement logiciel disponibles

Les kits de développement logiciel (SDK) suivants sont disponibles pour .NET Core :

| id | Description | Référentiel|
| - | - | - |
| `Microsoft.NET.Sdk` | Kit SDK .NET Core | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | Le kit de [développement logiciel (SDK) Web](/aspnet/core/razor-pages/web-sdk) .net Core | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | Le kit de [développement logiciel (SDK)](/aspnet/core/razor-pages/sdk) .net Core Razor |
| `Microsoft.NET.Sdk.Worker` | Kit de développement logiciel (SDK) .NET Core Worker service |
| `Microsoft.NET.Sdk.WindowsDesktop` | Le kit de développement logiciel (SDK) .NET Core WinForms et WPF |

Le kit SDK .NET Core est le kit de développement logiciel (SDK) de base pour .NET Core. Les autres kits de développement logiciel (SDK) référencent les kit SDK .NET Core, et les propriétés de kit SDK .NET Core associées aux autres kits de développement logiciel (SDK) sont disponibles. Le kit de développement logiciel (SDK) Web, par exemple, dépend à la fois du kit SDK .NET Core et du kit de développement logiciel (SDK) Razor.

Vous pouvez également créer votre propre kit de développement logiciel (SDK) qui peut être distribué via NuGet.

## <a name="project-files"></a>Fichiers projet

Les projets .NET Core sont basés sur le format [MSBuild](/visualstudio/msbuild/msbuild) . Les fichiers projet, qui ont des extensions telles que *. csproj* pour les projets C# et *. fsproj* pour les projets F #, sont au format XML. L’élément racine d’un fichier projet MSBuild est l’élément de [projet](/visualstudio/msbuild/project-element-msbuild) . L' `Project` élément possède un `Sdk` attribut facultatif qui spécifie le kit de développement logiciel (SDK) (et la version) à utiliser. Pour utiliser les outils .NET Core et générer votre code, affectez `Sdk` à l’attribut l’un des ID figurant dans la table kits de développement logiciel ( [SDK) disponibles](#available-sdks) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Pour spécifier un kit de développement logiciel (SDK) qui provient de NuGet, incluez la version à la fin du nom, ou spécifiez le nom et la version dans le fichier *global. JSON* .

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Vous pouvez également spécifier le kit de développement logiciel (SDK) à l’aide de l’élément [SDK](/visualstudio/msbuild/sdk-element-msbuild) de niveau supérieur :

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Le référencement d’un kit de développement logiciel (SDK) de l’une de ces manières simplifie grandement les fichiers projet pour .NET Core. Lors de l’évaluation du projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du fichier projet et `Sdk.targets` en bas.

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> Sur un ordinateur Windows, les fichiers *SDK. props* et *SDK. targets* se trouvent dans le dossier *%ProgramFiles%\dotnet\sdk \\ [version] \Sdks\Microsoft.net.Sdk\Sdk*

### <a name="preprocess-the-project-file"></a>Prétraiter le fichier projet

Vous pouvez voir le projet entièrement développé, car MSBuild le voit après l’inclusion du kit de développement logiciel (SDK) et de ses cibles à l’aide de la `dotnet msbuild -preprocess` commande. Le commutateur de [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la [`dotnet msbuild`](../tools/dotnet-msbuild.md) commande indique quels fichiers sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet.

Si le projet comporte plusieurs frameworks cibles, vous ne concentrez les résultats de la commande que sur un Framework en le spécifiant en tant que propriété MSBuild. Par exemple :

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>La compilation par défaut comprend

Les éléments include et Exclude par défaut pour les éléments de compilation, les ressources incorporées et `None` les éléments sont définis dans le kit de développement logiciel (SDK). Contrairement aux projets de .NET Framework non SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier projet, car les valeurs par défaut couvrent les cas d’utilisation les plus courants. Cela rend le fichier projet plus petit et plus facile à comprendre et à modifier manuellement, si nécessaire.

Le tableau suivant indique les éléments et les [modèles glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le kit SDK .net Core :

| Élément           | Inclure Glob                              | Exclure Glob                                                  | Supprimer Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compiler           | \*\*/\*.cs (ou autres extensions de langage) | \*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc  | NON APPLICABLE                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | NON APPLICABLE                      |
| None              | \*\*/\*                                   | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

> [!NOTE]
> Les `./bin` `./obj` dossiers et, représentés par les `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Propriétés et MSBuild, sont exclus par défaut de modèles glob. Les exclusions sont représentées par la propriété `$(DefaultItemExcludes)` .

#### <a name="build-errors"></a>Erreurs de build

Si vous définissez explicitement l’un de ces éléments dans votre fichier projet, vous risquez d’obtenir une erreur de build « NETSDK1022 » similaire à ce qui suit :

  > Les éléments « compile » dupliqués ont été inclus. Le kit de développement logiciel (SDK) .NET comprend les éléments de « compilation » de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.

  > Les éléments’EmbeddedResource’dupliqués ont été inclus. Le kit de développement logiciel (SDK) .NET comprend les éléments’EmbeddedResource’de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété’EnableDefaultEmbeddedResourceItems’sur’false’si vous souhaitez les inclure explicitement dans votre fichier projet.

Pour résoudre les erreurs, effectuez l’une des opérations suivantes :

- Supprimez les `Compile` éléments explicites, `EmbeddedResource` ou `None` qui correspondent aux éléments implicites listés dans le tableau précédent.

- Affectez à la propriété la valeur `EnableDefaultItems` `false` pour désactiver toute inclusion de fichier implicite :

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  Si vous souhaitez spécifier des fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l' `Content` élément.

- Désactivez de manière sélective uniquement `Compile` , `EmbeddedResource` ou `None` modèles glob en affectant `EnableDefaultCompileItems` à la propriété, ou la valeur `EnableDefaultEmbeddedResourceItems` `EnableDefaultNoneItems` `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  Si vous désactivez uniquement `Compile` modèles glob, Explorateur de solutions dans Visual Studio affiche toujours \* les éléments. cs dans le cadre du projet, inclus en tant qu' `None` éléments. Pour désactiver la glob implicite `None` , affectez la valeur `EnableDefaultNoneItems` à `false` .

## <a name="customize-the-build"></a>Personnaliser la Build

Il existe plusieurs façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build). Vous souhaiterez peut-être substituer une propriété en la passant comme argument à une commande [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) . Vous pouvez également ajouter la propriété au fichier projet ou à un fichier *Directory. Build. props* . Pour obtenir la liste des propriétés utiles pour les projets .NET Core, consultez [référence MSBuild pour les projets kit SDK .net Core](msbuild-props.md).

### <a name="custom-targets"></a>Cibles personnalisées

Les projets .NET Core peuvent empaqueter des cibles et des propriétés MSBuild personnalisées pour une utilisation par des projets qui utilisent le package. Utilisez ce type d’extensibilité lorsque vous souhaitez :

- Étendez le processus de génération.
- Accédez aux artefacts du processus de génération, tels que les fichiers générés.
- Inspectez la configuration sous laquelle la build est appelée.

Vous ajoutez des cibles de génération personnalisées ou des propriétés en plaçant des fichiers dans le formulaire `<package_id>.targets` ou `<package_id>.props` (par exemple, `Contoso.Utility.UsefulStuff.targets` ) dans le dossier *Build* du projet.

Le code XML suivant est un extrait d’un fichier *. csproj* qui indique [`dotnet pack`](../tools/dotnet-pack.md) à la commande ce qu’il faut empaqueter. L' `<ItemGroup Label="dotnet pack instructions">` élément place les fichiers cibles dans le dossier de *Build* à l’intérieur du package. L' `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` élément place les assemblys et les fichiers *. JSON* dans le dossier de *Build* .

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

Pour utiliser une cible personnalisée dans votre projet, ajoutez un `PackageReference` élément qui pointe vers le package et sa version. Contrairement aux outils, le package de cibles personnalisées est inclus dans la fermeture des dépendances du projet consommatrice.

Vous pouvez configurer l’utilisation de la cible personnalisée. Étant donné qu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible donnée, exécutée après une autre cible, ou être appelée manuellement à l’aide de la `dotnet msbuild -t:<target-name>` commande. Toutefois, pour offrir une meilleure expérience utilisateur, vous pouvez combiner des outils par projet et des cibles personnalisées. Dans ce scénario, l’outil par projet accepte tous les paramètres nécessaires et les convertit en l’appel requis [`dotnet msbuild`](../tools/dotnet-msbuild.md) qui exécute la cible. Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).

## <a name="see-also"></a>Voir aussi

- [Installez .NET Core](../install/index.md)
- [Comment utiliser les kits de développement logiciel (SDK) de projet MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Packages et cibles MSBuild personnalisés avec NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
