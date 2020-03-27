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
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344166"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Exécution d’opérations arithmétiques avec des dates et heures

Bien que <xref:System.DateTime> les <xref:System.DateTimeOffset> structures et les structures fournissent des membres qui effectuent des opérations d’arithmétique sur leurs valeurs, les résultats des opérations arithmétiques sont très différents. Ce sujet examine ces différences, les relie à des degrés de sensibilisation au fuseau horaire dans les données sur les dates et les délais, et discute de la façon d’effectuer des opérations pleinement chronoistiques en utilisant des données sur la date et l’heure.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparaisons et opérations arithmétiques avec les valeurs DateTime

La <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriété <xref:System.DateTimeKind> permet d’attribuer une valeur à la date et à l’heure pour indiquer si elle représente l’heure locale, l’heure universelle coordonnée (UTC), ou l’heure dans un fuseau horaire non spécifié. Toutefois, ces informations limitées sur les fuseaus horaires sont <xref:System.DateTimeKind> ignorées lorsqu’elles comparent ou exécutent l’arithmétique des dates et de l’heure sur les valeurs. Ceci est illustré dans l’exemple suivant, qui compare l’heure locale actuelle à l’heure UTC actuelle.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

La <xref:System.DateTime.CompareTo%28System.DateTime%29> méthode indique que l’heure locale est plus tôt que (ou moins que) l’heure UTC, et l’opération de soustraction indique que la différence entre UTC et l’heure locale pour un système dans le zone horaire standard du Pacifique des États-Unis est de sept heures. Mais comme ces deux valeurs fournissent des représentations différentes d’un seul point dans le temps, il est clair dans ce cas que l’intervalle de temps est complètement attribuable à la compensation du fuseau horaire local de l’UTC.

Plus généralement, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> la propriété n’affecte <xref:System.DateTime.Kind> pas les résultats retournés par comparaison et les méthodes arithmétiques (comme la comparaison de deux points identiques dans le temps l’indique), bien qu’elle puisse affecter l’interprétation de ces résultats. Par exemple :

- Le résultat de toute opération arithmétique effectuée <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> sur deux <xref:System.DateTimeKind> valeurs de date et d’heure dont les propriétés sont égales reflète l’intervalle de temps réel entre les deux valeurs. De même, la comparaison de deux valeurs de date et d’heure de ce type indique précisément la relation entre les heures.

- Le résultat de toute opération arithmétique ou de <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> comparaison effectuée <xref:System.DateTimeKind> sur deux valeurs de <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> date et d’heure dont les propriétés égales ou à deux valeurs de date et d’heure avec des valeurs de propriété différentes reflètent la différence de temps d’horloge entre les deux valeurs.

- Les opérations arithmétiques ou de comparaison sur des valeurs de date et d’heure locales ne prennent pas en compte le fait qu’une valeur particulière soit ambiguë ou non valide, ni l’incidence de règles d’ajustement quelconques résultant du passage du fuseau horaire local à l’heure d’été ou à l’heure d’hiver.

- Toute opération qui compare ou calcule la différence entre l’heure UTC et une heure locale inclut dans le résultat un intervalle de temps égal au décalage du fuseau horaire local par rapport à l’heure UTC.

- Toute opération qui compare ou calcule la différence entre une heure non spécifiée et l’heure UTC ou l’heure locale reflète le temps horloge simple. Les décalages entre les fuseaux horaires ne sont pas pris en compte et le résultat ne reflète pas l’application des règles d’ajustement des fuseaux horaires.

- Toute opération qui compare ou calcule la différence entre deux heures non spécifiées peut inclure un intervalle inconnu qui reflète la différence d’heure entre deux fuseaux horaires différents.

