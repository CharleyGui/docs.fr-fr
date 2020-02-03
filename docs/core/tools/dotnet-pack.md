---
title: Commande dotnet pack
description: La commande dotnet pack crée des packages NuGet pour votre projet .NET Core.
ms.date: 08/08/2019
ms.openlocfilehash: 057d1029e5c933912c43c178b6db8a8498f2ed57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734123"
---
# <a name="dotnet-pack"></a>dotnet pack

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

`dotnet pack` : Place le code dans un package NuGet.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet pack` génère le projet et crée les packages NuGet. Le résultat de cette commande est un package NuGet (autrement dit, un fichier *. nupkg* ).

Si vous souhaitez générer un package qui contient les symboles de débogage, deux options sont disponibles :

- `--include-symbols` : crée le package de symboles.
- `--include-source`-elle crée le package de symboles avec un dossier `src` dans contenant les fichiers sources.

Les dépendances NuGet du projet empaqueté sont ajoutées dans le fichier  *.nuspec*, pour pouvoir être correctement résolues lors de l’installation du package. Les références entre projets ne sont pas empaquetées à l’intérieur du projet. Actuellement, vous devez disposer d’un package par projet si vous avez des dépendances entre projets.

Par défaut, `dotnet pack` génère d’abord le projet. Pour éviter ce comportement, passez l’option `--no-build`. Cette option s’avère souvent utile dans les scénarios de build d’intégration continue (CI), pour lesquels vous savez que le code a déjà été créé.

Vous pouvez fournir des propriétés MSBuild à la commande `dotnet pack` pour le processus de compression. Pour plus d’informations, consultez [Propriétés des métadonnées NuGet](csproj.md#nuget-metadata-properties) et [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). La section [Exemples](#examples) montre comment utiliser le commutateur MSBuild -p pour deux scénarios différents.

Par défaut, les projets web ne peuvent pas être ajoutés dans un package. Pour remplacer le comportement par défaut, ajoutez la propriété suivante à votre fichier *.csproj* :

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

  Projet ou solution à empaqueter. Il s’agit d’un chemin d’accès à un [fichier csproj](csproj.md), à un fichier solution ou à un répertoire. S’il n’est pas spécifié, la commande recherche un fichier projet ou solution dans le répertoire actif.

## <a name="options"></a>Options

- **`-c|--configuration {Debug|Release}`**

  Définit la configuration de build. La valeur par défaut est `Debug`.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*. Option disponible à partir du kit SDK .NET Core 2.0.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--include-source`**

  Comprend les packages NuGet de symboles de débogage en plus des packages NuGet standard dans le répertoire de sortie. Les fichiers sources sont inclus dans le dossier `src` au sein du package de symboles.

- **`--include-symbols`**

  Comprend les packages NuGet de symboles de débogage en plus des packages NuGet standard dans le répertoire de sortie.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple). Disponible à partir du kit SDK .NET Core 3.0.

- **`--no-build`**

  Ne génère pas le projet avant de créer le package. L’indicateur `--no-restore` est également défini implicitement.

- **`--no-dependencies`**

  Ignore les références entre projets et restaure uniquement le projet racine. Option disponible à partir du kit SDK .NET Core 2.0.

- **`--no-restore`**

  N’effectue pas de restauration implicite à l’exécution de la commande. Option disponible à partir du kit SDK .NET Core 2.0.

- **`--nologo`**

  N’affiche pas la bannière de démarrage ni le message de copyright. Disponible à partir du kit SDK .NET Core 3.0.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Place les packages générés dans le répertoire spécifié.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Option disponible à partir du kit SDK .NET Core 2.0.

- **`-s|--serviceable`**

  Définit l’indicateur d’un état pouvant faire l’objet d’une maintenance dans le package. Pour plus d’informations, consultez [Blog .NET : .NET 4.5.1 prend en charge les mises à jour de sécurité de Microsoft pour les bibliothèques NuGet .NET](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Définit la valeur de la propriété MSBuild `$(VersionSuffix)` dans le projet.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="examples"></a>Exemples

- Empaquetez le projet dans le répertoire actif :

  ```dotnetcli
  dotnet pack
  ```

- Empaqueter le projet `app1` :

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Empaqueter le projet dans le répertoire actif et placer les packages résultants dans le dossier `nupkgs` :

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Empaqueter le projet dans le répertoire actif du dossier `nupkgs` et ignorer l’étape de génération :

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Avec le suffixe de version du projet configuré comme `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` dans le fichier *.csproj*, empaqueter le projet actif et mettre à jour la version du package obtenue avec le suffixe donné :

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Affectez `2.1.0` à la version du package à l’aide de la propriété MSBuild `PackageVersion` :

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Empaquetez le projet pour un [framework cible](../../standard/frameworks.md) spécifique :

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Empaqueter le projet et utiliser un runtime spécifique (Windows 10) pour l’opération de restauration (SDK .NET Core 2.0 et versions ultérieures) :

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Empaquetez le projet à l’aide d’un [fichier .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec) :

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
