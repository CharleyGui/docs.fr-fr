---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622051"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;.TryPeek peut retourner une valeur Null erronée via son paramètre de sortie

#### <a name="details"></a>Détails

Dans certains scénarios multithreads, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> peut retourner la valeur true, mais renseigner le paramètre de sortie avec la valeur Null (au lieu de la valeur correcte).

#### <a name="suggestion"></a>Suggestion

Ce problème a été résolu dans le .NET Framework 4.5.1. Pour résoudre votre problème, effectuez une mise niveau vers le .NET Framework 4.5.1.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
