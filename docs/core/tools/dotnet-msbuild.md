---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733200"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Résumé

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Description

La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.

La commande a exactement les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour les projets de style SDK uniquement. Les options sont identiques. Pour plus d’informations sur les options disponibles, consultez la page de référence de la [ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`. la [génération dotnet](dotnet-build.md) est plus couramment utilisée pour générer des projets, mais parce qu’elle exécute toujours la cible Build, vous pouvez utiliser `dotnet msbuild` lorsque vous ne voulez pas générer le projet. Par exemple, si vous avez une cible spécifique que vous souhaitez exécuter sans générer le projet, utilisez `dotnet msbuild` et spécifiez la cible.

## <a name="examples"></a>Exemples

* Générer un projet et ses dépendances :

  ```dotnetcli
  dotnet msbuild
  ```

* Générer un projet et ses dépendances à l’aide de la configuration Release :

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
