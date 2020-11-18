---
title: Utilisation des calendriers
ms.date: 04/01/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
ms.openlocfilehash: c30af36b3426c4abbdf9c55f6c9062a5d8fc8c23
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824250"
---
# <a name="work-with-calendars"></a>Utiliser des calendriers

Bien qu'une valeur de date et d'heure représente un moment donné, sa représentation sous forme de chaîne dépend de la culture, des conventions utilisées pour afficher des valeurs de date et d'heure par une culture spécifique et du calendrier utilisé par cette culture. Cette rubrique explore la prise en charge des calendriers dans .NET et traite de l’utilisation des classes Calendar lors de l’utilisation de valeurs de date.

## <a name="calendars-in-net"></a>Calendriers dans .NET

Tous les calendriers dans .NET dérivent de la <xref:System.Globalization.Calendar?displayProperty=nameWithType> classe, qui fournit l’implémentation de base du calendrier. Une des classes qui héritent de la classe <xref:System.Globalization.Calendar> est <xref:System.Globalization.EastAsianLunisolarCalendar>, qui constitue la base de tous les calendriers lunisolaires. .NET comprend les implémentations de calendrier suivantes :

- <xref:System.Globalization.ChineseLunisolarCalendar>, qui représente le calendrier lunisolaire chinois.

