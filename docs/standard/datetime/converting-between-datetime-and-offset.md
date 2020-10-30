---
title: Conversion entre DateTime et DateTimeOffset
description: Effectuer une conversion entre des valeurs DateTimeOffset et des valeurs DateTime dans .NET. La structure DateTimeOffset fournit plus de prise en plus de fuseau horaire que la structure DateTime.
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
ms.openlocfilehash: cccfa37663e5a046b08f70a89ebb7f3566486139
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063844"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Conversion entre DateTime et DateTimeOffset

Bien que la <xref:System.DateTimeOffset> structure fournisse un degré supérieur de prise en plus des fuseaux horaires par rapport à la <xref:System.DateTime> structure, les <xref:System.DateTime> paramètres sont utilisés plus communément dans les appels de méthode. Pour cette raison, la possibilité de convertir <xref:System.DateTimeOffset> des valeurs en <xref:System.DateTime> valeurs et vice versa est particulièrement importante. Cette rubrique montre comment effectuer ces conversions de façon à conserver autant d’informations de fuseau horaire que possible.

> [!NOTE]
> Les <xref:System.DateTime> <xref:System.DateTimeOffset> types et présentent des limitations lors de la représentation des heures dans des fuseaux horaires. Avec sa <xref:System.DateTime.Kind%2A> propriété, peut <xref:System.DateTime> refléter uniquement le temps universel coordonné (UTC, Universal Time Coordinated) et le fuseau horaire local du système. <xref:System.DateTimeOffset> reflète le décalage d’un temps par rapport à l’heure UTC, mais ne reflète pas le fuseau horaire réel auquel ce décalage appartient. Pour plus d’informations sur les valeurs d’heure et la prise en charge des fuseaux horaires, consultez [choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversions de DateTime en DateTimeOffset

La <xref:System.DateTimeOffset> structure fournit deux méthodes équivalentes pour effectuer une <xref:System.DateTime> <xref:System.DateTimeOffset> conversion adaptée à la plupart des conversions :

- Le <xref:System.DateTimeOffset.%23ctor%2A> constructeur, qui crée un nouvel <xref:System.DateTimeOffset> objet basé sur une <xref:System.DateTime> valeur.

- L’opérateur de conversion implicite, qui vous permet d’assigner une <xref:System.DateTime> valeur à un <xref:System.DateTimeOffset> objet.

Pour les valeurs UTC et locales <xref:System.DateTime> , la <xref:System.DateTimeOffset.Offset%2A> propriété de la <xref:System.DateTimeOffset> valeur résultante reflète précisément l’offset de fuseau horaire UTC ou local. Par exemple, le code suivant convertit une heure UTC en sa <xref:System.DateTimeOffset> valeur équivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Dans ce cas, le décalage de la variable `utcTime2` est 00:00. De même, le code suivant convertit une heure locale en sa <xref:System.DateTimeOffset> valeur équivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Toutefois, pour les <xref:System.DateTime> valeurs dont la <xref:System.DateTime.Kind%2A> propriété a <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> la valeur, ces deux méthodes de conversion produisent une <xref:System.DateTimeOffset> valeur dont le décalage est celui du fuseau horaire local. Cela est illustré dans l’exemple suivant, qui est exécuté dans le fuseau horaire Pacifique (États-Unis).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Si la <xref:System.DateTime> valeur reflète la date et l’heure dans autre chose que le fuseau horaire local ou UTC, vous pouvez la convertir en une <xref:System.DateTimeOffset> valeur et conserver ses informations de fuseau horaire en appelant le <xref:System.DateTimeOffset.%23ctor%2A> constructeur surchargé. Par exemple, l’exemple suivant instancie un <xref:System.DateTimeOffset> objet qui reflète l’heure standard centrale.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Le deuxième paramètre de cette surcharge de constructeur, un <xref:System.TimeSpan> objet qui représente le décalage de l’heure par rapport à l’heure UTC, doit être récupéré en appelant la <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> méthode du fuseau horaire correspondant à l’heure. Le seul paramètre de la méthode est la <xref:System.DateTime> valeur qui représente la date et l’heure à convertir. Si le fuseau horaire prend en charge l’heure d’été, ce paramètre permet à la méthode de déterminer le décalage approprié pour cette date et cette heure particulières.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversions de DateTimeOffset vers DateTime

La <xref:System.DateTimeOffset.DateTime%2A> propriété est généralement utilisée pour effectuer la <xref:System.DateTimeOffset> <xref:System.DateTime> conversion. Toutefois, elle retourne une <xref:System.DateTime> valeur dont <xref:System.DateTime.Kind%2A> la propriété est <xref:System.DateTimeKind.Unspecified> , comme l’illustre l’exemple suivant.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Cela signifie que toutes les informations sur la <xref:System.DateTimeOffset> relation de la valeur avec l’heure UTC sont perdues par la conversion lorsque la <xref:System.DateTimeOffset.DateTime%2A> propriété est utilisée. Cela affecte <xref:System.DateTimeOffset> les valeurs qui correspondent à l’heure UTC ou à l’heure locale du système, car la <xref:System.DateTimeOffset.DateTime%2A> structure reflète uniquement ces deux fuseaux horaires dans sa <xref:System.DateTime.Kind%2A> propriété.

Pour conserver autant d’informations de fuseau horaire que possible lors de la conversion <xref:System.DateTimeOffset> d’un en <xref:System.DateTime> valeur, vous pouvez utiliser les <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Propriétés et.

### <a name="converting-a-utc-time"></a>Conversion d’une heure UTC

Pour indiquer qu’une valeur convertie <xref:System.DateTimeOffset.DateTime%2A> est l’heure UTC, vous pouvez récupérer la valeur de la <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> propriété. Elle diffère de la <xref:System.DateTimeOffset.DateTime%2A> propriété de deux manières :

- Elle retourne une <xref:System.DateTime> valeur dont la <xref:System.DateTime.Kind%2A> propriété est <xref:System.DateTimeKind.Utc> .

- Si la <xref:System.DateTimeOffset.Offset%2A> valeur de la propriété n’est pas égale <xref:System.TimeSpan.Zero?displayProperty=nameWithType> à, elle convertit l’heure en heure UTC.

> [!NOTE]
> Si votre application exige que les valeurs converties <xref:System.DateTime> identifient de façon non ambiguë un point unique dans le temps, vous devez envisager d’utiliser la <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> propriété pour gérer toutes les <xref:System.DateTimeOffset> <xref:System.DateTime> conversions.

Le code suivant utilise la <xref:System.DateTimeOffset.UtcDateTime%2A> propriété pour convertir une <xref:System.DateTimeOffset> valeur dont le décalage est égal <xref:System.TimeSpan.Zero?displayProperty=nameWithType> à une <xref:System.DateTime> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Le code suivant utilise la <xref:System.DateTimeOffset.UtcDateTime%2A> propriété pour effectuer une conversion de fuseau horaire et une conversion de type sur une <xref:System.DateTimeOffset> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Conversion d’une heure locale

Pour indiquer qu’une <xref:System.DateTimeOffset> valeur représente l’heure locale, vous pouvez passer la <xref:System.DateTime> valeur retournée par la <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> propriété à `static` la `Shared` méthode (en Visual Basic) <xref:System.DateTime.SpecifyKind%2A> . La méthode retourne la date et l’heure qui lui sont passées en tant que premier paramètre, mais affecte <xref:System.DateTime.Kind%2A> à la propriété la valeur spécifiée par son deuxième paramètre. Le code suivant utilise la <xref:System.DateTime.SpecifyKind%2A> méthode lors de la conversion d’une <xref:System.DateTimeOffset> valeur dont le décalage correspond à celui du fuseau horaire local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Vous pouvez également utiliser la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour convertir une <xref:System.DateTimeOffset> valeur en valeur locale <xref:System.DateTime> . La <xref:System.DateTime.Kind%2A> propriété de la valeur retournée <xref:System.DateTime> est <xref:System.DateTimeKind.Local> . Le code suivant utilise la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété lors de la conversion d’une <xref:System.DateTimeOffset> valeur dont le décalage correspond à celui du fuseau horaire local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Lorsque vous récupérez une <xref:System.DateTime> valeur à l’aide de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété, l’accesseur de la propriété `get` convertit d’abord la <xref:System.DateTimeOffset> valeur en heure UTC, puis la convertit en heure locale en appelant la <xref:System.DateTimeOffset.ToLocalTime%2A> méthode. Cela signifie que vous pouvez récupérer une valeur de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour effectuer une conversion de fuseau horaire en même temps que vous effectuez une conversion de type. Cela signifie également que les règles d’ajustement du fuseau horaire local sont appliquées lors de la conversion. Le code suivant illustre l’utilisation de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour effectuer à la fois un type et une conversion de fuseau horaire. L’exemple de sortie concerne un ordinateur défini sur le fuseau horaire Pacifique (États-Unis et Canada). La date du jour de novembre est l’heure du Pacifique (UTC-8), tandis que la date de juin correspond à l’heure d’été (UTC-7).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Méthode de conversion à usage général

L’exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui convertit les <xref:System.DateTimeOffset> valeurs en <xref:System.DateTime> valeurs. En fonction de son décalage, elle détermine si la <xref:System.DateTimeOffset> valeur est une heure UTC, une heure locale ou une autre heure, et définit la propriété de la valeur de date et d’heure retournée en <xref:System.DateTime.Kind%2A> conséquence.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

L’exemple suivant appelle la `ConvertFromDateTimeOffset` méthode pour convertir <xref:System.DateTimeOffset> des valeurs qui représentent une heure UTC, une heure locale et une heure dans le fuseau horaire central des États-Unis.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Notez que ce code part de deux hypothèses qui, selon l’application et la source de ses valeurs de date et d’heure, peuvent ne pas toujours être valides :

- Elle suppose qu’une valeur de date et d’heure dont le décalage <xref:System.TimeSpan.Zero?displayProperty=nameWithType> représente l’heure UTC. En fait, l’heure UTC n’est pas une heure dans un fuseau horaire particulier, mais l’heure par rapport à laquelle les heures des fuseaux horaires du monde sont normalisées. Les fuseaux horaires peuvent également avoir un décalage de <xref:System.TimeSpan.Zero> .

- Il suppose qu’une date et une heure dont le décalage est égal à celui du fuseau horaire local représentent le fuseau horaire local. Étant donné que les valeurs de date et d’heure sont dissociées de leur fuseau horaire d’origine, cela peut ne pas être le cas ; la date et l’heure peuvent provenir d’un autre fuseau horaire affichant le même décalage.

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
