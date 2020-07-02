---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617217"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>List&lt;T&gt;.ForEach peut lever une exception quand vous modifiez un élément de la liste

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, un énumérateur <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> lève une exception <xref:System.InvalidOperationException?displayProperty=fullName> si un élément de la collection appelante est modifié. Avant, il ne levait pas d’exception, mais pouvait entraîner des conditions de concurrence.

#### <a name="suggestion"></a>Suggestion

Dans l’idéal, le code doit être corrigé de manière à ne pas modifier les listes pendant l’énumération de leurs éléments, car cela n’est jamais une opération sûre. Cependant, pour restaurer le comportement précédent, une application peut cibler .NET Framework 4.0.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
