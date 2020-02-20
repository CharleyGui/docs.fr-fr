---
title: Modèle d’extensibilité des outils CLI .NET Core
description: Découvrez comment vous pouvez étendre le CLI .NET Core.
ms.date: 04/12/2017
ms.openlocfilehash: 56a9cedc090ddca446c0ee1a60f2ca49590e7635
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451153"
---
# <a name="net-core-cli-extensibility-model"></a>Modèle d’extensibilité des outils CLI .NET Core

Cet article décrit les différentes façons dont vous pouvez étendre les CLI .NET Core et explique les scénarios qui les pilotent.
Vous verrez comment utiliser les outils et comment créer les différents types d’outils.

## <a name="how-to-extend-the-cli"></a>Comment étendre l’interface CLI
L’interface CLI peut être étendue de trois manières principales :

1. [Par le biais des packages NuGet, par projet](#per-project-based-extensibility)

   Les outils par projet sont contenus dans le contexte du projet, mais ils permettent une installation rapide grâce à une restauration.

2. [Par le biais des packages NuGet avec des cibles personnalisées](#custom-targets)

   Les cibles personnalisées vous permettent d’étendre facilement le processus de génération avec des tâches personnalisées.

3. [Par le biais du chemin (PATH) du système](#path-based-extensibility)

   Les outils basés sur le chemin sont efficaces pour les outils généraux multiprojets qui sont utilisables sur un seul ordinateur.

Les trois mécanismes d’extensibilité présentés ci-dessus ne sont pas exclusifs. Vous pouvez utiliser un seul, une partie ou la totalité d’entre eux. Le choix de la méthode dépend en grande partie de l’objectif de votre extension.

## <a name="per-project-based-extensibility"></a>Extensibilité par projet
Les outils par projet sont des [déploiements dépendants du framework](../deploying/index.md#publish-runtime-dependent) qui sont distribués dans les packages NuGet. Les outils sont uniquement disponibles dans le contexte du projet qui les référence et pour lequel ils sont restaurés. Les appels en dehors du contexte du projet (par exemple, en dehors du répertoire qui contient le projet) échouent parce que la commande est introuvable.

Ces outils sont parfaits pour les serveurs de build, puisque rien en dehors du fichier projet n’est nécessaire. Le processus de génération exécute la restauration pour le projet qu’il génère, et des outils seront disponibles. Les projets de langage, tels que F#, figurent également dans cette catégorie puisque chaque projet ne peut être écrit que dans un langage.

Enfin, ce modèle d’extensibilité prend en charge la création d’outils qui ont besoin d’accéder à la sortie générée du projet. Par exemple, les outils d’affichage Razor des applications MVC [ASP.NET](https://www.asp.net/) appartiennent à cette catégorie.

### <a name="consuming-per-project-tools"></a>Utilisation des outils par projet
Vous devez ajouter un élément `<DotNetCliToolReference>` à votre fichier projet pour chaque outil que vous souhaitez utiliser. À l’intérieur de l’élément `<DotNetCliToolReference>`, vous référencez le package dans lequel réside l’outil et spécifiez la version dont vous avez besoin. Après l’exécution de [`dotnet restore`](dotnet-restore.md), l’outil et ses dépendances sont restaurés.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pour les outils qui doivent charger la sortie de génération du projet pour l’exécution, il existe généralement une autre dépendance qui est répertoriée sous les dépendances régulières du fichier projet. Étant donné que l’interface CLI utilise MSBuild comme moteur de génération, nous vous recommandons d’écrire ces parties de l’outil sous forme de [cibles](/visualstudio/msbuild/msbuild-targets) et [tâches](/visualstudio/msbuild/msbuild-tasks) MSBuild personnalisées puisqu’elles peuvent ensuite prendre part à l’ensemble du processus de génération. Elles peuvent aussi facilement récupérer tout ou partie des données produites par la génération, notamment l’emplacement des fichiers de sortie ou la configuration en cours de génération, etc. Toutes ces informations deviennent un jeu de propriétés MSBuild qui peut être lu à partir de toutes les cibles. Vous verrez comment ajouter une cible personnalisée à l’aide de NuGet plus loin dans ce document.

Voyons un exemple d’ajout d’un outil simple de type « tools-only » à un projet simple. Prenons un exemple de commande appelé `dotnet-api-search` qui vous permette de parcourir les packages NuGet à la recherche de l’API spécifiée. Voici le fichier projet de l’application console qui utilise cet outil :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

L’élément `<DotNetCliToolReference>` est structuré de la même façon que l’élément `<PackageReference>`. Pour procéder à la restauration, il a besoin de l’ID de package du package qui contient l’outil et sa version.

### <a name="building-tools"></a>Outils de création
Comme nous l’avons mentionné précédemment, les outils sont des applications console portables. Vous les créez comme toute autre application console.
Une fois l’outil créé, utilisez la commande [`dotnet pack`](dotnet-pack.md) pour créer un package NuGet (fichier .nupkg) devant contenir votre code, les informations sur ses dépendances, etc. Vous pouvez donner n’importe quel nom au package. Toutefois, l’application qui s’y trouve, le fichier binaire de l’outil, doit respecter la convention de `dotnet-<command>` pour pouvoir être appelée par `dotnet`.

> [!NOTE]
> Dans les versions antérieures à RC3 des outils en ligne de commande .NET Core, la commande `dotnet pack` présentait un bogue qui empêchait la compression de *.runtimeconfig.json* avec l’outil. L’absence de ce fichier aboutit à des erreurs lors de l’exécution. Si vous rencontrez ce comportement, veillez à utiliser les outils les plus récents et essayez `dotnet pack` une nouvelle fois.

Étant donné que les outils sont des applications portables, l’utilisateur qui utilise un outil doit disposer de la version des bibliothèques .NET Core à l’aide desquelles l’outil a été développé, afin de pouvoir l’exécuter. Toute autre dépendance que l’outil utilise et qui ne figure pas dans les bibliothèques .NET Core est restaurée et placée dans le cache de NuGet. L’outil entier est, par conséquent, exécuté à l’aide des assemblys des bibliothèques .NET Core et du cache de NuGet.

Ces types d’outils ont un graphique de dépendance qui est complètement distinct du graphique de dépendance du projet qui les utilise. Le processus de restauration restaure d’abord les dépendances du projet, puis restaure chacun des outils et leurs dépendances.

Vous trouverez des exemples plus complets dans le [dépôt sur les outils CLI .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Vous pouvez également voir l’[implémentation des outils utilisés](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) dans le même dépôt.

## <a name="custom-targets"></a>Cibles personnalisées

NuGet peut [empaqueter des fichiers de cibles et de propriétés MSBuild personnalisées](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package). Avec le déplacement de .NET Core pour utiliser MSBuild, le même mécanisme d’extensibilité s’applique désormais aux projets .NET Core. Vous utilisez ce type d’extensibilité quand vous souhaitez étendre le processus de génération, accéder à tous les artefacts dans le processus de génération, tels que les fichiers générés, inspecter la configuration sous laquelle la build est appelée, etc.

Dans l’exemple suivant, vous pouvez voir le fichier projet de la cible à l’aide de la syntaxe `csproj`. Celle-ci indique à la commande [`dotnet pack`](dotnet-pack.md) les éléments à empaqueter. Les fichiers de cibles et les assemblys sont placés dans le dossier *build* à l’intérieur du package. Notez l’élément `<ItemGroup>` dont la propriété `Label` a la valeur `dotnet pack instructions`, et la cible définie en dessous.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
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
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

L’utilisation de cibles personnalisées s’effectue en fournissant un `<PackageReference>` qui pointe vers le package et sa version dans le projet en cours d’extension. Contrairement aux outils, le package des cibles personnalisées n’est pas inclus dans la fermeture de dépendance du projet de consommation.

L’utilisation de la cible personnalisée dépend uniquement de la façon dont vous la configurez. Puisqu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible donnée, exécutée après une autre cible, et peut également être appelée manuellement à l’aide de la commande `dotnet msbuild -t:<target-name>`.

Toutefois, si vous souhaitez procurer une meilleure expérience à vos utilisateurs, vous pouvez combiner des outils par projet et des cibles personnalisées. Dans ce scénario, l’outil par projet se contenterait essentiellement d’accepter tous les paramètres nécessaires à partir desquels il générerait l’invocation [`dotnet msbuild`](dotnet-msbuild.md) nécessaire pour exécuter la cible. Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).

## <a name="path-based-extensibility"></a>Extensibilité basée sur le chemin (PATH)
L’extensibilité basée sur le chemin est généralement utilisée pour les ordinateurs de développement qui nécessitent un outil qui traite conceptuellement plusieurs projets. Le principal inconvénient de ce mécanisme d’extension est qu’il est limité à l’ordinateur sur lequel est installé l’outil. Si vous avez besoin de l’installer sur un autre ordinateur, vous devrez le déployer.

Ce modèle d’extensibilité des outils CLI est très simple. Comme indiqué dans la [présentation des outils CLI .NET Core](index.md), le pilote `dotnet` peut exécuter toutes les commandes dont le nom respecte la convention `dotnet-<command>`. La logique de résolution par défaut sonde d’abord plusieurs emplacements avant de revenir au chemin (PATH) système. Si la commande demandée existe dans le chemin système et s’il s’agit d’un fichier binaire qui peut être appelé, le pilote `dotnet` l’appellera.

Le fichier doit être exécutable. Sur les systèmes Unix, il peut s’agir de tous les fichiers dont le bit d’exécution est défini via `chmod +x`. Sur Windows, vous pouvez utiliser des fichiers *cmd*.

Examinons l’implémentation simple d’un outil « Hello World ». Nous allons utiliser `bash` et `cmd` sur Windows.
La commande suivante répète simplement « Hello World » dans la console.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

Sur Mac OS, nous pouvons enregistrer ce script en tant que `dotnet-hello` et définir son bit exécutable avec `chmod +x dotnet-hello`. Nous pouvons ensuite créer un lien symbolique vers le script dans `/usr/local/bin` à l’aide de la commande `ln -s <full_path>/dotnet-hello /usr/local/bin/`. Cela permet d’appeler la commande à l’aide de la syntaxe `dotnet hello`.

Sur Windows, nous pouvons enregistrer ce script en tant que `dotnet-hello.cmd` et le placer dans un emplacement figurant dans un chemin système (ou vous pouvez l’ajouter à un dossier qui existe déjà dans le chemin). Après cela, vous pouvez simplement utiliser `dotnet hello` pour exécuter cet exemple.
