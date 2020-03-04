---
title: commande d’exécution de l’outil dotnet
description: La commande d’exécution de l’outil dotnet appelle un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156957"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="name"></a>Nom

`dotnet tool run` : appelle un outil local.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool run` recherche les fichiers de manifeste de l’outil qui se trouvent dans la portée du répertoire actif. Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil. Pour plus d’informations, consultez [appeler un outil local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Arguments

- **`COMMAND_NAME`**

  Nom de commande de l’outil à exécuter.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="example"></a>Exemple

- **`dotnet tool run dotnetsay`**

  Exécute l’outil local `dotnetsay`.

## <a name="see-also"></a>Voir aussi

- [Outils .NET Core](global-tools.md)
