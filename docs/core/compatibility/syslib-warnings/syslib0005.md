---
title: AVERTISSEMENT SYSLIB0005
description: En savoir plus sur le obsoletion qui génère des SYSLIB0005 d’avertissement au moment de la compilation.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1263a4d327c735268f77ed56bdcea6a4cbed4bfa
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596527"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a>SYSLIB0005 : le Global Assembly Cache (GAC) n’est pas pris en charge

.NET Core et .NET 5,0 et versions ultérieures éliminent le concept de Global Assembly Cache (GAC) qui était présent dans .NET Framework. Pour aider les développeurs à s’éloigner de ces API, certaines API associées au GAC sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0005` au moment de la compilation.

Les API associées au GAC suivantes sont marquées comme obsolètes :

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  Les bibliothèques et les applications ne doivent pas utiliser l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> API pour effectuer des déterminations sur le comportement au moment de l’exécution, car elles sont toujours renvoyées `false` dans .net Core et .net 5 +.

## <a name="workarounds"></a>Solutions de contournement

Si votre application interroge la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété, envisagez de supprimer l’appel. Si vous utilisez la <xref:System.Reflection.Assembly.GlobalAssemblyCache> valeur pour choisir entre un « assembly dans le GAC » et un « assembly qui n’est pas dans le GAC » au moment de l’exécution, reconsidérez si le workflow a toujours un sens pour une application .net 5 +.

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [Global assembly cache](../../../framework/app-domains/gac.md)
