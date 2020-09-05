---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497565"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;.TryPeek peut retourner une valeur Null erronée via son paramètre de sortie

#### <a name="details"></a>Détails

Dans certains scénarios multithreads, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> peut retourner la valeur true, mais renseigner le paramètre de sortie avec la valeur Null (au lieu de la valeur correcte).

#### <a name="suggestion"></a>Suggestion

Ce problème a été résolu dans le .NET Framework 4.5.1. Pour résoudre votre problème, effectuez une mise niveau vers le .NET Framework 4.5.1.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->
