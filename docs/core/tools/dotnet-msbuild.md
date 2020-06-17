---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803174"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Name

`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances. Remarque : vous devrez peut-être spécifier un fichier solution ou projet s’il en existe plusieurs.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>Description

La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.

La commande a exactement les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour les projets de style SDK uniquement. Les options sont identiques. Pour plus d’informations sur les options disponibles, consultez la page de référence de la [ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore`. Lorsque vous ne souhaitez pas générer le projet et que vous avez une cible spécifique que vous souhaitez exécuter, utilisez `dotnet build` ou `dotnet msbuild` et spécifiez la cible.

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
  dotnet msbuild -preprocess:<fileName>.xml
  ```
