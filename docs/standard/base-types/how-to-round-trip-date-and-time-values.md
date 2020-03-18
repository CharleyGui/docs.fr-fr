---
title: "Comment : effectuer un aller-retour de valeurs de date et d'heure"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 2e3a58ffe8332e0afec62461f6897d673e1da09f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132005"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Comment : effectuer un aller-retour de valeurs de date et d'heure

Dans de nombreuses applications, une valeur de date et d’heure est destinée à identifier clairement un point unique dans le temps. Cette rubrique montre comment enregistrer et restaurer une valeur <xref:System.DateTime>, une valeur <xref:System.DateTimeOffset> et une valeur de date et d’heure avec des informations de fuseau horaire pour que la valeur restaurée identifie la même heure que la valeur enregistrée.

### <a name="to-round-trip-a-datetime-value"></a>Pour effectuer un aller-retour d’une valeur DateTime

1. Convertissez la valeur <xref:System.DateTime> en sa représentation sous forme de chaîne en appelant la méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> avec le spécificateur de format « o ».

2. Enregistrez la représentation sous forme de chaîne de la valeur <xref:System.DateTime> dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.

3. Récupérez la chaîne qui représente la valeur <xref:System.DateTime>.

4. Appelez la méthode <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> en tant que valeur du paramètre `styles`.

L’exemple suivant montre comment effectuer un aller-retour d’une valeur <xref:System.DateTime>.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Durant l’aller-retour d’une valeur <xref:System.DateTime>, cette technique permet de conserver correctement l’heure pour toutes les heures locales et universelles. Par exemple, si <xref:System.DateTime> une valeur locale est économisée sur un système dans le fuseau horaire standard du Pacifique des États-Unis et est rétablie sur un système dans le fuseau horaire standard central des États-Unis, la date et l’heure restaurées seront deux heures plus tard que l’heure d’origine, ce qui reflète le décalage horaire entre les deux fuseaux horaires. En revanche, cette technique n’est pas nécessairement exacte pour les heures non spécifiées. Toutes les valeurs <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind.Unspecified> sont traitées comme s’il s’agissait d’heures locales. Si ce n’est pas le cas, la valeur <xref:System.DateTime> n’identifie pas correctement le point adéquat dans le temps. La solution pour contourner cette limitation consiste à associer étroitement une valeur de date et d’heure avec son fuseau horaire pour l’opération d’enregistrement et de restauration.

### <a name="to-round-trip-a-datetimeoffset-value"></a>Pour effectuer un aller-retour d’une valeur DateTimeOffset

1. Convertissez la valeur <xref:System.DateTimeOffset> en sa représentation sous forme de chaîne en appelant la méthode <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> avec le spécificateur de format « o ».

2. Enregistrez la représentation sous forme de chaîne de la valeur <xref:System.DateTimeOffset> dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.

3. Récupérez la chaîne qui représente la valeur <xref:System.DateTimeOffset>.

4. Appelez la méthode <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> en tant que valeur du paramètre `styles`.

L’exemple suivant montre comment effectuer un aller-retour d’une valeur <xref:System.DateTimeOffset>.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Cette technique identifie toujours clairement une valeur <xref:System.DateTimeOffset> comme point unique dans le temps. La valeur peut ensuite être convertie en temps universel coordonné (UTC) en appelant la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>, ou convertie en heure dans un fuseau horaire particulier en appelant la méthode <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>. La principale limitation de cette technique est que les opérations arithmétiques de date et heure, effectuées sur une valeur <xref:System.DateTimeOffset> qui représente l’heure dans un fuseau horaire particulier, risquent de ne pas produire des résultats exacts pour ce fuseau horaire. En effet, quand une valeur <xref:System.DateTimeOffset> est instanciée, elle est dissociée de son fuseau horaire. Ainsi, les règles d’ajustement de ce fuseau horaire ne sont plus applicables quand vous effectuez des calculs de date et d’heure. Vous pouvez contourner ce problème en définissant un type personnalisé qui inclut à la fois une valeur de date et heure et son fuseau horaire correspondant.

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Pour effectuer un aller-retour d’une valeur de date et d’heure avec son fuseau horaire

1. Définissez une classe ou une structure avec deux champs. Le premier champ est un objet <xref:System.DateTime> ou <xref:System.DateTimeOffset>, et le second est un objet <xref:System.TimeZoneInfo>. L’exemple suivant est une version simple de ce type.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Marquez la classe avec l’attribut <xref:System.SerializableAttribute>.

3. Sérialisez l’objet à l’aide de la méthode <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.

4. Restaurez l’objet à l’aide de la méthode <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.

5. Castez (en C#) ou convertissez (en Visual Basic) l’objet désérialisé en objet du type approprié.

L’exemple suivant montre comment effectuer un aller-retour d’un objet qui stocke à la fois des informations de date et d’heure et de fuseau horaire.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Cette technique devrait toujours refléter clairement le point dans le temps correct avant et après son enregistrement et sa restauration, à condition que l’implémentation de l’objet combiné de date et d’heure et de fuseau horaire ne permette pas à la valeur de date de se désynchroniser de la valeur de fuseau horaire.

## <a name="compiling-the-code"></a>Compilation du code

Ces exemples requièrent les éléments suivants :

- Que les espaces de noms suivants soient importés avec les instructions `using` en C# ou les instructions `Imports` en Visual Basic :

  - <xref:System> (C# uniquement).

  - <xref:System.Globalization?displayProperty=nameWithType>.

  - <xref:System.IO?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.

- Que chaque exemple de code, autre que la classe `DateInTimeZone`, soit inclus dans une classe ou un module Visual Basic, encapsulé dans des méthodes et appelé à partir de la méthode `Main`.

## <a name="see-also"></a>Voir aussi

- [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
