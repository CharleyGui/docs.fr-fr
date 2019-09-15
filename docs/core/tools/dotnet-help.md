---
title: Commande dotnet help
description: La commande dotnet help affiche une documentation en ligne plus détaillée pour la commande spécifiée.
ms.date: 08/08/2019
ms.openlocfilehash: e76f858f2529afc50646473f1aab9d52730cff16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990461"
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

  ```console
  dotnet help new
  ```
