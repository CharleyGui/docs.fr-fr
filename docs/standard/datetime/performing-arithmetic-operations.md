---
title: Exécution d’opérations arithmétiques avec des dates et heures
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET], arithmetic operations
- dates [.NET], arithmetic operations
- time zones [.NET], arithmetic operations
- arithmetic operations [.NET], dates and times
- dates [.NET], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: af294c45359f6226c4189aabb34fdfc670bbd1c9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817768"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Exécution d’opérations arithmétiques avec des dates et heures

Bien que les <xref:System.DateTime> structures et <xref:System.DateTimeOffset> fournissent des membres qui effectuent des opérations arithmétiques sur leurs valeurs, les résultats des opérations arithmétiques sont très différents. Cette rubrique examine ces différences, les met en relation avec les degrés de prise en charge des fuseaux horaires dans les données de date et d’heure, et explique comment effectuer des opérations qui prennent en charge les fuseaux horaires à l’aide de données de date et d’heure.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparaisons et opérations arithmétiques avec des valeurs DateTime

La <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriété permet à une <xref:System.DateTimeKind> valeur d’être assignée à la date et à l’heure pour indiquer si elle représente l’heure locale, le temps universel coordonné (UTC) ou l’heure dans un fuseau horaire non spécifié. Toutefois, ces informations limitées de fuseau horaire sont ignorées lors de la comparaison ou de l’exécution d’opérations arithmétiques de date et d’heure sur des <xref:System.DateTimeKind> valeurs. Ceci est illustré dans l’exemple suivant, qui compare l’heure locale actuelle à l’heure UTC actuelle.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

La <xref:System.DateTime.CompareTo%28System.DateTime%29> méthode signale que l’heure locale est antérieure (ou inférieure) à l’heure UTC, et l’opération de soustraction indique que la différence entre l’heure UTC et l’heure locale pour un système dans le fuseau horaire Pacifique (États-Unis) est de sept heures. Toutefois, étant donné que ces deux valeurs fournissent des représentations différentes d’un point unique dans le temps, il est clair dans ce cas que l’intervalle de temps est totalement attribuable au décalage du fuseau horaire local par rapport à l’heure UTC.

Plus généralement, la <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriété n’affecte pas les résultats retournés par les <xref:System.DateTime.Kind> méthodes de comparaison et arithmétiques (comme la comparaison de deux points identiques dans le temps indique), bien qu’elle puisse affecter l’interprétation de ces résultats. Par exemple :

- Le résultat de toute opération arithmétique exécutée sur deux valeurs de date et d’heure dont <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> les propriétés sont égales <xref:System.DateTimeKind> reflète l’intervalle de temps réel entre les deux valeurs. De même, la comparaison de deux valeurs de date et d’heure de ce type indique précisément la relation entre les heures.

- Le résultat de toute opération arithmétique ou de comparaison exécutée sur deux valeurs de date et d’heure dont <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> les propriétés sont égales <xref:System.DateTimeKind> ou sur deux valeurs de date et d’heure avec des <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> valeurs de propriété différentes reflète la différence de temps de l’horloge entre les deux valeurs.

- Les opérations arithmétiques ou de comparaison sur des valeurs de date et d’heure locales ne prennent pas en compte le fait qu’une valeur particulière soit ambiguë ou non valide, ni l’incidence de règles d’ajustement quelconques résultant du passage du fuseau horaire local à l’heure d’été ou à l’heure d’hiver.

- Toute opération qui compare ou calcule la différence entre l’heure UTC et une heure locale inclut dans le résultat un intervalle de temps égal au décalage du fuseau horaire local par rapport à l’heure UTC.

- Toute opération qui compare ou calcule la différence entre une heure non spécifiée et l’heure UTC ou l’heure locale reflète le temps horloge simple. Les décalages entre les fuseaux horaires ne sont pas pris en compte et le résultat ne reflète pas l’application des règles d’ajustement des fuseaux horaires.

- Toute opération qui compare ou calcule la différence entre deux heures non spécifiées peut inclure un intervalle inconnu qui reflète la différence d’heure entre deux fuseaux horaires différents.

Il existe de nombreux scénarios dans lesquels les différences entre les fuseaux horaires n’affectent pas les calculs de date et d’heure (pour en savoir plus, consultez [choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md)) ou dans lequel le contexte des données de date et d’heure définit la signification des opérations de comparaison ou arithmétiques.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparaisons et opérations arithmétiques avec des valeurs DateTimeOffset