Il existe de nombreux scénarios dans lesquels les différences de fuseau horaire n’affectent pas les calculs de date et d’heure (pour une discussion de certains d’entre eux, voir [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) ou dans lequel le contexte des données de date et d’heure définit le sens de comparaison ou les opérations arithmétiques.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparaisons et opérations arithmétiques avec les valeurs DateTimeOffset

Une <xref:System.DateTimeOffset> valeur comprend non seulement une date et une heure, mais aussi un décalage qui définit sans ambiguïté cette date et cette heure par rapport à UTC. Cela permet de définir l’égalité <xref:System.DateTimeOffset> quelque peu différemment des valeurs. Alors <xref:System.DateTime> que les valeurs sont égales si <xref:System.DateTimeOffset> elles ont la même date et la même valeur de temps, les valeurs sont égales si elles se réfèrent toutes les deux au même point dans le temps. Cela rend <xref:System.DateTimeOffset> une valeur plus précise et moins besoin d’interprétation lorsqu’elle est utilisée en comparaisons et dans la plupart des opérations arithmétiques qui déterminent l’intervalle entre deux dates et heures. L’exemple suivant, <xref:System.DateTimeOffset> qui est l’équivalent de l’exemple précédent qui comparait les valeurs locales et UTC, <xref:System.DateTimeOffset> illustre cette différence de comportement.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Dans cet exemple, la <xref:System.DateTimeOffset.CompareTo%2A> méthode indique que l’heure locale actuelle et l’heure UTC actuelle sont égales, et la soustraction des <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> valeurs indique que la différence entre les deux fois est <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

La principale limite <xref:System.DateTimeOffset> de l’utilisation des valeurs dans <xref:System.DateTimeOffset> l’arithmétique des dates et des temps est que, bien que les valeurs aient une certaine connaissance du fuseau horaire, elles ne sont pas pleinement conscientes du fuseau horaire. Bien <xref:System.DateTimeOffset> que le décalage de la valeur reflète le <xref:System.DateTimeOffset> décalage d’un fuseau horaire de l’UTC lorsqu’une variable est d’abord attribuée à une valeur, elle se dissocie du fuseau horaire par la suite. Comme il n’est plus directement associé à une heure identifiable, l’addition et la soustraction d’intervalles de dates et d’heures ne prennent pas en compte les règles d’ajustement des fuseaux horaires.

Pour illustrer, la transition vers l’heure d’été dans le fuseau horaire standard central des États-Unis a lieu à 2 h du matin. le 9 mars 2008. Cela signifie que l’ajout d’un intervalle de deux heures trente à l’heure de 1:30 dans le fuseau horaire du Centre des États-Unis, le 9 mars 2008, doit avoir pour résultat 5:00, le 9 mars 2008. Toutefois, comme le montre l’exemple suivant, le résultat de l’addition est 4:00, le 9 mars 2008. Notez que le résultat de cette opération représente le bon point dans le temps, même si ce n’est pas le moment dans le fuseau horaire dans lequel nous sommes intéressés (c’est-à-dire qu’il n’a pas le fuseau horaire prévu).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Opérations arithmétiques avec des temps dans les fuseaux horaires

La <xref:System.TimeZoneInfo> classe comprend un certain nombre de méthodes de conversion qui appliquent automatiquement les ajustements lorsqu’ils convertissent les temps d’un fuseau horaire à l’autre. Ces options en question sont les suivantes :

- Les <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> méthodes et les méthodes, qui convertissent les temps entre deux fuseaux horaires.

- Les <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> méthodes et les méthodes, qui convertissent le temps dans un fuseau horaire particulier en UTC, ou convertissent UTC à l’heure dans un fuseau horaire particulier.

Pour plus de détails, voir [Les temps de conversion entre les fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md).

Le <xref:System.TimeZoneInfo> cours ne fournit aucune méthode qui applique automatiquement les règles d’ajustement lorsque vous effectuez l’arithmétique de date et d’heure. Toutefois, vous pouvez convertir l’heure d’un fuseau horaire en heure UTC, effectuer l’opération arithmétique, puis reconvertir l’heure UTC dans l’heure du fuseau horaire. Pour plus de détails, voir [Comment: Utilisez les fuseaux horaires dans la date et l’heure arithmétique](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Par exemple, le code suivant est semblable au code précédent qui ajoutait deux heures trente à 2:00, le 9 mars 2008. Toutefois, comme il convertit l’heure du Centre des États-Unis en heure UTC avant d’effectuer les opérations arithmétiques de date et d’heure, puis reconvertit le résultat UTC en heure du Centre, l’heure résultante reflète le passage du fuseau horaire du Centre des États-Unis à l’heure d’été.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Comment: Utiliser des fuseaux horaires dans l’arithmétique de date et d’heure](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
