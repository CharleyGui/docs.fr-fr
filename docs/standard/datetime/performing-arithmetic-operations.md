---
title: Exécution d’opérations arithmétiques avec des dates et heures
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01314c160fc531f5c97a1369c8444dce7f590d53
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106616"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Exécution d’opérations arithmétiques avec des dates et heures

Bien que les <xref:System.DateTime> <xref:System.DateTimeOffset> structures et fournissent des membres qui effectuent des opérations arithmétiques sur leurs valeurs, les résultats des opérations arithmétiques sont très différents. Cette rubrique examine ces différences, les met en relation avec les degrés de prise en charge des fuseaux horaires dans les données de date et d’heure, et explique comment effectuer des opérations qui prennent en charge les fuseaux horaires à l’aide de données de date et d’heure.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparaisons et opérations arithmétiques avec des valeurs DateTime

La <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriété permet à <xref:System.DateTimeKind> une valeur d’être assignée à la date et à l’heure pour indiquer si elle représente l’heure locale, le temps universel coordonné (UTC) ou l’heure dans un fuseau horaire non spécifié. Toutefois, ces informations limitées de fuseau horaire sont ignorées lors de la comparaison ou de l' <xref:System.DateTimeKind> exécution d’opérations arithmétiques de date et d’heure sur des valeurs. Ceci est illustré dans l’exemple suivant, qui compare l’heure locale actuelle à l’heure UTC actuelle.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

La <xref:System.DateTime.CompareTo%28System.DateTime%29> méthode signale que l’heure locale est antérieure (ou inférieure) à l’heure UTC, et que l’opération de soustraction indique que la différence entre l’heure UTC et l’heure locale pour un système dans le fuseau horaire du Pacifique est de sept heures. Toutefois, comme ces deux valeurs donnent des représentations différentes d’un même point dans le temps, il apparaît clairement dans ce cas que cet intervalle de temps est totalement attribuable au décalage du fuseau horaire local par rapport à l’heure UTC.

Plus généralement, la <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriété n’affecte pas les résultats retournés par <xref:System.DateTime.Kind> les méthodes de comparaison et arithmétiques (comme la comparaison de deux points identiques dans le temps indique), bien qu’elle puisse affecter l’interprétation de ces résultats. Par exemple :

- Le résultat de toute opération arithmétique exécutée sur deux valeurs de date et <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> d’heure dont <xref:System.DateTimeKind> les propriétés sont égales reflète l’intervalle de temps réel entre les deux valeurs. De même, la comparaison de deux valeurs de date et d’heure de ce type indique précisément la relation entre les heures.

- Le résultat de toute opération arithmétique ou de comparaison exécutée sur deux valeurs de date <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> et d’heure <xref:System.DateTimeKind> dont les propriétés sont égales ou sur deux <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> valeurs de date et d’heure avec des valeurs de propriété différentes reflète la différence de temps horloge entre les deux valeurs.

- Les opérations arithmétiques ou de comparaison sur des valeurs de date et d’heure locales ne prennent pas en compte le fait qu’une valeur particulière soit ambiguë ou non valide, ni l’incidence de règles d’ajustement quelconques résultant du passage du fuseau horaire local à l’heure d’été ou à l’heure d’hiver.

- Toute opération qui compare ou calcule la différence entre l’heure UTC et une heure locale inclut dans le résultat un intervalle de temps égal au décalage du fuseau horaire local par rapport à l’heure UTC.

- Toute opération qui compare ou calcule la différence entre une heure non spécifiée et l’heure UTC ou l’heure locale reflète le temps horloge simple. Les décalages entre les fuseaux horaires ne sont pas pris en compte et le résultat ne reflète pas l’application des règles d’ajustement des fuseaux horaires.

- Toute opération qui compare ou calcule la différence entre deux heures non spécifiées peut inclure un intervalle inconnu qui reflète la différence d’heure entre deux fuseaux horaires différents.