- <xref:System.Globalization.GregorianCalendar>, qui représente le calendrier grégorien. Ce calendrier est encore divisé en sous-types (tels que l'arabe et le français du Moyen-Orient) qui sont définis par l'énumération <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType>. La propriété <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> spécifie le sous-type du calendrier grégorien.

- <xref:System.Globalization.HebrewCalendar>, qui représente le calendrier hébreu.

- <xref:System.Globalization.HijriCalendar>, qui représente le calendrier Hijri.

- <xref:System.Globalization.JapaneseCalendar>, qui représente le calendrier japonais.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, qui représente le calendrier lunisolaire japonais.

- <xref:System.Globalization.JulianCalendar>, qui représente le calendrier julien.

- <xref:System.Globalization.KoreanCalendar>, qui représente le calendrier coréen.

- <xref:System.Globalization.KoreanLunisolarCalendar>, qui représente le calendrier lunisolaire coréen.

- <xref:System.Globalization.PersianCalendar>, qui représente le calendrier persan.

- <xref:System.Globalization.TaiwanCalendar>, qui représente le calendrier taïwanais.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, qui représente le calendrier lunisolaire taïwanais.

- <xref:System.Globalization.ThaiBuddhistCalendar>, qui représente le calendrier thaï bouddhiste.

- <xref:System.Globalization.UmAlQuraCalendar>, qui représente le calendrier Um Al Qura.

Un calendrier peut être utilisé de deux manières différentes :

- En tant que calendrier utilisé par une culture spécifique. Chaque objet <xref:System.Globalization.CultureInfo> possède un calendrier actuel, qui est celui que l'objet utilise actuellement. Les représentations sous forme de chaîne de toutes les valeurs de date et d'heure reflètent automatiquement la culture actuelle et le calendrier en cours. En général, le calendrier actuel est le calendrier par défaut de la culture. <xref:System.Globalization.CultureInfo> les objets ont également des calendriers facultatifs, qui incluent des calendriers supplémentaires que la culture peut utiliser.

- En tant que calendrier autonome, indépendant d'une culture spécifique. Dans ce cas, les méthodes <xref:System.Globalization.Calendar> sont utilisées pour exprimer des dates sous forme de valeurs qui reflètent le calendrier.

Notez que six classes de calendrier – <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar> et <xref:System.Globalization.TaiwanLunisolarCalendar> - peuvent être utilisées uniquement en tant que calendriers autonomes. Elles ne sont utilisées par aucune culture comme le calendrier par défaut ou comme calendrier facultatif.

## <a name="calendars-and-cultures"></a>Calendriers et cultures

Chaque culture a un calendrier par défaut, qui est défini par la propriété <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>. La propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> retourne un tableau d'objets <xref:System.Globalization.Calendar> qui spécifie tous les calendriers pris en charge par une culture particulière, y compris le calendrier par défaut de cette culture.

L'exemple suivant illustre les propriétés <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> et <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Il crée des objets `CultureInfo` pour les cultures thaï (Thaïlande) et japonaise (Japon) et affiche leurs calendriers par défaut et facultatifs. Notez que dans les deux cas, le calendrier par défaut de la culture est également inclus dans la collection <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Le calendrier actuellement utilisé par un objet <xref:System.Globalization.CultureInfo> particulier est défini par la propriété de la culture <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>. Un objet <xref:System.Globalization.DateTimeFormatInfo> de la culture est retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Lorsqu'une culture est créée, sa valeur par défaut est identique à celle de la propriété <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>. Toutefois, vous pouvez remplacer le calendrier actuel de la culture par n'importe quel calendrier contenu dans le tableau retourné par la propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Si vous essayez de définir le calendrier actuel à un calendrier qui n'est pas compris dans la valeur d'une propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>, une <xref:System.ArgumentException> est levée.

L'exemple suivant remplace le calendrier utilisé par la culture arabe (Arabie Saoudite). Il instancie d'abord une valeur <xref:System.DateTime> et l'affiche à l'aide de la culture actuelle, qui, dans ce cas, est l'anglais (États-unis) et le calendrier actuel de la culture (qui, dans ce cas, est le calendrier grégorien). Ensuite, il remplace la culture actuelle par l'arabe (Arabie Saoudite) et affiche la date en utilisant son calendrier Um Al Qura par défaut. Il appelle ensuite la méthode `CalendarExists` pour déterminer si le calendrier Hijri est pris en charge par la culture arabe (Arabie Saoudite). Étant donné que le calendrier est pris en charge, il modifie le calendrier Hijri en cours et affiche à nouveau la date. Notez que, dans chaque cas, la date est affichée à l'aide du calendrier actuel de la culture actuelle.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Dates et calendriers

À l'exception des constructeurs qui incluent un paramètre de type <xref:System.Globalization.Calendar> et permettent aux éléments d'une date (c'est-à-dire, le mois, le jour et l'année) de refléter des valeurs dans un calendrier indiqué, les valeurs de <xref:System.DateTime> et <xref:System.DateTimeOffset> sont toujours basées sur le calendrier grégorien. Cela signifie, par exemple, que la <xref:System.DateTime.Year%2A?displayProperty=nameWithType> retourne l'année dans le calendrier grégorien, tandis que la propriété <xref:System.DateTime.Day%2A?displayProperty=nameWithType> retourne le jour du mois dans le calendrier grégorien.

> [!IMPORTANT]
> Il est important de se souvenir qu'il existe une différence entre une valeur de date et sa représentation sous forme de chaîne. La première est basée sur le calendrier grégorien ; la dernière est basée sur le calendrier actuel d'une culture spécifique.

L'exemple suivant illustre cette différence entre les propriétés <xref:System.DateTime> et les méthodes <xref:System.Globalization.Calendar> correspondantes. Dans l'exemple, la culture actuelle est arabe (Égypte) et le calendrier actuel est Um Al Qura. Une valeur <xref:System.DateTime> est définie sur le quinzième jour du septième mois de 2011. Il est clair qu'elle est interprétée comme étant une date grégorienne, car ces mêmes valeurs sont retournées par la méthode <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lorsqu'elle utilise des conventions de la culture indifférente. La représentation sous forme de chaîne de la date qui est mise en forme à l'aide des conventions de la culture actuelle est 14/08/32, qui est la date équivalente dans le calendrier Um Al Qura. Ensuite, les membres de `DateTime` et `Calendar` sont utilisés pour retourner le jour, le mois et l'année de la valeur <xref:System.DateTime>. Dans chaque cas, les valeurs retournées par les membres <xref:System.DateTime> reflètent les valeurs du calendrier grégorien, tandis que les valeurs retournées par les membres <xref:System.Globalization.UmAlQuraCalendar> reflètent les valeurs du calendrier Um-Al Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>Instancier des dates en fonction d’un calendrier

Étant donné que les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sont basées sur le calendrier grégorien, vous devez appeler un constructeur surchargé qui inclut un paramètre de type <xref:System.Globalization.Calendar> pour instancier une valeur de date si vous souhaitez utiliser le jour, le mois ou les années d'un calendrier différent. Vous pouvez également appeler une des surcharges d'une méthode <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> d'un calendrier spécifique pour instancier un objet <xref:System.DateTime> en fonction des valeurs d'un calendrier particulier.

L'exemple suivant instancie une valeur <xref:System.DateTime> en passant un objet <xref:System.Globalization.HebrewCalendar> à un constructeur <xref:System.DateTime> et instancie une seconde valeur <xref:System.DateTime> en appelant la méthode <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>. Étant donné que les deux valeurs sont créées avec des valeurs identiques du calendrier hébreu, l'appel de la méthode <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> indique que les deux valeurs <xref:System.DateTime> sont égales.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Représenter des dates dans le calendrier actuel

Les méthodes de mise en forme de la date et de l'heure utilisent toujours le calendrier actuel en convertissant les dates en chaînes. Cela signifie que la représentation sous forme de chaîne de l'année, du mois et du jour du mois reflète le calendrier actuel et pas nécessairement le calendrier grégorien.

L'exemple suivant montre comment le calendrier actuel affecte la représentation sous forme de chaîne d'une date. Il remplace la culture actuelle par le chinois (traditionnel, Taïwan) et instancie une valeur de date. Il affiche ensuite le calendrier actuel et la date, remplace le calendrier actuel par <xref:System.Globalization.TaiwanCalendar> et affiche à nouveau le calendrier actuel et la date . La première fois que la date est affichée, elle est représentée sous la forme d'une date du calendrier grégorien. La seconde fois qu'elle est affichée, elle est représentée sous la forme d'une date du calendrier taïwanais.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Représenter des dates dans un calendrier non actuel

Pour représenter une date à l'aide d'un calendrier qui n'est pas le calendrier actuel d'une culture particulière, vous devez appeler des méthodes de cet objet <xref:System.Globalization.Calendar>. Par exemple, les méthodes <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> et <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> convertissent l'année, le mois et le jour en valeurs qui reflètent un calendrier particulier.

> [!WARNING]
> Étant donné que certains calendriers ne sont les calendriers facultatifs d'aucune culture, la représentation des dates dans ces calendriers requiert toujours l'appel de méthodes de calendrier. C'est le cas de tous les calendriers qui dérivent des classes <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar> et <xref:System.Globalization.PersianCalendar>.

L'exemple suivant utilise un objet <xref:System.Globalization.JulianCalendar> pour instancier une date, le 9 janvier 1905, dans le calendrier julien. Lorsque cette date est affichée à l'aide du calendrier par défaut (grégorien), elle est représentée sous la forme de 22 janvier 1905. Les appels de méthodes <xref:System.Globalization.JulianCalendar> individuelles permettent de représenter la date dans le calendrier julien.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Calendriers et plages de dates

La première date prise en charge par un calendrier est indiquée par la propriété <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> de ce calendrier. Pour la classe <xref:System.Globalization.GregorianCalendar>, cette date est le 1er janvier 0001 (notre ère). La plupart des autres calendriers dans .NET prennent en charge une date ultérieure. Le fait d'essayer d'utiliser une valeur de date et d'heure qui précède la première date prise en charge d'un calendrier lève une exception <xref:System.ArgumentOutOfRangeException>.

Toutefois, il existe une exception importante. La valeur par défaut (non initialisée) d'un objet <xref:System.DateTime> et d'un objet <xref:System.DateTimeOffset> est égale à la valeur <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType>. Si vous essayez de mettre en forme cette date dans un calendrier qui ne prend pas en charge le 1er janvier 0001 (notre ère) et vous ne fournissez pas de spécificateur de format, la méthode de mise en forme utilise le spécificateur de format "s" (modèle de date/heure pouvant être trié) à la place du spécificateur de format "G" (modèle de date/heure général). Par conséquent, l'opération de mise en forme ne lève pas d'exception <xref:System.ArgumentOutOfRangeException>. Au lieu de cela, elle retourne la date non prise en charge. L'exemple suivant illustre cela en affichant la valeur <xref:System.DateTime.MinValue?displayProperty=nameWithType> lorsque la culture actuelle est définie sur Japonais (Japon) avec le calendrier japonais, et Arabe (Égypte) avec le calendrier Um Al Qura. Il définit également la culture actuelle sur Anglais (États-Unis) et appelle la méthode <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> à chacun de ces objets <xref:System.Globalization.CultureInfo>. Dans chaque cas, la date est affichée à l’aide du modèle de date/heure pouvant être trié.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Utiliser des ères

Les calendriers divisent en général les dates en ères. Toutefois, les <xref:System.Globalization.Calendar> classes dans .net ne prennent pas en charge chaque ère définie par un calendrier, et la plupart des <xref:System.Globalization.Calendar> classes ne prennent en charge qu’une seule ère. Seules les classes <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar> prennent en charge plusieurs ères.

> [!IMPORTANT]
> L’ère Reiwa, une nouvelle ère dans <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar> , commence le 1er mai 2019. Ce changement affecte toutes les applications qui utilisent ces calendriers. Pour plus d’informations, consultez les articles suivants :
>
> - [Gestion d’une nouvelle ère dans le calendrier japonais dans .net](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), qui documente les fonctionnalités ajoutées à .net pour prendre en charge les calendriers avec plusieurs ères et présente les meilleures pratiques à utiliser lors de la gestion des calendriers à plusieurs ère.
> - [Préparez votre application pour la modification de l’ère japonaise](/windows/uwp/design/globalizing/japanese-era-change), qui fournit des informations sur le test de vos applications sur Windows pour garantir leur disponibilité pour la modification de l’ère.
> - [Résumé des nouvelles mises à jour de l’ère japonaise pour .NET Framework](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), qui répertorie les mises à jour .NET Framework pour les différentes versions de Windows qui sont liées à la nouvelle ère du calendrier japonais, note les nouvelles fonctionnalités de .NET Framework pour la prise en charge de plusieurs ère et comprend des éléments à rechercher dans le test de vos applications.

Une ère dans la plupart des calendriers indique une période très longue. Dans le calendrier grégorien, par exemple, l’ère actuelle s’étend sur plus de deux depuis. Pour le <xref:System.Globalization.JapaneseCalendar> et le <xref:System.Globalization.JapaneseLunisolarCalendar> , les deux calendriers qui prennent en charge plusieurs ères, ce n’est pas le cas. Une ère correspond à la période du règne d’un empereur. La prise en charge de plusieurs ères, en particulier lorsque la limite supérieure de l’ère actuelle est inconnue, pose des défis particuliers.

### <a name="eras-and-era-names"></a>Ères et noms d’ères

Dans .NET, les entiers qui représentent les ères pris en charge par une implémentation de calendrier particulière sont stockés dans l’ordre inverse dans le <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tableau. L’ère actuelle (qui est l’ère avec la dernière plage de temps) est à l’index zéro et, pour les <xref:System.Globalization.Calendar> classes qui prennent en charge plusieurs ères, chaque index successif reflète l’ère précédente. La propriété statique <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> définit l'index de l'ère actuelle dans le tableau <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> ; il s'agit d'une constante dont la valeur est toujours zéro. Les classes <xref:System.Globalization.Calendar> individuelles incluent également les champs static qui retournent la valeur de l’ère actuelle. Elles sont répertoriées dans le tableau suivant.

| Classe de calendrier                                        | Champ d'ère actuelle                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

Le nom qui correspond à un numéro d'ère particulier peut être extrait en passant le numéro d'ère à la méthode <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> ou <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType>. L'exemple suivant appelle ces méthodes pour extraire des informations sur la prise en charge de l'ère dans la classe <xref:System.Globalization.GregorianCalendar>. Il affiche la date du calendrier grégorien qui correspond au 1er janvier de la deuxième année de l’ère actuelle, ainsi que la date du calendrier grégorien qui correspond au 1er janvier de la deuxième année de chaque ère de calendrier japonais prise en charge.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

En outre, la chaîne de format de date et d'heure personnalisée « g » inclut un nom d'ère du calendrier dans la représentation sous forme de chaîne d'une date et d'une heure. Pour plus d’informations, consultez [chaînes de format de date et d’heure personnalisées](../base-types/custom-date-and-time-format-strings.md).

### <a name="instantiatie-a-date-with-an-era"></a>Instantiatie une date avec une ère

Pour les deux <xref:System.Globalization.Calendar> classes qui prennent en charge plusieurs ères, une date comprenant une année, un mois et un jour de la valeur de mois peut être ambiguë. Par exemple, toutes les ères prises en charge par <xref:System.Globalization.JapaneseCalendar> ont des années dont le nombre est 1. En règle générale, si une ère n'est pas spécifiée, les méthodes de date et d'heure et de calendrier supposent que les valeurs appartiennent à l'ère actuelle. Cela est vrai pour les <xref:System.DateTime.%23ctor%2A> <xref:System.DateTimeOffset.%23ctor%2A> constructeurs et qui incluent des paramètres de type <xref:System.Globalization.Calendar> , ainsi que les méthodes [JapaneseCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) et [JapaneseLunisolarCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) . L’exemple suivant instancie une date qui représente le 1er janvier de la deuxième année d’une ère non spécifiée. Si vous exécutez l’exemple lorsque l’ère Reiwa est l’ère actuelle, la date est interprétée comme la deuxième année de l’ère Reiwa. L’ère, 令和, précède l’année dans la chaîne retournée par la <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> méthode et correspond au 1er janvier 2020 dans le calendrier grégorien. (L’ère Reiwa commence dans l’année 2019 du calendrier grégorien.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Toutefois, si l’ère change, l’objectif de ce code devient ambigu. La date est-elle destinée à représenter la deuxième année de l’ère actuelle, ou est-elle destinée à représenter la deuxième année de l’ère Heisei ? Il existe deux façons d’éviter cette ambiguïté :

- Instanciez la valeur de date et d’heure à l’aide de la classe par défaut <xref:System.Globalization.GregorianCalendar> . Vous pouvez ensuite utiliser le calendrier japonais ou le calendrier luni-solaire japonais pour la représentation sous forme de chaîne de dates, comme le montre l’exemple suivant.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Appelez une méthode de date et d’heure qui spécifie explicitement une ère. Celle-ci comprend les méthodes suivantes :

  - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)>Méthode de la <xref:System.Globalization.JapaneseCalendar> classe ou <xref:System.Globalization.JapaneseLunisolarCalendar> .

  - <xref:System.DateTime>Ou une <xref:System.DateTimeOffset> méthode d’analyse, telle que <xref:System.DateTime.Parse%2A> , <xref:System.DateTime.TryParse%2A> , <xref:System.DateTime.ParseExact%2A> ou <xref:System.DateTime.TryParseExact%2A> , qui comprend la chaîne à analyser et éventuellement un <xref:System.Globalization.DateTimeStyles> argument si la culture actuelle est Japanese-Japan (« ja-JP ») et que le calendrier de la culture est le <xref:System.Globalization.JapaneseCalendar> . La chaîne à analyser doit inclure l’ère.

  - <xref:System.DateTime>Ou une <xref:System.DateTimeOffset> méthode d’analyse qui comprend un `provider` paramètre de type <xref:System.IFormatProvider> . `provider` doit être un <xref:System.Globalization.CultureInfo> objet qui représente la culture Japanese-Japan (« ja-JP ») dont le calendrier actuel est <xref:System.Globalization.JapaneseCalendar> ou un <xref:System.Globalization.DateTimeFormatInfo> objet dont la <xref:System.Globalization.DateTimeFormatInfo.Calendar> propriété a la valeur <xref:System.Globalization.JapaneseCalendar> . La chaîne à analyser doit inclure l’ère.

  L’exemple suivant utilise trois de ces méthodes pour instancier une date et une heure dans l’ère Meiji, qui a débuté le 8 septembre 1868 et se termine le 29 juillet 1912.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Lorsque vous travaillez avec des calendriers qui prennent en charge plusieurs ères, utilisez *toujours* la date grégorienne pour instancier une date, ou spécifiez l’ère quand vous instanciez une date et une heure en fonction de ce calendrier.

