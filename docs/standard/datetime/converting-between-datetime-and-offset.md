---
title: Conversion entre DateTime et DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb91ed8edd0c5cd3cb1d051157596f311718195d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107067"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Conversion entre DateTime et DateTimeOffset

Bien que <xref:System.DateTimeOffset> la structure fournisse un degré supérieur de prise en plus <xref:System.DateTime> des fuseaux horaires par rapport à la structure, <xref:System.DateTime> les paramètres sont utilisés plus communément dans les appels de méthode. Pour cette raison, la possibilité de convertir <xref:System.DateTimeOffset> des valeurs <xref:System.DateTime> en valeurs et vice versa est particulièrement importante. Cette rubrique montre comment effectuer ces conversions de façon à conserver autant d’informations de fuseau horaire que possible.

> [!NOTE]
> Les <xref:System.DateTime> types<xref:System.DateTimeOffset> et présentent des limitations lors de la représentation des heures dans des fuseaux horaires. Avec sa <xref:System.DateTime.Kind%2A> propriété, <xref:System.DateTime> peut refléter uniquement le temps universel coordonné (UTC, Universal Time Coordinated) et le fuseau horaire local du système. <xref:System.DateTimeOffset>reflète le décalage d’un temps par rapport à l’heure UTC, mais ne reflète pas le fuseau horaire réel auquel ce décalage appartient. Pour plus d’informations sur les valeurs d’heure et la prise en charge des fuseaux horaires, consultez [choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversions de DateTime en DateTimeOffset

La <xref:System.DateTimeOffset> structure fournit deux méthodes équivalentes pour <xref:System.DateTime> <xref:System.DateTimeOffset> effectuer une conversion adaptée à la plupart des conversions:

- Le <xref:System.DateTimeOffset.%23ctor%2A> constructeur, qui crée un nouvel <xref:System.DateTimeOffset> objet basé sur une <xref:System.DateTime> valeur.

- L’opérateur de conversion implicite, qui vous permet d' <xref:System.DateTime> assigner <xref:System.DateTimeOffset> une valeur à un objet.

Pour les valeurs UTC <xref:System.DateTime> et locales, <xref:System.DateTimeOffset.Offset%2A> la propriété de la <xref:System.DateTimeOffset> valeur résultante reflète précisément l’offset de fuseau horaire UTC ou local. Par exemple, le code suivant convertit une heure UTC en sa <xref:System.DateTimeOffset> valeur équivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Dans ce cas, le décalage de la variable `utcTime2` est 00:00. De même, le code suivant convertit une heure locale en sa <xref:System.DateTimeOffset> valeur équivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Toutefois, pour <xref:System.DateTime> les valeurs <xref:System.DateTime.Kind%2A> dont la <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>propriété a la valeur, ces deux <xref:System.DateTimeOffset> méthodes de conversion produisent une valeur dont le décalage est celui du fuseau horaire local. Cela est illustré dans l’exemple suivant, qui se déroule dans le fuseau horaire Pacifique (É.-U.).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Si la <xref:System.DateTime> valeur reflète la date et l’heure dans autre chose que le fuseau horaire local ou UTC, vous pouvez la convertir en <xref:System.DateTimeOffset> une valeur et conserver ses informations de fuseau horaire en <xref:System.DateTimeOffset.%23ctor%2A> appelant le constructeur surchargé. Par exemple, l’exemple suivant instancie un <xref:System.DateTimeOffset> objet qui reflète l’heure standard centrale.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Le deuxième paramètre de cette surcharge de constructeur, <xref:System.TimeSpan> un objet qui représente le décalage de l’heure par rapport à l’heure UTC, <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> doit être récupéré en appelant la méthode du fuseau horaire correspondant à l’heure. Le seul paramètre de la méthode est <xref:System.DateTime> la valeur qui représente la date et l’heure à convertir. Si le fuseau horaire prend en charge l’heure d’été, ce paramètre permet à la méthode de déterminer le décalage approprié pour cette date et cette heure particulières.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversions de DateTimeOffset vers DateTime

La <xref:System.DateTimeOffset.DateTime%2A> propriété est généralement utilisée pour <xref:System.DateTime> effectuer <xref:System.DateTimeOffset> la conversion. Toutefois, elle retourne une <xref:System.DateTime> valeur dont <xref:System.DateTime.Kind%2A> la propriété <xref:System.DateTimeKind.Unspecified>est, comme l’illustre l’exemple suivant.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Cela signifie que toutes les informations sur <xref:System.DateTimeOffset> la relation de la valeur avec l’heure UTC sont perdues <xref:System.DateTimeOffset.DateTime%2A> par la conversion lorsque la propriété est utilisée. Cela affecte <xref:System.DateTimeOffset> les valeurs qui correspondent à l’heure UTC ou à l’heure locale du système <xref:System.DateTimeOffset.DateTime%2A> , car la structure reflète uniquement ces deux fuseaux horaires dans sa <xref:System.DateTime.Kind%2A> propriété.

Pour conserver autant d’informations de fuseau horaire que possible lors de <xref:System.DateTimeOffset> la conversion <xref:System.DateTime> d’un en valeur, vous <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> pouvez <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> utiliser les propriétés et.

### <a name="converting-a-utc-time"></a>Conversion d’une heure UTC

Pour indiquer qu’une valeur <xref:System.DateTimeOffset.DateTime%2A> convertie est l’heure UTC, vous pouvez récupérer la valeur <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> de la propriété. Elle diffère de la <xref:System.DateTimeOffset.DateTime%2A> propriété de deux manières:

- Elle retourne une <xref:System.DateTime> valeur dont <xref:System.DateTime.Kind%2A> la propriété <xref:System.DateTimeKind.Utc>est.

- Si la <xref:System.DateTimeOffset.Offset%2A> valeur de la propriété n' <xref:System.TimeSpan.Zero?displayProperty=nameWithType>est pas égale à, elle convertit l’heure en heure UTC.

> [!NOTE]
> Si votre application exige que les <xref:System.DateTime> valeurs converties identifient de façon non ambiguë un point unique dans le temps <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> , vous devez envisager d' <xref:System.DateTime> utiliser la propriété pour gérer toutes les <xref:System.DateTimeOffset> conversions.

Le code suivant utilise la <xref:System.DateTimeOffset.UtcDateTime%2A> propriété pour convertir une <xref:System.DateTimeOffset> <xref:System.TimeSpan.Zero?displayProperty=nameWithType> valeur dont le décalage est égal à <xref:System.DateTime> une valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Le code suivant utilise la <xref:System.DateTimeOffset.UtcDateTime%2A> propriété pour effectuer une conversion de fuseau horaire et une conversion de type sur <xref:System.DateTimeOffset> une valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Conversion d’une heure locale

Pour indiquer qu’une <xref:System.DateTimeOffset> valeur représente l’heure locale, vous pouvez passer la <xref:System.DateTime> valeur retournée par <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> la propriété à `static` la`Shared` méthode (en <xref:System.DateTime.SpecifyKind%2A> Visual Basic). La méthode retourne la date et l’heure qui lui sont passées en tant que premier paramètre, <xref:System.DateTime.Kind%2A> mais affecte à la propriété la valeur spécifiée par son deuxième paramètre. Le code suivant utilise la <xref:System.DateTime.SpecifyKind%2A> méthode lors de la <xref:System.DateTimeOffset> conversion d’une valeur dont le décalage correspond à celui du fuseau horaire local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Vous pouvez également utiliser la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour convertir une <xref:System.DateTimeOffset> valeur en valeur locale <xref:System.DateTime> . La <xref:System.DateTime.Kind%2A> propriété de la valeur <xref:System.DateTime> retournée <xref:System.DateTimeKind.Local>est. Le code suivant utilise la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété lors de la <xref:System.DateTimeOffset> conversion d’une valeur dont le décalage correspond à celui du fuseau horaire local. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Lorsque vous récupérez <xref:System.DateTime> une valeur à <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> l’aide de la propriété `get` , l’accesseur de <xref:System.DateTimeOffset> la propriété convertit d’abord la valeur en heure UTC, puis <xref:System.DateTimeOffset.ToLocalTime%2A> la convertit en heure locale en appelant la méthode. Cela signifie que vous pouvez récupérer une valeur de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour effectuer une conversion de fuseau horaire en même temps que vous effectuez une conversion de type. Cela signifie également que les règles d’ajustement du fuseau horaire local sont appliquées lors de la conversion. Le code suivant illustre l’utilisation de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour effectuer à la fois un type et une conversion de fuseau horaire.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Méthode de conversion à usage général

L’exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui <xref:System.DateTimeOffset> convertit les <xref:System.DateTime> valeurs en valeurs. En fonction de son décalage, elle détermine si <xref:System.DateTimeOffset> la valeur est une heure UTC, une heure locale ou une autre heure, et définit la propriété de la valeur de date <xref:System.DateTime.Kind%2A> et d’heure retournée en conséquence.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

L’exemple suivant appelle la `ConvertFromDateTimeOffset` méthode pour convertir <xref:System.DateTimeOffset> des valeurs qui représentent une heure UTC, une heure locale et une heure dans le fuseau horaire horaire Centre des États-Unis.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Notez que ce code part de deux hypothèses qui, selon l’application et la source de ses valeurs de date et d’heure, peuvent ne pas toujours être valides :

- Elle suppose qu’une valeur de date et d’heure dont le <xref:System.TimeSpan.Zero?displayProperty=nameWithType> décalage représente l’heure UTC. En fait, l’heure UTC n’est pas une heure dans un fuseau horaire particulier, mais l’heure par rapport à laquelle les heures des fuseaux horaires du monde sont normalisées. Les fuseaux horaires peuvent également avoir un <xref:System.TimeSpan.Zero>décalage de.

- Il suppose qu’une date et une heure dont le décalage est égal à celui du fuseau horaire local représentent le fuseau horaire local. Étant donné que les valeurs de date et d’heure sont dissociées de leur fuseau horaire d’origine, cela peut ne pas être le cas ; la date et l’heure peuvent provenir d’un autre fuseau horaire affichant le même décalage.

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