Il existe de nombreux scénarios dans lesquels les différences entre les fuseaux horaires n’affectent pas les calculs de date et d’heure (pour en savoir plus, consultez [choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) ou dans quel contexte les données de date et d’heure définit la signification des opérations arithmétiques ou de comparaison.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparaisons et opérations arithmétiques avec des valeurs DateTimeOffset

Une <xref:System.DateTimeOffset> valeur comprend non seulement une date et une heure, mais également un décalage qui définit clairement cette date et cette heure par rapport à l’heure UTC. Cela permet de définir une égalité d’une manière quelque peu <xref:System.DateTimeOffset> différente de celle des valeurs. Alors <xref:System.DateTime> que les valeurs sont égales si elles ont la même valeur de <xref:System.DateTimeOffset> date et d’heure, les valeurs sont égales si elles font toutes les deux référence au même point dans le temps. Cela rend une <xref:System.DateTimeOffset> valeur plus précise et nécessite moins d’interprétation lorsqu’elle est utilisée dans les comparaisons et dans la plupart des opérations arithmétiques qui déterminent l’intervalle entre deux dates et heures. L’exemple suivant, qui est l' <xref:System.DateTimeOffset> équivalent de l’exemple précédent, qui comparait les <xref:System.DateTimeOffset> valeurs locales et UTC, illustre cette différence de comportement.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Dans cet exemple, la <xref:System.DateTimeOffset.CompareTo%2A> méthode indique que l’heure locale actuelle et l’heure UTC actuelle sont égales, et la soustraction des <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> valeurs indique que la différence entre les deux <xref:System.TimeSpan.Zero?displayProperty=nameWithType>heures est.

La principale limitation de l' <xref:System.DateTimeOffset> utilisation de valeurs dans les opérations arithmétiques de <xref:System.DateTimeOffset> date et d’heure est que, bien que les valeurs aient une prise en charge des fuseaux horaires, elles ne prennent pas complètement en charge les fuseaux horaires. Bien que <xref:System.DateTimeOffset> le décalage de la valeur reflète le décalage d’un fuseau horaire par <xref:System.DateTimeOffset> rapport à l’heure UTC lorsqu’une valeur est affectée pour la première fois à une variable, celle-ci est dissociée du fuseau horaire par la suite. Comme il n’est plus directement associé à une heure identifiable, l’addition et la soustraction d’intervalles de dates et d’heures ne prennent pas en compte les règles d’ajustement des fuseaux horaires.

Pour illustrer cela, la passage à l’heure d’été dans le fuseau horaire du Centre (États-Unis) se produit à 2:00, le 9 mars 2008. Cela signifie que l’ajout d’un intervalle de deux heures trente à l’heure de 1:30 dans le fuseau horaire du Centre des États-Unis, le 9 mars 2008, doit avoir pour résultat 5:00, le 9 mars 2008. Toutefois, comme le montre l’exemple suivant, le résultat de l’addition est 4:00, le 9 mars 2008. Notez que le résultat de cette opération représente l’heure correcte, même s’il ne s’agit pas de l’heure dans le fuseau horaire qui nous intéresse (autrement dit, elle n’a pas le décalage horaire attendu).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Opérations arithmétiques avec des heures dans des fuseaux horaires

La <xref:System.TimeZoneInfo> classe comprend un certain nombre de méthodes de conversion qui appliquent automatiquement des ajustements lorsqu’ils convertissent des heures d’un fuseau horaire à un autre. Notamment :

- Les <xref:System.TimeZoneInfo.ConvertTime%2A> méthodes <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> et, qui convertissent des heures entre deux fuseaux horaires quelconques.

- Les <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> méthodes <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> et, qui convertissent l’heure d’un fuseau horaire particulier en heure UTC, ou convertient l’heure UTC en heure d’un fuseau horaire particulier.

Pour plus d’informations, consultez [conversion d’heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md).

La <xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> classe ne fournit pas de méthodes qui appliquent automatiquement des règles d’ajustement lorsque vous effectuez des opérations arithmétiques de date et d’heure. Toutefois, vous pouvez convertir l’heure d’un fuseau horaire en heure UTC, effectuer l’opération arithmétique, puis reconvertir l’heure UTC dans l’heure du fuseau horaire. Pour plus d’informations, consultez [Guide pratique pour Utilisez des fuseaux horaires dans des opérations](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)arithmétiques de date et d’heure.

Par exemple, le code suivant est semblable au code précédent qui ajoutait deux heures trente à 2:00, le 9 mars 2008. Toutefois, comme il convertit l’heure du Centre des États-Unis en heure UTC avant d’effectuer les opérations arithmétiques de date et d’heure, puis reconvertit le résultat UTC en heure du Centre, l’heure résultante reflète le passage du fuseau horaire du Centre des États-Unis à l’heure d’été.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Guide pratique : Utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
