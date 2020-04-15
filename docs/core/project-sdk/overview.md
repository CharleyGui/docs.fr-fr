---
title: vue d’ensemble du projet SDK de base de NET
description: En savoir plus sur le projet .NET Core SDKs.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: d0ac01dca31dffea482745126e00c34b1da20774
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389666"
---
# <a name="net-core-project-sdks"></a>.NET Core projet SDKs

.NET Les projets de base sont associés à un kit de développement logiciel (SDK). Chaque *projet SDK* est un ensemble d’objectifs MSBuild et [de tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’emballage et de la publication du code. [targets](/visualstudio/msbuild/msbuild-targets) Un projet qui fait référence à un projet SDK est parfois appelé un *projet de style SDK.*

## <a name="available-sdks"></a>SDKs disponibles

Les SDK suivants sont disponibles pour .NET Core:

| id | Description | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | Le SDK core .NET | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | Le .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | Le rasoir de base .NET [SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | Le service de travailleurs de base .NET SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | Les WinForms de base de .NET et WPF SDK |

Le .NET Core SDK est la base SDK pour .NET Core. Les autres SDK font référence à la SDK Core .NET, et les projets qui sont associés aux autres SDK ont toutes les propriétés SDK de base .NET à leur disposition. Le Web SDK, par exemple, dépend à la fois du .NET Core SDK et du Razor SDK.

Vous pouvez également écrire votre propre SDK qui peut être distribué via NuGet.

## <a name="project-files"></a>Fichiers projet

.NET Les projets de base sont basés sur le format [MSBuild.](/visualstudio/msbuild/msbuild) Les fichiers de projet, qui ont des extensions comme *.csproj* pour les projets C et *.fsproj* pour les projets F, sont en format XML. L’élément racine d’un fichier de projet MSBuild est l’élément [projet.](/visualstudio/msbuild/project-element-msbuild) L’élément `Project` a `Sdk` un attribut facultatif qui spécifie ce SDK (et la version) à utiliser. Pour utiliser les outils .NET Core et `Sdk` construire votre code, définissez l’attribut à l’un des DI dans la table [SDKs disponible.](#available-sdks)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Pour spécifier un SDK qui vient de NuGet, inclure la version à la fin du nom, ou spécifier le nom et la version dans le fichier *global.json.*

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Une autre façon de spécifier le SDK est avec l’élément [Sdk](/visualstudio/msbuild/sdk-element-msbuild) de haut niveau:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Le référencement d’un SDK de l’une de ces façons simplifie grandement les fichiers de projets pour .NET Core. Tout en évaluant le projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du dossier du projet et `Sdk.targets` en bas.

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
> Sur une machine Windows, les fichiers *Sdk.props* et *Sdk.targets* peuvent être trouvés dans le dossier *%ProgramFiles%'dotnet’sdk\\[version] -Sdks-Microsoft.NET.Sdk-Sdk.*

### <a name="preprocess-the-project-file"></a>Prétraiter le dossier du projet

Vous pouvez voir le projet entièrement élargi comme MSBuild le voit après `dotnet msbuild -preprocess` le SDK et ses cibles sont inclus en utilisant la commande. Le commutateur de [`dotnet msbuild`](../tools/dotnet-msbuild.md) [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande montre quels fichiers sont importés, leurs sources, et leurs contributions à la construction sans réellement construire le projet.

Si le projet a plusieurs cadres cibles, concentrez les résultats de la commande sur un seul cadre en le spécifiant comme propriété MSBuild. Par exemple :

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>La compilation par défaut comprend

La valeur par défaut comprend et exclut pour les éléments de compilation et les ressources intégrées sont définis dans le SDK. Contrairement aux projets cadres .NET non-SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier de projet, car les défauts couvrent la plupart des cas d’utilisation courants. Cela conduit à de plus petits fichiers de projet qui sont plus faciles à comprendre ainsi que modifier à la main, si nécessaire.

Le tableau suivant montre quel élément et quels [globs](https://en.wikipedia.org/wiki/Glob_(programming)) sont inclus et exclus dans le SDK core .NET:

| Élément           | Inclure Glob                              | Exclure Glob                                                  | Supprimer Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compiler           | \*\*/\*.cs (ou autres extensions de langage) | \*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc  | N/A                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

> [!NOTE]
> Les `./bin` `./obj` dossiers, qui sont représentés `$(BaseIntermediateOutputPath)` par les propriétés et MSBuild, `$(BaseOutputPath)` sont exclus des globs par défaut. Les exclus sont représentés par le bien `$(DefaultItemExcludes)`.

Si vous définissez explicitement ces éléments dans votre fichier de projet, vous êtes susceptible d’obtenir l’erreur suivante :

**Des éléments de compiles en double ont été inclus. Le .NET SDK inclut les éléments de compilation de votre répertoire de projet par défaut. Vous pouvez soit supprimer ces éléments de votre dossier de projet, soit définir la propriété 'EnableDefaultCompileItems' à 'faux' si vous souhaitez les inclure explicitement dans votre dossier de projet.**

Pour résoudre l’erreur, `Compile` soit supprimez les éléments explicites qui correspondent `EnableDefaultCompileItems` aux `false`éléments implicites énumérés sur le tableau précédent, ou définissez la propriété à , ce qui désactive l’inclusion implicite:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Si vous souhaitez spécifier, par exemple, certains fichiers pour être publiés avec votre application, vous `Content` pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l’élément.

`EnableDefaultCompileItems`ne désactive que les `Compile` globs, mais n’affecte pas d’autres globs, comme le glob implicite `None` qui s’applique également aux \*articles .cs. Pour cette raison, Solution Explorer \*dans Visual Studio montre .cs `None` articles dans le cadre du projet, inclus comme éléments. Pour désactiver le `None` glob `EnableDefaultNoneItems` implicite, réglé sur `false`:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Pour désactiver *tous les* globs `EnableDefaultItems` implicites, définissez la propriété à `false`:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Personnaliser la construction

Il existe différentes façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build). Vous pouvez remplacer une propriété en la passant comme argument à une commande [de msbuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet.](../tools/index.md) Vous pouvez également ajouter la propriété au fichier du projet ou à un fichier *Directory.Build.props.* Pour une liste de propriétés utiles pour les projets .NET Core, voir [propriétés MSBuild pour .NET Core SDK projets](msbuild-props.md).

### <a name="custom-targets"></a>Cibles personnalisées

.NET Les projets de base peuvent emballer des cibles et des propriétés MSBuild personnalisées pour les utiliser par les projets qui consomment le paquet. Utilisez ce type d’extéabilité lorsque vous voulez :

- Étendre le processus de construction.
- Accédez aux artefacts du processus de construction, tels que les fichiers générés.
- Inspectez la configuration sous laquelle la construction est invoquée.

Vous ajoutez des cibles ou des propriétés `<package_id>.props` de construction `Contoso.Utility.UsefulStuff.targets`personnalisées en plaçant des fichiers sous la forme `<package_id>.targets` ou (par exemple) dans le dossier de *construction* du projet.

Le XML suivant est un extrait d’un fichier *.csproj* qui indique à la [`dotnet pack`](../tools/dotnet-pack.md) commande ce qu’il faut emballer. L’élément `<ItemGroup Label="dotnet pack instructions">` place les fichiers cibles dans le dossier *de construction* à l’intérieur du paquet. L’élément `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` place les assemblages et les fichiers *.json* dans le dossier *de construction.*

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

Pour consommer une cible personnalisée dans `PackageReference` votre projet, ajoutez un élément qui indique le package et sa version. Contrairement aux outils, l’ensemble de cibles personnalisées est inclus dans la fermeture de la dépendance du projet de consommation.

Vous pouvez configurer comment utiliser la cible personnalisée. Puisqu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible `dotnet msbuild -t:<target-name>` donnée, courir après une autre cible, ou être invoquée manuellement en utilisant la commande. Toutefois, pour offrir une meilleure expérience utilisateur, vous pouvez combiner des outils par projet et des cibles personnalisées. Dans ce scénario, l’outil par projet accepte tous les paramètres [`dotnet msbuild`](../tools/dotnet-msbuild.md) nécessaires et traduit cela dans l’invocation requise qui exécute la cible. Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).

## <a name="see-also"></a>Voir aussi

- [Installez .NET Core](../install/index.md)
- [Comment utiliser msBuild projet SDKs](/visualstudio/msbuild/how-to-use-project-sdk)
- [Forfait personnalisé cibles et accessoires MSBuild avec NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
