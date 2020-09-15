---
title: Modifications importantes de l’analyse du code
description: Répertorie les modifications avec rupture dans les analyseurs de code source .NET.
ms.date: 09/02/2020
ms.openlocfilehash: 20badd69b316e1d87700b3c5061a71d648b71c64
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065154"
---
# <a name="code-analysis-breaking-changes"></a>Modifications importantes de l’analyse du code

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [CA1416 : compatibilité de la plateforme](#ca1416-platform-compatibility) | 5.0 |
| [Ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke](#ca1417-outattribute-on-string-parameter-for-pinvoke) | 5.0 |
| [CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour la chaîne](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | 5.0 |
| [CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur](#ca2013-do-not-use-referenceequals-with-value-types) | 5.0 |
| [CA2014 : Ne pas utiliser stackalloc dans les boucles](#ca2014-do-not-use-stackalloc-in-loops) | 5.0 |
| [Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager\<T>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5.0 |
| [CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
