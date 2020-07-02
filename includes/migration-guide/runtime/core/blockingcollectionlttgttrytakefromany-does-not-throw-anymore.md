---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619950"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a>BlockingCollection&lt;T&gt;.TryTakeFromAny ne lève plus d’exceptions

#### <a name="details"></a>Détails

Si l’une des collections d’entrée est marquée comme terminée, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> ne retourne plus -1, et <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> ne lève plus d’exceptions. Cette modification permet d'utiliser des collections lorsque l'une est vide ou terminée, alors que l'autre comporte toujours des éléments pouvant être récupérés.

#### <a name="suggestion"></a>Suggestion

Si vous utilisiez TryTakeFromAny pour retourner -1 ou TakeFromAny pour lever des exceptions à des fins de flux de contrôle, dans le contexte d’une collection bloquante terminée, ce code doit à présent être modifié pour utiliser <code>.Any(b =&gt; b.IsCompleted)</code> de manière à détecter cette condition.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|
