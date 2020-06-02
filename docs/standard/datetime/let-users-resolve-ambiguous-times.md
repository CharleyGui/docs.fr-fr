---
title: 'Comment : permettre aux utilisateurs de résoudre des heures ambiguës'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: ac723738d80a2f686a5fcaf279cec791b3c58619
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281581"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Comment : permettre aux utilisateurs de résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

- Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

- Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.

Cette rubrique montre comment permettre à un utilisateur de résoudre une heure ambiguë.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Pour permettre à un utilisateur de résoudre une heure ambiguë

1. Obtenez la date et l’heure entrées par l’utilisateur.

2. Appelez la <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.

3. Si l’heure est ambiguë, appelez la <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> méthode pour récupérer un tableau d' <xref:System.TimeSpan> objets. Chaque élément du tableau contient un décalage UTC auquel l’heure ambiguë peut être mappée.

4. Laissez l’utilisateur sélectionner le décalage souhaité.

5. Obtenez la date et l’heure UTC en soustrayant de l’heure locale le décalage sélectionné par l’utilisateur.

6. Appelez la `static` `Shared` méthode (en Visual Basic .net) <xref:System.DateTime.SpecifyKind%2A> pour affecter à la propriété de la valeur de date et d’heure UTC la valeur <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="example"></a>Exemple

L’exemple suivant invite l’utilisateur à entrer une date et une heure et, si cette dernière est ambiguë, permet à l’utilisateur de sélectionner l’heure UTC à laquelle l’heure ambiguë correspond.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Le cœur de l’exemple de code utilise un tableau d' <xref:System.TimeSpan> objets pour indiquer les décalages possibles de l’heure ambiguë par rapport à l’heure UTC. Toutefois, ces décalages ne seront probablement pas significatifs pour l’utilisateur. Pour clarifier leur signification, le code note également si un décalage représente l’heure d’hiver du fuseau horaire local ou son heure d’été. Le code détermine l’heure standard et l’heure d’été en comparant le décalage avec la valeur de la <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété. Cette propriété indique la différence entre l’heure UTC et l’heure d’hiver du fuseau horaire.

Dans cet exemple, toutes les références au fuseau horaire local sont effectuées par le biais de la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété ; le fuseau horaire local n’est jamais assigné à une variable objet. Il s’agit d’une pratique recommandée, car un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> méthode invalide tous les objets auxquels le fuseau horaire local est assigné.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que l' <xref:System> espace de noms soit importé avec l' `using` instruction (obligatoire dans le code C#).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
- [Comment : résoudre des heures ambiguës](resolve-ambiguous-times.md)
