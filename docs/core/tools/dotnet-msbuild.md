---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503678"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Synopsis

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Description

La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.

La commande a exactement les mêmes capacités que le client de ligne de commande MSBuild existant pour les projets de style SDK seulement. Les options sont identiques. Pour plus d’informations sur les options disponibles, consultez la [référence MSBuild de la ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference).

La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`. [la construction de dotnet](dotnet-build.md) est plus couramment utilisée pour la construction `dotnet msbuild` de projets, mais parce qu’elle exécute toujours la cible de construction, vous pouvez utiliser lorsque vous ne voulez pas construire le projet. Par exemple, si vous avez une cible spécifique que `dotnet msbuild` vous souhaitez exécuter sans construire le projet, utilisez et spécifiez la cible.

## <a name="examples"></a>Exemples

- Générer un projet et ses dépendances :

  ```dotnetcli
  dotnet msbuild
  ```

- Générer un projet et ses dépendances à l’aide de la configuration Release :

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