En spécifiant une ère pour la <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> méthode, vous fournissez l’index de l’ère dans la <xref:System.Globalization.Calendar.Eras> propriété du calendrier. Toutefois, pour les calendriers dont les ères sont sujettes à modification, ces index ne sont pas des valeurs constantes. l’ère actuelle se trouve à l’index 0 et l’ère la plus ancienne est au niveau de l’index `Eras.Length - 1` . Lorsqu’une nouvelle ère est ajoutée à un calendrier, les index des ères précédentes augmentent d’une unité. Vous pouvez fournir l’index d’ère approprié comme suit :

- Pour les dates de l’ère actuelle, utilisez toujours la propriété du calendrier <xref:System.Globalization.Calendar.CurrentEra> .

- Pour les dates dans une ère spécifiée, utilisez la <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> méthode pour récupérer l’index qui correspond à un nom d’ère spécifié. Cela requiert que <xref:System.Globalization.JapaneseCalendar> soit le calendrier actuel de l' <xref:System.Globalization.CultureInfo> objet qui représente la culture ja-JP.  (Cette technique fonctionne également pour le <xref:System.Globalization.JapaneseLunisolarCalendar> , car elle prend en charge les mêmes ères que le <xref:System.Globalization.JapaneseCalendar> .) L’exemple précédent illustre cette approche.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Calendriers, ères et plages de dates : contrôles de plage souple

