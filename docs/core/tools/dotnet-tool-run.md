---
title: commande d’exécution d’outil de dotnet
description: La commande d’exécution d’outil de dotnet invoque un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847844"
---
# <a name="dotnet-tool-run"></a>dotnet outil exécuter

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet tool run`- Invoque un outil local.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a>Description

L’outil `dotnet tool run` de recherche de commande manifeste les fichiers qui sont en portée pour l’annuaire actuel. Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil. Pour plus d’informations, voir [Invoquez un outil local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Arguments

- **`COMMAND_NAME`**

  Le nom de commande de l’outil à exécuter.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="example"></a> Exemple

- **`dotnet tool run dotnetsay`**

  Exécute `dotnetsay` l’outil local.

## <a name="see-also"></a>Voir aussi

- [.NET Outils de base](global-tools.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
