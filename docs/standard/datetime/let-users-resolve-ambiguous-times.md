---
title: 'Comment : permettre aux utilisateurs de résoudre des heures ambiguës'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122277"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Comment : permettre aux utilisateurs de résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

- Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

- Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.

Cette rubrique montre comment permettre à un utilisateur de résoudre une heure ambiguë.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Pour permettre à un utilisateur de résoudre une heure ambiguë

1. Obtenez la date et l’heure entrées par l’utilisateur.

2. Appelez la méthode <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> pour déterminer si l’heure est ambiguë.

3. Si l’heure est ambiguë, appelez la méthode <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pour récupérer un tableau d’objets <xref:System.TimeSpan>. Chaque élément du tableau contient un décalage UTC auquel l’heure ambiguë peut être mappée.

4. Laissez l’utilisateur sélectionner le décalage souhaité.

5. Obtenez la date et l’heure UTC en soustrayant de l’heure locale le décalage sélectionné par l’utilisateur.

6. Appelez la méthode `static` (`Shared` dans Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> pour définir la propriété <xref:System.DateTime.Kind%2A> de la valeur de date et d’heure UTC sur <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L’exemple suivant invite l’utilisateur à entrer une date et une heure et, si cette dernière est ambiguë, permet à l’utilisateur de sélectionner l’heure UTC à laquelle l’heure ambiguë correspond.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Le cœur de l’exemple de code utilise un tableau d’objets <xref:System.TimeSpan> pour indiquer les décalages possibles de l’heure ambiguë par rapport à l’heure UTC. Toutefois, ces décalages ne seront probablement pas significatifs pour l’utilisateur. Pour clarifier leur signification, le code note également si un décalage représente l’heure d’hiver du fuseau horaire local ou son heure d’été. Le code détermine l’heure standard et l’heure d’été en comparant le décalage avec la valeur de la propriété <xref:System.TimeZoneInfo.BaseUtcOffset%2A>. Cette propriété indique la différence entre l’heure UTC et l’heure d’hiver du fuseau horaire.

Dans cet exemple, toutes les références au fuseau horaire local sont effectuées via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; le fuseau horaire local n’est jamais assigné à une variable objet. Il s’agit d’une pratique recommandée, car un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> invalide tous les objets auxquels le fuseau horaire local est assigné.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- L’importation de l’espace de noms <xref:System> avec l’instruction `using` ( C# obligatoire dans le code).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Guide pratique pour résoudre des heures ambiguës](../../../docs/standard/datetime/resolve-ambiguous-times.md)
