---
title: commande d’exécution de l’outil dotnet
description: La commande d’exécution de l’outil dotnet appelle un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: 116ecb61748a0ca70ed385b279b11b939748f4a8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634153"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool run` -Appelle un outil local.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a>Description

La `dotnet tool run` commande recherche les fichiers de manifeste de l’outil qui sont dans la portée du répertoire actif. Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil. Pour plus d’informations, consultez [appeler un outil local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Arguments

- **`COMMAND_NAME`**

  Nom de commande de l’outil à exécuter.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="example"></a>Exemple

- **`dotnet tool run dotnetsay`**

  Exécute l' `dotnetsay` outil local.

## <a name="see-also"></a>Voir aussi

- [Outils .NET](global-tools.md)
- [Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET](local-tools-how-to-use.md)