Comme les calendriers individuels ont des plages de dates prises en charge, les ères dans les <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> classes et ont également des plages prises en charge. Auparavant, .NET utilisait des contrôles de plage d’ère stricts pour s’assurer qu’une date spécifique à l’ère était comprise dans la plage de cette ère. Autrement dit, si une date est en dehors de la plage de l’ère spécifiée, la méthode lève une <xref:System.ArgumentOutOfRangeException> . À l’heure actuelle, .NET utilise la vérification à plage déstricte par défaut. Les mises à jour de toutes les versions de .NET ont introduit des contrôles de plage d’ère assouplis ; la tentative d’instanciation d’une date spécifique à l’ère qui est en dehors de la plage de l’ère spécifiée est dépassée dans l’ère suivante et aucune exception n’est levée.

L’exemple suivant tente d’instancier une date de l’année 65th de l’ère Showa, qui a débuté le 25 décembre 1926 et a pris fin le 7 janvier 1989. Cette date correspond au 9 janvier 1990, qui est en dehors de la plage de l’ère Showa dans le <xref:System.Globalization.JapaneseCalendar> . Comme l’illustre la sortie de l’exemple, la date affichée par l’exemple est le 9 janvier 1990, dans la deuxième année de l’ère Heisei.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Si les contrôles de plage souple ne sont pas souhaitables, vous pouvez restaurer des contrôles de plage stricts de plusieurs façons, selon la version de .NET sur laquelle votre application s’exécute :

