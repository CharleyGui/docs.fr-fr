---
title: Commande dotnet help
description: La commande dotnet help affiche une documentation en ligne plus détaillée pour la commande spécifiée.
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117713"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

**Cet article s’applique à : ✓** .net Core 2,0 SDK et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Name

`dotnet help` : affiche une documentation en ligne plus détaillée pour la commande spécifiée.

## <a name="synopsis"></a>Résumé

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet help` ouvre la page de référence sur docs.microsoft.com pour afficher des informations plus détaillées sur la commande spécifiée.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  Nom de la commande CLI .NET Core. Pour obtenir la liste des commandes CLI valides, consultez [Commandes CLI](index.md#cli-commands).

## <a name="options"></a>Options

* **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

* Ouvre la page de documentation de la commande [dotnet new](dotnet-new.md) :

  ```dotnetcli
  dotnet help new
  ```
