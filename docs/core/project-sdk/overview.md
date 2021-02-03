---
title: Vue d’ensemble du SDK de projet .NET
titleSuffix: ''
description: Découvrez les kits de développement logiciel (SDK) de projet .NET.
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: d0eb4291f4def9263f37d2d09f09ef43d40dfbac
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506394"
---
# <a name="net-project-sdks"></a>SDK de projet .NET

Les projets .NET Core et .NET 5,0 et versions ultérieures sont associés à un kit de développement logiciel (SDK). Chaque *Kit de développement logiciel (SDK) de projet* est un ensemble de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild et de [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication de code. Un projet qui fait référence à un kit de développement logiciel (SDK) de projet est parfois appelé *projet de style SDK*.

## <a name="available-sdks"></a>Kits de développement logiciel disponibles

Les kits de développement logiciel (SDK) suivants sont disponibles :

| id | Description | Dépôt|
| - | - | - |
| `Microsoft.NET.Sdk` | Le kit de développement logiciel (SDK) .NET | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | [SDK Web](/aspnet/core/razor-pages/web-sdk) .net | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | Le [Kit de développement logiciel (SDK) .net Razor](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | Le kit de développement logiciel (SDK) .NET Worker service |
| `Microsoft.NET.Sdk.WindowsDesktop` | Le kit de développement logiciel (SDK) WinForms et WPF\* | <https://github.com/dotnet/winforms> et <https://github.com/dotnet/wpf> |

Le kit de développement logiciel (SDK) .NET est le kit de développement logiciel de base pour .NET. Les autres SDK référencent le kit de développement logiciel (SDK) .NET, et les projets associés aux autres SDK disposent de toutes les propriétés du SDK .NET. Le SDK Web, par exemple, dépend à la fois du kit de développement logiciel (SDK) .NET et du kit de développement logiciel (SDK) Razor.

Vous pouvez également créer votre propre kit de développement logiciel (SDK) qui peut être distribué via NuGet.

\* À compter de .NET 5,0, les projets Windows Forms et Windows Presentation Foundation (WPF) doivent spécifier le kit de développement logiciel (SDK) .NET ( `Microsoft.NET.Sdk` ) au lieu de `Microsoft.NET.Sdk.WindowsDesktop` . Pour ces projets, `TargetFramework` l’affectation de la valeur à `net5.0-windows` et `UseWPF` ou `UseWindowsForms` à `true` entraîne l’importation automatique du kit de développement logiciel (SDK) Windows. Si votre projet cible .NET 5,0 ou une version ultérieure et spécifie le `Microsoft.NET.Sdk.WindowsDesktop` Kit de développement logiciel (SDK), vous obtiendrez un avertissement de génération NETSDK1137.

## <a name="project-files"></a>Fichiers projet

Les projets .NET sont basés sur le format [MSBuild](/visualstudio/msbuild/msbuild) . Les fichiers projet, qui ont des extensions telles que *. csproj* pour les projets C# et *. fsproj* pour les projets F #, sont au format XML. L’élément racine d’un fichier projet MSBuild est l’élément de [projet](/visualstudio/msbuild/project-element-msbuild) . L' `Project` élément possède un `Sdk` attribut facultatif qui spécifie le kit de développement logiciel (SDK) (et la version) à utiliser. Pour utiliser les outils .NET et générer votre code, affectez `Sdk` à l’attribut l’un des ID dans le tableau [Kits de développement](#available-sdks) logiciel (SDK) disponibles.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Pour spécifier un kit de développement logiciel (SDK) qui provient de NuGet, incluez la version à la fin du nom, ou spécifiez le nom et la version dans le fichier *global.js* .

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

Le référencement d’un kit de développement logiciel (SDK) de l’une de ces manières simplifie grandement les fichiers projet pour .NET. Lors de l’évaluation du projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du fichier projet et `Sdk.targets` en bas.

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

## <a name="default-includes-and-excludes"></a>Inclusions et exclusions par défaut

La valeur par défaut inclut et exclut [ `Compile` les éléments, les](/visualstudio/msbuild/common-msbuild-project-items#compile) [ressources incorporées](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)et les [ `None` éléments](/visualstudio/msbuild/common-msbuild-project-items#none) sont définis dans le kit de développement logiciel (SDK). Contrairement aux projets de .NET Framework non SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier projet, car les valeurs par défaut couvrent les cas d’utilisation les plus courants. Ce comportement rend le fichier projet plus petit et plus facile à comprendre et à modifier manuellement, si nécessaire.

Le tableau suivant répertorie les éléments et les [modèles glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le kit de développement logiciel (SDK) .net :

| Élément           | Inclure Glob                              | Exclure Glob                                                  | Supprimer Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compiler           | \*\*/\*.cs (ou autres extensions de langage) | \*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc  | N/A                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

> [!NOTE]
> Les `./bin` `./obj` dossiers et, représentés par les `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Propriétés et MSBuild, sont exclus par défaut de modèles glob. Les exclusions sont représentées par la [propriété DefaultItemExcludes](msbuild-props.md#defaultitemexcludes).

### <a name="build-errors"></a>Erreurs de build

Si vous définissez explicitement l’un de ces éléments dans votre fichier projet, vous risquez d’obtenir une erreur de build « NETSDK1022 » similaire à ce qui suit :

  > Les éléments « compile » dupliqués ont été inclus. Le kit de développement logiciel (SDK) .NET comprend les éléments de « compilation » de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.

  > Les éléments’EmbeddedResource’dupliqués ont été inclus. Le kit de développement logiciel (SDK) .NET comprend les éléments’EmbeddedResource’de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété’EnableDefaultEmbeddedResourceItems’sur’false’si vous souhaitez les inclure explicitement dans votre fichier projet.

Pour résoudre les erreurs, effectuez l’une des opérations suivantes :

- Supprimez les `Compile` éléments explicites, `EmbeddedResource` ou `None` qui correspondent aux éléments implicites listés dans le tableau précédent.

- Affectez à la [propriété EnableDefaultItems](msbuild-props.md#enabledefaultitems) la valeur `false` pour désactiver toute inclusion de fichier implicite :

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  Si vous souhaitez spécifier des fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l' `Content` élément.

- Désactivez de manière sélective uniquement `Compile` , `EmbeddedResource` ou `None` modèles glob en affectant à la propriété [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems)ou [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) la valeur `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  Si vous désactivez uniquement `Compile` modèles glob, Explorateur de solutions dans Visual Studio affiche toujours \* les éléments. cs dans le cadre du projet, inclus en tant qu' `None` éléments. Pour désactiver la glob implicite `None` , affectez la valeur `EnableDefaultNoneItems` à `false` .

## <a name="implicit-package-references"></a>Références de package implicites

Quand vous ciblez .NET Core 1,0-2,2 ou .NET Standard 1,0-2,0, le kit de développement logiciel (SDK) .NET ajoute des références implicites à certains sous- *packages*. Un reconditionnement est un package basé sur une infrastructure qui se compose uniquement de dépendances sur d’autres packages. Les reconditionnements sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété [targetFramework](msbuild-props.md#targetframework) ou [TargetFrameworks](msbuild-props.md#targetframeworks) de votre fichier projet.

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp2.1</TargetFramework>
</PropertyGroup>
```

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
</PropertyGroup>
```

Si nécessaire, vous pouvez désactiver les références de package implicites à l’aide de la propriété [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) et ajouter des références explicites uniquement aux frameworks ou aux packages dont vous avez besoin.

Recommandations :

- Quand vous ciblez .NET Framework, .NET Core 1,0-2,2 ou .NET Standard 1,0-2,0, n’ajoutez pas de référence explicite aux `Microsoft.NETCore.App` packages ou à l' `NETStandard.Library` aide d’un `<PackageReference>` élément de votre fichier projet. Pour les projets .NET Core 1,0-2,2 et .NET Standard 1,0-2,0, ces packages sont référencés implicitement. Pour les projets .NET Framework, si une version de `NETStandard.Library` est nécessaire lors de l’utilisation d’un package NuGet basé sur .NET standard, NuGet installe automatiquement cette version.
- Si vous avez besoin d’une version spécifique du runtime lorsque vous ciblez .NET Core 1,0-2,2, utilisez la `<RuntimeFrameworkVersion>` propriété dans votre projet (par exemple, `1.0.4` ) au lieu de référencer le repackage. Par exemple, vous pouvez avoir besoin d’une version de correctif spécifique de 1.0.0 LTS Runtime si vous utilisez des [déploiements autonomes](../deploying/index.md#publish-self-contained).
- Si vous avez besoin d’une version spécifique du `NETStandard.Library` repackage lorsque vous ciblez .NET Standard 1,0-2,0, vous pouvez utiliser la `<NetStandardImplicitPackageVersion>` propriété et définir la version dont vous avez besoin.

## <a name="build-events"></a>Événements de build

Dans les projets de type SDK, utilisez une cible MSBuild nommée `PreBuild` ou `PostBuild` et définissez la `BeforeTargets` propriété pour `PreBuild` ou `AfterTargets` pour la propriété de `PostBuild` .

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - Vous pouvez utiliser n’importe quel nom pour les cibles MSBuild. Toutefois, l’IDE de Visual Studio reconnaît `PreBuild` et `PostBuild` cible, donc en utilisant ces noms, vous pouvez modifier les commandes dans l’IDE.
> - Les propriétés `PreBuildEvent` et ne `PostBuildEvent` sont pas recommandées dans les projets de style SDK, car les macros telles que ne sont pas `$(ProjectDir)` résolues. Par exemple, le code suivant n’est pas pris en charge :
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a>Personnaliser la Build

Il existe plusieurs façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build). Vous souhaiterez peut-être substituer une propriété en la passant comme argument à une commande [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) . Vous pouvez également ajouter la propriété au fichier projet ou à un fichier *Directory. Build. props* . Pour obtenir la liste des propriétés utiles pour les projets .NET, consultez informations de [référence sur MSBuild pour les projets SDK .net](msbuild-props.md).

### <a name="custom-targets"></a>Cibles personnalisées

Les projets .NET peuvent empaqueter des cibles et des propriétés MSBuild personnalisées pour une utilisation par les projets qui utilisent le package. Utilisez ce type d’extensibilité lorsque vous souhaitez :

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

- [Installez .NET Core](../install/index.yml)
- [Comment utiliser les kits de développement logiciel (SDK) de projet MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Packages et cibles MSBuild personnalisés avec NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
