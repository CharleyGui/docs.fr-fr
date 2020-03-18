---
title: 'Comment : afficher des dates dans des calendriers non grégoriens'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
ms.openlocfilehash: 455996d091f92367667e7077a4524898cd8face6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138755"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Comment : afficher des dates dans des calendriers non grégoriens
Les types <xref:System.DateTime> et <xref:System.DateTimeOffset> utilisent le calendrier grégorien comme calendrier par défaut. Cela signifie que l’appel de la méthode `ToString` d’une valeur de date et d’heure affiche la représentation sous forme de chaîne de la date et de l’heure dans le calendrier grégorien, même si ces date et heure ont été créées à l’aide d’un autre calendrier. Cela est illustré dans l’exemple suivant, qui utilise deux méthodes différentes pour créer une valeur de date et d’heure avec le calendrier persan, mais affiche toujours ces valeurs de date et d’heure dans le calendrier grégorien quand il appelle la méthode <xref:System.DateTime.ToString%2A>. Cet exemple reflète deux techniques couramment utilisées, mais incorrectes, pour l’affichage de la date dans un calendrier particulier.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Deux techniques différentes peuvent être utilisées pour afficher la date dans un calendrier particulier. La première nécessite que le calendrier soit le calendrier par défaut pour une culture particulière. La seconde est utilisable avec n’importe quel calendrier.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Pour afficher la date pour le calendrier par défaut d’une culture  
  
1. Instanciez un objet de calendrier dérivé de la classe <xref:System.Globalization.Calendar> qui représente le calendrier à utiliser.  
  
2. Instanciez un objet <xref:System.Globalization.CultureInfo> représentant la culture dont la mise en forme doit être utilisée pour afficher la date.  
  
3. Appelez la méthode <xref:System.Array.Exists%2A?displayProperty=nameWithType> pour déterminer si l’objet de calendrier est membre du tableau retourné par la propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Cela indique que le calendrier peut servir de calendrier par défaut pour l’objet <xref:System.Globalization.CultureInfo>. S’il n’est pas membre du tableau, suivez les instructions de la section « Pour afficher la date dans un calendrier ».  
  
4. Attribuez l’objet de calendrier à la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> de l'objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > La classe <xref:System.Globalization.CultureInfo> a également une propriété <xref:System.Globalization.CultureInfo.Calendar%2A>. Toutefois, elle est en lecture seule et constante. Elle ne change pas pour refléter le nouveau calendrier par défaut attribué à la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>.  
  
5. Appelez la méthode <xref:System.DateTime.ToString%2A> ou <xref:System.DateTime.ToString%2A> et passez-la à l’objet <xref:System.Globalization.CultureInfo> dont le calendrier par défaut a été modifié à l’étape précédente.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Pour afficher la date dans un calendrier  
  
1. Instanciez un objet de calendrier dérivé de la classe <xref:System.Globalization.Calendar> qui représente le calendrier à utiliser.  
  
2. Déterminez les éléments de date et d’heure qui doivent apparaître dans la représentation sous forme de chaîne de la valeur de date et d’heure.  
  
3. Pour chaque élément de date et d’heure que vous souhaitez afficher, appelez la méthode `Get`... de l’objet de calendrier. . Les méthodes suivantes sont disponibles :  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, pour afficher l’année dans le calendrier approprié.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, pour afficher le mois dans le calendrier approprié.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, pour afficher le numéro du jour du mois dans le calendrier approprié.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, pour afficher l’heure du jour dans le calendrier approprié.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, pour afficher les minutes de l’heure dans le calendrier approprié.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, pour afficher les secondes de la minute dans le calendrier approprié.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, pour afficher les millisecondes de la seconde dans le calendrier approprié.  
  
## <a name="example"></a> Exemple  
 L’exemple affiche une date à l’aide de deux calendriers différents. Il affiche la date après avoir défini le calendrier hégirien comme calendrier par défaut pour la culture ar-JO et affiche la date à l’aide du calendrier persan, qui n’est pas pris en charge comme calendrier facultatif par la culture fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Chaque objet <xref:System.Globalization.CultureInfo> peut prendre en charge un ou plusieurs calendriers, indiqués par la propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A>. L’un d’eux est désigné comme calendrier par défaut de la culture et est retourné par la propriété <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> en lecture seule. Un autre des calendriers facultatifs peut être désigné comme calendrier par défaut en attribuant un objet <xref:System.Globalization.Calendar> qui représente ce calendrier à la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> retournée par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Toutefois, certains calendriers, tels que le calendrier persan représenté par la classe <xref:System.Globalization.PersianCalendar>, ne servent de calendriers facultatifs pour aucune culture.  
  
 L’exemple définit une classe utilitaire de calendrier réutilisable, `CalendarUtility`, pour gérer de nombreux détails de la génération de la représentation sous forme de chaîne d’une date à l’aide d’un calendrier particulier. La classe `CalendarUtility` possède les membres suivants :  
  
- Un constructeur paramétré dont le paramètre unique est un objet <xref:System.Globalization.Calendar> dans lequel la date doit être représentée. Il est assigné à un champ privé de la classe.  
  
- `CalendarExists`, méthode privée qui retourne une valeur booléenne indiquant si le calendrier représenté par l’objet `CalendarUtility` est pris en charge par l’objet <xref:System.Globalization.CultureInfo> qui est passé à la méthode comme paramètre. La méthode encapsule un appel à la méthode <xref:System.Array.Exists%2A?displayProperty=nameWithType>, à laquelle est passé le tableau <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>.  
  
- `HasSameName`, méthode privée assignée au délégué <xref:System.Predicate%601> qui est passé comme paramètre à la méthode <xref:System.Array.Exists%2A?displayProperty=nameWithType>. Chaque membre du tableau est passé à la méthode jusqu’à ce qu’elle retourne `true`. La méthode détermine si le nom d’un calendrier facultatif est identique à celui du calendrier représenté par l’objet `CalendarUtility`.  
  
- `DisplayDate`, méthode publique surchargée qui reçoit deux paramètres : une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> à exprimer dans le calendrier représenté par l’objet `CalendarUtility` et la culture dont les règles de mise en forme doivent être utilisées. La façon dont elle retourne la représentation sous forme de chaîne d’une date varie selon que le calendrier cible est pris en charge ou non par la culture dont les règles de mise en forme doivent être utilisées.  
  
 Quel que soit le calendrier utilisé pour créer une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> dans cet exemple, la valeur est généralement exprimée sous la forme d’une date du calendrier grégorien. En effet, les types <xref:System.DateTime> et <xref:System.DateTimeOffset> ne conservent pas les informations de calendrier. En interne, elles sont représentées comme nombre de graduations qui se sont écoulées depuis le 1er janvier 0001 à minuit. L’interprétation de ce nombre dépend du calendrier. Pour la plupart des cultures, le calendrier par défaut est le calendrier grégorien.  
  
## <a name="see-also"></a>Voir aussi

- [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)
