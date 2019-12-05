---
title: Paramètres de configuration de compilation
description: En savoir plus sur les paramètres d’exécution qui configurent le fonctionnement du compilateur JIT pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802819"
---
# <a name="run-time-configuration-options-for-compilation"></a>Options de configuration au moment de l’exécution pour la compilation

## <a name="tiered-compilation"></a>Compilation hiérarchisée

- Configure si le compilateur JIT utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).
- Dans .NET Core 3,0 et versions ultérieures, la compilation à plusieurs niveaux est activée par défaut.
- Dans .NET Core 2,1 et 2,2, la compilation à plusieurs niveaux est désactivée par défaut.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | activé `true`<br/>`false`-désactivé |
| **Variable d'environnement** | `COMPlus_TieredCompilation` | activé `1`<br/>`0`-désactivé |