Une <xref:System.DateTimeOffset> valeur comprend non seulement une date et une heure, mais également un décalage qui définit clairement cette date et cette heure par rapport à l’heure UTC. Cela permet de définir une égalité d’une manière quelque peu différente de celle des <xref:System.DateTimeOffset> valeurs. Alors que les <xref:System.DateTime> valeurs sont égales si elles ont la même valeur de date et d’heure, les <xref:System.DateTimeOffset> valeurs sont égales si elles font toutes les deux référence au même point dans le temps. Cela rend une <xref:System.DateTimeOffset> valeur plus précise et nécessite moins d’interprétation lorsqu’elle est utilisée dans les comparaisons et dans la plupart des opérations arithmétiques qui déterminent l’intervalle entre deux dates et heures. L’exemple suivant, qui est l' <xref:System.DateTimeOffset> équivalent de l’exemple précédent, qui comparait les valeurs locales et UTC <xref:System.DateTimeOffset> , illustre cette différence de comportement.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Dans cet exemple, la <xref:System.DateTimeOffset.CompareTo%2A> méthode indique que l’heure locale actuelle et l’heure UTC actuelle sont égales, et la soustraction des <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> valeurs indique que la différence entre les deux heures est <xref:System.TimeSpan.Zero?displayProperty=nameWithType> .

La principale limitation de l’utilisation de <xref:System.DateTimeOffset> valeurs dans les opérations arithmétiques de date et d’heure est que, bien que les <xref:System.DateTimeOffset> valeurs aient une prise en charge des fuseaux horaires, elles ne prennent pas complètement en charge les fuseaux horaires. Bien que le <xref:System.DateTimeOffset> décalage de la valeur reflète le décalage d’un fuseau horaire par rapport à l’heure UTC lorsqu’une <xref:System.DateTimeOffset> valeur est affectée pour la première fois à une variable, celle-ci est dissociée du fuseau horaire par la suite. Comme il n’est plus directement associé à une heure identifiable, l’addition et la soustraction d’intervalles de dates et d’heures ne prennent pas en compte les règles d’ajustement des fuseaux horaires.

À titre d’illustration, le passage à l’heure d’été dans le fuseau horaire du Centre des États-Unis se produit à 2:00 h 00 le 9 mars 2008. Cela signifie que l’ajout d’un intervalle de deux heures trente à l’heure de 1:30 dans le fuseau horaire du Centre des États-Unis, le 9 mars 2008, doit avoir pour résultat 5:00, le 9 mars 2008. Toutefois, comme le montre l’exemple suivant, le résultat de l’addition est 4:00, le 9 mars 2008. Notez que le résultat de cette opération représente le point correct dans le temps, bien qu’il ne s’agisse pas de l’heure dans le fuseau horaire qui nous intéresse (autrement dit, elle n’a pas le décalage de fuseau horaire attendu).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Opérations arithmétiques avec des heures dans des fuseaux horaires

La <xref:System.TimeZoneInfo> classe comprend un certain nombre de méthodes de conversion qui appliquent automatiquement des ajustements lorsqu’ils convertissent des heures d’un fuseau horaire à un autre. Elles sont associées aux limitations suivantes :

- Les <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> méthodes et, qui convertissent des heures entre deux fuseaux horaires quelconques.

- Les <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> méthodes et, qui convertissent l’heure d’un fuseau horaire particulier en heure UTC, ou convertient l’heure UTC en heure d’un fuseau horaire particulier.

Pour plus d’informations, consultez [conversion d’heures entre fuseaux horaires](converting-between-time-zones.md).

La <xref:System.TimeZoneInfo> classe ne fournit pas de méthodes qui appliquent automatiquement des règles d’ajustement lorsque vous effectuez des opérations arithmétiques de date et d’heure. Toutefois, vous pouvez convertir l’heure d’un fuseau horaire en heure UTC, effectuer l’opération arithmétique, puis reconvertir l’heure UTC dans l’heure du fuseau horaire. Pour plus d’informations, consultez [Comment : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md).

Par exemple, le code suivant est semblable au code précédent qui ajoutait deux heures trente à 2:00, le 9 mars 2008. Toutefois, comme il convertit l’heure du Centre des États-Unis en heure UTC avant d’effectuer les opérations arithmétiques de date et d’heure, puis reconvertit le résultat UTC en heure du Centre, l’heure résultante reflète le passage du fuseau horaire du Centre des États-Unis à l’heure d’été.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
- [Procédure : utiliser des fuseaux horaires en arithmétique de date et heure](use-time-zones-in-arithmetic.md)
