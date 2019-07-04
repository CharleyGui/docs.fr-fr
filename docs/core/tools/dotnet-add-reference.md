---
title: Commande dotnet-add reference
description: La commande dotnet add reference est une option pratique pour ajouter des références entre projets.
ms.date: 06/26/2019
ms.openlocfilehash: 6e0ca40e701b62dcc18147f9de83cafa6aa2f50f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422003"
---
# <a name="dotnet-add-reference"></a>dotnet-add reference

**Cet article s’applique à : ✓** SDK .NET Core 1.x et ultérieur

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add reference` : ajoute des références entre projets (P2P).

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Description

La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet. Une fois que vous avez exécuté la commande, les éléments [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) sont ajoutés au fichier projet.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

* **`PROJECT_REFERENCES`**

  Références entre projets (P2P) à ajouter. Spécifiez un ou plusieurs projets. Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.

## <a name="options"></a>Options

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`-f|--framework <FRAMEWORK>`**

  Ajoute des références de projet uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.

* **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple). Option disponible à partir du kit SDK .NET Core 3.0.

## <a name="examples"></a>Exemples

* Ajouter une référence de projet :

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Ajouter plusieurs références de projet au projet dans le répertoire actuel :

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