- **.Net Core :** Ajoutez le code suivant au *.netcore.runtime.jssur* le fichier de configuration :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4,6 ou version ultérieure :** Définissez le commutateur AppContext suivant dans le fichier *app.config* :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 ou version antérieure :** Définissez la valeur de Registre suivante :

   |  |  |
   |--|--|
   | **Clé** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\ . NETFramework\AppContext** |
   | **Nom** | Switch.SysTEM. Globalization. EnforceJapaneseEraYearRanges |
   | **Type** | REG_SZ |
   | **Valeur** | true |

Si les vérifications de plage strictes sont activées, l’exemple précédent lève une <xref:System.ArgumentOutOfRangeException> et affiche la sortie suivante :

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Représenter des dates dans des calendriers avec plusieurs ères

Si un objet <xref:System.Globalization.Calendar> prend en charge les ères et est le calendrier actuel d’un objet <xref:System.Globalization.CultureInfo>, l’ère est comprise dans la représentation sous forme de chaîne d’une valeur de date et d’heure pour les modèles de date et d’heure complètes, de date longue et de date courte. L’exemple suivant illustre ces modèles de date lorsque la culture actuelle est le japonais (Japon) et le calendrier actuel est le japonais.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> La <xref:System.Globalization.JapaneseCalendar> classe est la seule classe Calendar dans .net qui prend en charge les dates dans plusieurs ères et qui peut être le calendrier actuel d’un <xref:System.Globalization.CultureInfo> objet, en particulier, d’un <xref:System.Globalization.CultureInfo> objet qui représente la culture japonaise (Japon).

