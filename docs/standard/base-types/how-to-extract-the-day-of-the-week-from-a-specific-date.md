---
title: 'Procédure : extraire le jour de la semaine d’une date spécifique'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
ms.openlocfilehash: 8eed7c0176a2c1f4beb472dff981d52e522c7e36
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523830"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Procédure : extraire le jour de la semaine d’une date spécifique
Le .NET Framework permet de déterminer facilement le jour ordinal de la semaine pour une date particulière, et d'afficher le nom du jour de la semaine localisé pour une date particulière. Le jour de la semaine correspondant à une date particulière est indiqué par une valeur énumérée contenue dans la propriété <xref:System.DateTime.DayOfWeek%2A> ou <xref:System.DateTimeOffset.DayOfWeek%2A>. Par contre, la récupération du nom du jour de la semaine est une opération de mise en forme qui peut être effectuée en appelant une méthode de mise en forme, comme la méthode `ToString` d'une valeur de date et d'heure ou la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>. Cette rubrique montre comment effectuer ces opérations de mise en forme.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Pour extraire un nombre indiquant le jour de la semaine d'une date spécifique  
  
1. Si la date est représentée sous forme de chaîne, convertissez-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> en utilisant la méthode <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> statique.  
  
2. Utilisez la propriété <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> pour récupérer une valeur <xref:System.DayOfWeek> qui indique le jour de la semaine.  
  
3. Au besoin, effectuez un cast (en C#) ou une conversion (en Visual Basic) de la valeur <xref:System.DayOfWeek> en un entier.  
  
 L'exemple suivant affiche un entier qui représente le jour de la semaine d'une date spécifique.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Pour extraire le nom abrégé du jour de la semaine d'une date spécifique  
  
1. Si la date est représentée sous forme de chaîne, convertissez-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> en utilisant la méthode <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> statique.  
  
2. Vous pouvez extraire le nom abrégé du jour de la semaine au format de la culture actuelle ou d'une culture spécifique :  
  
    1. Pour extraire le nom abrégé du jour de la semaine au format de la culture actuelle, appelez la méthode d'instance <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> de la valeur de date et d'heure, puis indiquez la chaîne « ddd » comme paramètre `format`. L'exemple suivant illustre l'appel de la méthode <xref:System.DateTime.ToString%28System.String%29>.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Pour extraire le nom abrégé en semaine pour une culture <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> spécifique, appelez la méthode de la date et de la valeur de l’heure ou <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> de l’instance. Indiquez la chaîne « ddd » comme paramètre `format`. Indiquez comme paramètre <xref:System.Globalization.CultureInfo> un objet <xref:System.Globalization.DateTimeFormatInfo> ou `provider` qui représente la culture au format de laquelle vous souhaitez récupérer le nom du jour de la semaine. Le code suivant illustre un appel de la méthode <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> à l'aide d'un objet <xref:System.Globalization.CultureInfo> qui représente la culture fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Pour extraire le nom complet du jour de la semaine d'une date spécifique  
  
1. Si la date est représentée sous forme de chaîne, convertissez-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> en utilisant la méthode <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> statique.  
  
2. Vous pouvez extraire le nom complet du jour de la semaine au format de la culture actuelle ou d'une culture spécifique :  
  
    1. Pour extraire le nom en semaine de la culture <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> actuelle, appelez la méthode de la valeur de la date et de l’heure ou <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> de l’instance, et passez la chaîne « dddd » comme `format` paramètre. L'exemple suivant illustre l'appel de la méthode <xref:System.DateTime.ToString%28System.String%29>.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Pour extraire le nom en semaine d’une culture <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> spécifique, appelez la méthode de la date et de l’heure ou <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> de l’instance. Indiquez la chaîne « dddd » comme paramètre `format`. Indiquez comme paramètre <xref:System.Globalization.CultureInfo> un objet <xref:System.Globalization.DateTimeFormatInfo> ou `provider` qui représente la culture au format de laquelle vous souhaitez récupérer le nom du jour de la semaine. Le code suivant illustre un appel de la méthode <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> à l'aide d'un objet <xref:System.Globalization.CultureInfo> qui représente la culture es-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Exemple  
 L'exemple montre comment appeler les propriétés <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> et les méthodes <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> pour récupérer le nombre qui représente le jour de la semaine, le nom abrégé du jour de la semaine et le nom complet du jour de la semaine pour une date particulière.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Des langages spécifiques peuvent fournir des fonctionnalités similaires aux fonctionnalités offertes par le .NET Framework, ou complémentaires de celles-ci. Par exemple, Visual Basic comprend deux de ces fonctions :  
  
- `Weekday`, qui retourne un nombre qui indique le jour de la semaine d'une date particulière. Il considère que la valeur ordinale du premier jour de la semaine est un, tandis que la propriété <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> considère que cette valeur est égale à zéro.  
  
- `WeekdayName`, qui retourne, dans la culture actuelle, le nom du jour de la semaine correspondant au nombre d'un jour de la semaine.  
  
 L'exemple suivant illustre l'utilisation des fonctions Visual Basic `Weekday` et `WeekdayName`.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Vous pouvez également recourir à la valeur retournée par la propriété <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> pour récupérer le nom du jour de la semaine d'une date particulière. Pour ce faire, vous avez uniquement besoin d'appeler la méthode <xref:System.Enum.ToString%2A> sur la valeur <xref:System.DayOfWeek> retournée par la propriété. Toutefois, cette technique ne génère pas un nom de jour de la semaine localisé dans la culture actuelle, comme l'illustre l'exemple suivant.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a>Voir aussi

- [Chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Chaînes de format de date et d'heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
