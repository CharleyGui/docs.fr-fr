---
title: 'Procédure : résoudre des heures ambiguës'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 467153ad1217e529f52bf90262c4264de069ff00
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063519"
---
# <a name="how-to-resolve-ambiguous-times"></a>Procédure : résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

- Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.

- Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

Cette rubrique montre comment résoudre une heure ambiguë en supposant qu’elle représente l’heure d’hiver du fuseau horaire.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire

1. Appelez la <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.

2. Si l’heure est ambiguë, soustraire l’heure de l' <xref:System.TimeSpan> objet retourné par la propriété du fuseau horaire <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .

3. Appelez la `static` `Shared` méthode (en Visual Basic .net) <xref:System.DateTime.SpecifyKind%2A> pour affecter à la propriété de la valeur de date et d’heure UTC la valeur <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="example"></a>Exemple

L’exemple suivant montre comment convertir une heure ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

L’exemple se compose d’une méthode nommée `ResolveAmbiguousTime` qui détermine si la <xref:System.DateTime> valeur qui lui est passée est ambiguë. Si la valeur est ambiguë, la méthode retourne une <xref:System.DateTime> valeur qui représente l’heure UTC correspondante. La méthode gère cette conversion en soustrayant la valeur de la propriété du fuseau horaire local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> de l’heure locale.

En règle générale, une heure ambiguë est gérée en appelant la <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> méthode pour récupérer un tableau d' <xref:System.TimeSpan> objets qui contiennent les décalages UTC possibles de l’heure ambiguë. Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire. La <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.

Dans cet exemple, toutes les références au fuseau horaire local sont effectuées par le biais de la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété ; le fuseau horaire local n’est jamais assigné à une variable objet. Il s’agit d’une pratique recommandée, car un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> méthode invalide tous les objets auxquels le fuseau horaire local est assigné.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que l' <xref:System> espace de noms soit importé avec l' `using` instruction (obligatoire dans le code C#).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
- [Comment : permettre aux utilisateurs de résoudre des heures ambiguës](let-users-resolve-ambiguous-times.md)
