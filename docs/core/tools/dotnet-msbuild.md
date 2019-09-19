---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117704"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Résumé

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Description

La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.

La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour un projet de type SDK uniquement. Les options sont identiques. Pour plus d’informations sur les options disponibles, consultez [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`. `dotnet build` est généralement utilisée pour générer les projets, mais `dotnet msbuild` vous donne davantage de contrôle. Par exemple, si vous avez une cible spécifique que vous souhaitez exécuter (sans exécuter la cible build ), utilisez plutôt `dotnet msbuild`.

## <a name="examples"></a>Exemples

* Générer un projet et ses dépendances :

  ```dotnetcli
  dotnet msbuild
  ```

* Générer un projet et ses dépendances à l’aide de la configuration Release :

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :

  ```dotnetcli
  dotnet msbuild -pp
  ```