Pour tous les calendriers, le spécificateur de format personnalisé « g » inclut l'ère dans la chaîne de résultat. L'exemple suivant utilise la chaîne de format personnalisé de "MM-jj-aaaa g" pour inclure l'ère dans la chaîne de résultat quand le calendrier actuel est le calendrier grégorien.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Dans les cas où la représentation sous forme de chaîne d'une date est exprimée dans un calendrier qui n'est pas le calendrier en cours, la classe <xref:System.Globalization.Calendar> inclut une méthode <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> qui peut être utilisée avec les méthodes <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> et <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> pour indiquer clairement une date ainsi que l'ère à laquelle elle appartient. L'exemple suivant utilise la classe <xref:System.Globalization.JapaneseLunisolarCalendar> pour fournir une illustration. Toutefois, notez que le fait d'inclure un nom ou une abréviation explicite au lieu d'un entier pour l'ère dans la chaîne de résultat requiert d'instancier un objet <xref:System.Globalization.DateTimeFormatInfo> et de faire de <xref:System.Globalization.JapaneseCalendar> son calendrier actuel. (Le calendrier <xref:System.Globalization.JapaneseLunisolarCalendar> ne peut pas être le calendrier actuel d'une culture, mais dans ce cas, les deux calendriers partagent les mêmes ères.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

