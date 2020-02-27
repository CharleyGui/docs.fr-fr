---
title: Vue d’ensemble du SDK de projet .NET Core
description: En savoir plus sur les kits de développement logiciel (SDK) de projet .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: c41b25bf7933e7b1f6cb50da5e52dc0b312f5c74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626248"
---
# <a name="net-core-project-sdks"></a>Kits de développement logiciel (SDK) de projet .NET Core

Les projets .NET Core sont associés à un kit de développement logiciel (SDK). Chaque kit de développement logiciel (SDK) de projet est un ensemble de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild et de [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication de code.

## <a name="available-sdks"></a>Kits de développement logiciel disponibles

Les kits de développement logiciel (SDK) suivants sont disponibles pour .NET Core :

| id | Description | Référentiel|
| - | - | - |
| `Microsoft.NET.Sdk` | Kit SDK .NET Core | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | Le kit de [développement logiciel (SDK) Web](/aspnet/core/razor-pages/web-sdk) .net Core | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | Le kit de [développement logiciel (SDK)](/aspnet/core/razor-pages/sdk) .net Core Razor |
| `Microsoft.NET.Sdk.Worker` | Kit de développement logiciel (SDK) .NET Core Worker service |
| `Microsoft.NET.Sdk.WindowsDesktop` | Le kit de développement logiciel (SDK) .NET Core WinForms et WPF |

Le kit SDK .NET Core est le kit de développement logiciel (SDK) de base pour .NET Core. Les autres kits de développement logiciel (SDK) référencent les kit SDK .NET Core, et les propriétés de kit SDK .NET Core associées aux autres kits de développement logiciel (SDK) sont disponibles. Le kit de développement logiciel (SDK) Web, par exemple, dépend à la fois du kit SDK .NET Core et du kit de développement logiciel (SDK) Razor.

Vous pouvez également créer votre propre kit de développement logiciel (SDK) qui peut être distribué via NuGet.

## <a name="project-files"></a>Fichiers projet

Les projets .NET Core sont basés sur le format [MSBuild](/visualstudio/msbuild/msbuild) . Les fichiers projet, qui ont des extensions telles que C# *. csproj* pour les projets F# et *. fsproj* pour les projets, sont au format XML. L’élément racine d’un fichier projet MSBuild est l’élément de [projet](/visualstudio/msbuild/project-element-msbuild) . L’élément `Project` a un attribut `Sdk` facultatif qui spécifie le kit de développement logiciel (SDK) et la version à utiliser. Pour utiliser les outils .NET Core et générer votre code, affectez à l’attribut `Sdk` l’un des ID figurant dans le tableau kits de développement logiciel ( [SDK) disponibles](#available-sdks) .

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
> Sur un ordinateur Windows, les fichiers *SDK. props* et *SDK. targets* se trouvent dans le dossier *%ProgramFiles%\dotnet\sdk\\[version] \Sdks\Microsoft.net.Sdk\Sdk*

### <a name="preprocess-the-project-file"></a>Prétraiter le fichier projet

Vous pouvez voir le projet entièrement développé, car MSBuild le voit après l’inclusion du kit de développement logiciel (SDK) et de ses cibles à l’aide de la commande `dotnet msbuild -preprocess`. Le commutateur de [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](../tools/dotnet-msbuild.md) indique quels fichiers sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet.

Si le projet comporte plusieurs frameworks cibles, vous ne concentrez les résultats de la commande que sur un Framework en le spécifiant en tant que propriété MSBuild. Par exemple :

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>La compilation par défaut comprend

Les inclusions et les exclusions par défaut pour les éléments de compilation et les ressources incorporées sont définies dans le kit de développement logiciel (SDK). Contrairement aux projets de .NET Framework non SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier projet, car les valeurs par défaut couvrent les cas d’utilisation les plus courants. Cela donne lieu à des fichiers de projet plus petits qui sont plus faciles à comprendre et à modifier manuellement, si nécessaire.

Le tableau suivant indique l’élément et les [modèles glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le kit SDK .net Core :

| Élément           | Inclure Glob                              | Exclure Glob                                                  | Supprimer Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compiler           | \*\*/\*.cs (ou autres extensions de langage) | \*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc  | N/A                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

> [!NOTE]
> Les dossiers `./bin` et `./obj`, représentés par les propriétés `$(BaseOutputPath)` et `$(BaseIntermediateOutputPath)` MSBuild, sont exclus du modèles glob par défaut. Les exclusions sont représentées par la propriété `$(DefaultItemExcludes)`.

Si vous définissez explicitement ces éléments dans votre fichier projet, vous risquez de recevoir l’erreur suivante :

**Des éléments de compilation en double ont été inclus. Le kit de développement logiciel (SDK) .NET comprend les éléments de compilation de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété’EnableDefaultCompileItems’sur’false’si vous souhaitez les inclure explicitement dans votre fichier projet.**

Pour résoudre l’erreur, supprimez les éléments de `Compile` explicites qui correspondent aux éléments implicites figurant dans le tableau précédent, ou affectez à la propriété `EnableDefaultCompileItems` la valeur `false`, ce qui désactive l’inclusion implicite :

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Si vous souhaitez spécifier, par exemple, certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l’élément `Content`.

`EnableDefaultCompileItems` désactive uniquement `Compile` modèles glob, mais n’affecte pas les autres modèles glob, comme le Glob implicite `None` qui s’applique également aux éléments \*. cs. Pour cette raison, Explorateur de solutions dans Visual Studio affiche les éléments \*. cs dans le cadre du projet, inclus en tant qu’éléments de `None`. Pour désactiver la glob implicite `None`, définissez `EnableDefaultNoneItems` sur `false`:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Pour désactiver *toutes les* modèles glob implicites, affectez à la propriété `EnableDefaultItems` la valeur `false`:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Personnaliser la Build

Il existe plusieurs façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build). Vous souhaiterez peut-être substituer une propriété en la passant comme argument à une commande [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) . Vous pouvez également ajouter la propriété au fichier projet ou à un fichier *Directory. Build. props* . Pour obtenir la liste des propriétés utiles pour les projets .NET Core, consultez [propriétés MSBuild pour les projets kit SDK .net Core](msbuild-props.md).

## <a name="see-also"></a>Voir aussi

- [Installez .NET Core](../install/index.md)
- [Comment utiliser les kits de développement logiciel (SDK) de projet MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
