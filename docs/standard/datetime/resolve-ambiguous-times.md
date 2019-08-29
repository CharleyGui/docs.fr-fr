---
title: 'Procédure : résoudre des heures ambiguës'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106783"
---
# <a name="how-to-resolve-ambiguous-times"></a>Procédure : résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit quand l’heure de l’horloge est retardée, comme lors du passage de l’heure d’été à l'heure d'hiver dans un fuseau horaire. Quand vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

- Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée à l'heure d’hiver du fuseau horaire.

- Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

Cette rubrique montre comment résoudre une heure ambiguë en supposant qu’elle représente l’heure d’hiver du fuseau horaire.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire

1. Appelez la <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.

2. Si l’heure est ambiguë, soustraire l’heure de <xref:System.TimeSpan> l’objet retourné par la propriété du <xref:System.TimeZoneInfo.BaseUtcOffset%2A> fuseau horaire.

3. Appelez la `static` méthode`Shared` (en Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A> ) pour affecter à <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>la propriété de <xref:System.DateTime.Kind%2A> la valeur de date et d’heure UTC la valeur.

## <a name="example"></a>Exemple

L’exemple suivant montre comment convertir une heure ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

L’exemple se compose d’une méthode `ResolveAmbiguousTime` nommée qui détermine si <xref:System.DateTime> la valeur qui lui est passée est ambiguë. Si la valeur est ambiguë, la méthode retourne une <xref:System.DateTime> valeur qui représente l’heure UTC correspondante. La méthode gère cette conversion en soustrayant la valeur de la propriété du <xref:System.TimeZoneInfo.BaseUtcOffset%2A> fuseau horaire local de l’heure locale.

En règle générale, une heure ambiguë est gérée en <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> appelant la méthode pour récupérer un <xref:System.TimeSpan> tableau d’objets qui contiennent les décalages UTC possibles de l’heure ambiguë. Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire. La <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.

Dans cet exemple, toutes les références au fuseau horaire local sont faites par le biais de la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; le fuseau horaire local n’est jamais affecté à une variable objet. Cette pratique est recommandée, car un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> invalide tous les objets auxquels le fuseau horaire est affecté.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que l'espace de noms <xref:System> soit importé avec l'instruction `using` (obligatoire en C#).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Guide pratique pour Permettre aux utilisateurs de résoudre des heures ambiguës](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
