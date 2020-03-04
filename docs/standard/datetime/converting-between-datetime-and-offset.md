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
ms.openlocfilehash: 5c19296f75e9e002e88263c5e5efa9917e185ebc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156034"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Conversion entre DateTime et DateTimeOffset

Bien que la structure <xref:System.DateTimeOffset> offre un degré de prise en plus plus élevé des fuseaux horaires que la structure <xref:System.DateTime>, les paramètres <xref:System.DateTime> sont utilisés plus communément dans les appels de méthode. Pour cette raison, la possibilité de convertir les valeurs de <xref:System.DateTimeOffset> en <xref:System.DateTime> valeurs et vice versa est particulièrement importante. Cette rubrique montre comment effectuer ces conversions de façon à conserver autant d’informations de fuseau horaire que possible.

> [!NOTE]
> La <xref:System.DateTime> et les types de <xref:System.DateTimeOffset> présentent des limitations lors de la représentation des heures dans des fuseaux horaires. Avec sa propriété <xref:System.DateTime.Kind%2A>, <xref:System.DateTime> est en mesure de refléter uniquement le temps universel coordonné (UTC, Universal Time Coordinated) et le fuseau horaire local du système. <xref:System.DateTimeOffset> reflète le décalage d’un temps par rapport à l’heure UTC, mais ne reflète pas le fuseau horaire réel auquel ce décalage appartient. Pour plus d’informations sur les valeurs d’heure et la prise en charge des fuseaux horaires, consultez [choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversions de DateTime en DateTimeOffset

La structure <xref:System.DateTimeOffset> fournit deux façons équivalentes d’effectuer des <xref:System.DateTime> pour <xref:System.DateTimeOffset> la conversion qui conviennent à la plupart des conversions :

- Le constructeur <xref:System.DateTimeOffset.%23ctor%2A>, qui crée un nouvel objet <xref:System.DateTimeOffset> basé sur une valeur de <xref:System.DateTime>.

- L’opérateur de conversion implicite, qui vous permet d’assigner une valeur <xref:System.DateTime> à un objet <xref:System.DateTimeOffset>.

Pour les valeurs de <xref:System.DateTime> locales et UTC, la propriété <xref:System.DateTimeOffset.Offset%2A> de la valeur de <xref:System.DateTimeOffset> résultante reflète précisément le décalage de fuseau horaire UTC ou local. Par exemple, le code suivant convertit une heure UTC en sa valeur <xref:System.DateTimeOffset> équivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Dans ce cas, le décalage de la variable `utcTime2` est 00:00. De même, le code suivant convertit une heure locale en sa valeur <xref:System.DateTimeOffset> équivalente.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Toutefois, pour les valeurs <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, ces deux méthodes de conversion produisent une valeur <xref:System.DateTimeOffset> dont le décalage est celui du fuseau horaire local. Cela est illustré dans l’exemple suivant, qui est exécuté dans le fuseau horaire Pacifique (États-Unis).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Si la valeur de <xref:System.DateTime> reflète la date et l’heure dans autre chose que le fuseau horaire local ou UTC, vous pouvez la convertir en une valeur <xref:System.DateTimeOffset> et conserver ses informations de fuseau horaire en appelant le constructeur surchargé <xref:System.DateTimeOffset.%23ctor%2A>. Par exemple, l’exemple suivant instancie un objet <xref:System.DateTimeOffset> qui reflète l’heure standard centrale.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Le deuxième paramètre de cette surcharge de constructeur, un objet <xref:System.TimeSpan> qui représente le décalage de l’heure par rapport à l’heure UTC, doit être récupéré en appelant la méthode <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> du fuseau horaire correspondant à l’heure. Le seul paramètre de la méthode est la valeur <xref:System.DateTime> qui représente la date et l’heure à convertir. Si le fuseau horaire prend en charge l’heure d’été, ce paramètre permet à la méthode de déterminer le décalage approprié pour cette date et cette heure particulières.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversions de DateTimeOffset vers DateTime

La propriété <xref:System.DateTimeOffset.DateTime%2A> est couramment utilisée pour effectuer des <xref:System.DateTimeOffset> à <xref:System.DateTime> conversion. Toutefois, elle retourne une valeur <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind.Unspecified>, comme l’illustre l’exemple suivant.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Cela signifie que toutes les informations sur la relation de la valeur de <xref:System.DateTimeOffset> avec l’heure UTC sont perdues par la conversion lorsque la propriété <xref:System.DateTimeOffset.DateTime%2A> est utilisée. Cela affecte les valeurs de <xref:System.DateTimeOffset> qui correspondent à l’heure UTC ou à l’heure locale du système, car la structure de <xref:System.DateTimeOffset.DateTime%2A> reflète uniquement ces deux fuseaux horaires dans sa propriété <xref:System.DateTime.Kind%2A>.

Pour conserver autant d’informations de fuseau horaire que possible lors de la conversion d’un <xref:System.DateTimeOffset> en valeur <xref:System.DateTime>, vous pouvez utiliser les propriétés <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>.

### <a name="converting-a-utc-time"></a>Conversion d’une heure UTC

Pour indiquer qu’une valeur de <xref:System.DateTimeOffset.DateTime%2A> convertie est l’heure UTC, vous pouvez récupérer la valeur de la propriété <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>. Elle diffère de la propriété <xref:System.DateTimeOffset.DateTime%2A> de deux manières :

- Elle retourne une valeur <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind.Utc>.

- Si la valeur de la propriété <xref:System.DateTimeOffset.Offset%2A> n’est pas égale à <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, elle convertit l’heure en heure UTC.

> [!NOTE]
> Si votre application exige que les valeurs converties <xref:System.DateTime> identifient de manière non ambiguë un point unique dans le temps, vous devez envisager d’utiliser la propriété <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> pour gérer toutes les <xref:System.DateTimeOffset> à <xref:System.DateTime> conversions.

Le code suivant utilise la propriété <xref:System.DateTimeOffset.UtcDateTime%2A> pour convertir une valeur <xref:System.DateTimeOffset> dont le décalage est égal à <xref:System.TimeSpan.Zero?displayProperty=nameWithType> à une valeur <xref:System.DateTime>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Le code suivant utilise la propriété <xref:System.DateTimeOffset.UtcDateTime%2A> pour effectuer une conversion de fuseau horaire et une conversion de type sur une valeur <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Conversion d’une heure locale

Pour indiquer qu’une valeur <xref:System.DateTimeOffset> représente l’heure locale, vous pouvez passer la valeur <xref:System.DateTime> retournée par la propriété <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> à la `static` (`Shared` dans Visual Basic) <xref:System.DateTime.SpecifyKind%2A> méthode. La méthode retourne la date et l’heure qui lui sont passées en tant que premier paramètre, mais définit la propriété <xref:System.DateTime.Kind%2A> sur la valeur spécifiée par son deuxième paramètre. Le code suivant utilise la méthode <xref:System.DateTime.SpecifyKind%2A> lors de la conversion d’une valeur <xref:System.DateTimeOffset> dont le décalage correspond à celui du fuseau horaire local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Vous pouvez également utiliser la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> pour convertir une valeur de <xref:System.DateTimeOffset> en une valeur de <xref:System.DateTime> locale. La propriété <xref:System.DateTime.Kind%2A> de la valeur <xref:System.DateTime> retournée est <xref:System.DateTimeKind.Local>. Le code suivant utilise la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> lors de la conversion d’une valeur <xref:System.DateTimeOffset> dont le décalage correspond à celui du fuseau horaire local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Lorsque vous récupérez une valeur <xref:System.DateTime> à l’aide de la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>, l’accesseur `get` de la propriété convertit d’abord la valeur <xref:System.DateTimeOffset> en heure UTC, puis la convertit en heure locale en appelant la méthode <xref:System.DateTimeOffset.ToLocalTime%2A>. Cela signifie que vous pouvez récupérer une valeur de la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> pour effectuer une conversion de fuseau horaire en même temps que vous effectuez une conversion de type. Cela signifie également que les règles d’ajustement du fuseau horaire local sont appliquées lors de la conversion. Le code suivant illustre l’utilisation de la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> pour exécuter à la fois un type et une conversion de fuseau horaire.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Méthode de conversion à usage général

L’exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui convertit <xref:System.DateTimeOffset> valeurs en <xref:System.DateTime> valeurs. En fonction de son décalage, elle détermine si la valeur <xref:System.DateTimeOffset> est une heure UTC, une heure locale ou une autre heure, et définit la propriété de <xref:System.DateTime.Kind%2A> de la valeur de date et d’heure retournée en conséquence.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

L’exemple suivant appelle la méthode `ConvertFromDateTimeOffset` pour convertir les valeurs <xref:System.DateTimeOffset> qui représentent une heure UTC, une heure locale et une heure dans le fuseau horaire central des États-Unis.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Notez que ce code part de deux hypothèses qui, selon l’application et la source de ses valeurs de date et d’heure, peuvent ne pas toujours être valides :

- Elle suppose qu’une valeur de date et d’heure dont le décalage est <xref:System.TimeSpan.Zero?displayProperty=nameWithType> représente l’heure UTC. En fait, l’heure UTC n’est pas une heure dans un fuseau horaire particulier, mais l’heure par rapport à laquelle les heures des fuseaux horaires du monde sont normalisées. Les fuseaux horaires peuvent également avoir un décalage de <xref:System.TimeSpan.Zero>.

- Il suppose qu’une date et une heure dont le décalage est égal à celui du fuseau horaire local représentent le fuseau horaire local. Étant donné que les valeurs de date et d’heure sont dissociées de leur fuseau horaire d’origine, cela peut ne pas être le cas ; la date et l’heure peuvent provenir d’un autre fuseau horaire affichant le même décalage.

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