Dans les calendriers japonais, la première année d’une ère est appelée Gannen (元年). Par exemple, au lieu de Heisei 1, la première année de l’ère Heisei peut être décrite comme Heisei gannen. .NET adopte cette Convention dans les opérations de mise en forme des dates et heures mises en forme avec les chaînes de format de date et d’heure standard ou personnalisées suivantes lorsqu’elles sont utilisées avec un <xref:System.Globalization.CultureInfo> objet qui représente la culture Japanese-Japan (« ja-JP ») avec la <xref:System.Globalization.JapaneseCalendar> classe :

- [Le modèle de date longue](../base-types/standard-date-and-time-format-strings.md#LongDate), indiqué par la chaîne de format de date et d’heure standard « D ».
- [Modèle d’heure longue de date complète](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), indiqué par la chaîne de format de date et d’heure standard "F".
- [Modèle d’heure abrégée de date complète](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), indiqué par la chaîne de format de date et d’heure standard "f".
- [Modèle d’année/mois](../base-types/standard-date-and-time-format-strings.md#YearMonth), indiqué par la chaîne de format de date et d’heure standard y "ou" y ".
- [La [chaîne de format de date et d’heure personnalisée](../base-types/custom-date-and-time-format-strings.md)« GGY » 年 « » ou «ggy年 ».

Par exemple, l’exemple suivant affiche une date dans la première année de l’ère Heisei dans le <xref:System.Globalization.JapaneseCalendar> .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Si ce comportement n’est pas souhaitable dans les opérations de mise en forme, vous pouvez restaurer le comportement précédent, qui représente toujours la première année d’une ère sous la forme « 1 » plutôt que « gannen », en procédant comme suit, selon la version de .NET :

- **.Net Core :** Ajoutez le code suivant au *.netcore.runtime.jssur* le fichier de configuration :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4,6 ou version ultérieure :** Définissez le commutateur AppContext suivant dans le fichier *app.config* :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 ou version antérieure :** Définissez la valeur de Registre suivante :

   |  |  |
   |--|--|
   | **Clé** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\ . NETFramework\AppContext** |
   | **Nom** | Switch.SysTEM. Globalization. FormatJapaneseFirstYearAsANumber |
   | **Type** | REG_SZ |
   | **Valeur** | true |

Avec la prise en charge de gannen dans les opérations de mise en forme désactivées, l’exemple précédent affiche la sortie suivante :

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET a également été mis à jour afin que les opérations d’analyse de date et d’heure prennent en charge les chaînes qui contiennent l’année représentée sous la forme « 1 » ou gannen. Même si vous n’avez pas besoin de le faire, vous pouvez restaurer le comportement précédent pour ne reconnaître que « 1 » comme première année d’une ère. Pour ce faire, vous pouvez procéder comme suit, selon la version de .NET :

- **.Net Core :** Ajoutez le code suivant au *.netcore.runtime.jssur* le fichier de configuration :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4,6 ou version ultérieure :** Définissez le commutateur AppContext suivant dans le fichier *app.config* :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 ou version antérieure :** Définissez la valeur de Registre suivante :

   |  |  |
   |--|--|
   | **Clé** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\ . NETFramework\AppContext** |
   | **Nom** | Switch.SysTEM. Globalization. EnforceLegacyJapaneseDateParsing |
   | **Type** | REG_SZ |
   | **Valeur** | true |

## <a name="see-also"></a>Voir aussi

- [Comment : afficher des dates dans des calendriers non grégoriens](../base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Exemple : utilitaire de plage de semaine du calendrier](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Classe de calendrier](xref:System.Globalization.Calendar)
