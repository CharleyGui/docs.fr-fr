---
title: dotnet ajouter la commande de référence
description: La commande dotnet add reference est une option pratique pour ajouter des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503791"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

`dotnet add reference` : ajoute des références entre projets (P2P).

## <a name="synopsis"></a>Synopsis

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Description

La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet. Une fois que vous avez exécuté la commande, les éléments `<ProjectReference>` sont ajoutés au fichier projet.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

- **`PROJECT`**

  Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

- **`PROJECT_REFERENCES`**

  Références entre projets (P2P) à ajouter. Spécifiez un ou plusieurs projets. Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`-f|--framework <FRAMEWORK>`**

  Ajoute des références de projet seulement lors du ciblage d’un [cadre](../../standard/frameworks.md)spécifique .

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple). Option disponible à partir du kit SDK .NET Core 3.0.

## <a name="examples"></a>Exemples

- Ajouter une référence de projet :

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Ajouter plusieurs références de projet au projet dans le répertoire actuel :

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
