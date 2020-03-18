---
title: Utilisation des calendriers
ms.date: 04/01/2019
ms.technology: dotnet-standard
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
ms.openlocfilehash: de8e5a03c769a22f3320c7785706555898bf8c1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400588"
---
# <a name="work-with-calendars"></a>Travailler avec des calendriers

Bien qu'une valeur de date et d'heure représente un moment donné, sa représentation sous forme de chaîne dépend de la culture, des conventions utilisées pour afficher des valeurs de date et d'heure par une culture spécifique et du calendrier utilisé par cette culture. Ce sujet explore le support pour les calendriers en .NET et discute de l’utilisation des classes de calendrier lorsque vous travaillez avec les valeurs de date.

## <a name="calendars-in-net"></a>Calendriers en .NET

Tous les calendriers en <xref:System.Globalization.Calendar?displayProperty=nameWithType> .NET dérivent de la classe, qui fournit la mise en œuvre du calendrier de base. Une des classes qui héritent de la classe <xref:System.Globalization.Calendar> est <xref:System.Globalization.EastAsianLunisolarCalendar>, qui constitue la base de tous les calendriers lunisolaires. .NET inclut les implémentations du calendrier suivantes :

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

- En tant que calendrier utilisé par une culture spécifique. Chaque objet <xref:System.Globalization.CultureInfo> possède un calendrier actuel, qui est celui que l'objet utilise actuellement. Les représentations sous forme de chaîne de toutes les valeurs de date et d'heure reflètent automatiquement la culture actuelle et le calendrier en cours. En général, le calendrier actuel est le calendrier par défaut de la culture. <xref:System.Globalization.CultureInfo>les objets ont également des calendriers optionnels, qui comprennent des calendriers supplémentaires que la culture peut utiliser.

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

### <a name="instantiate-dates-based-on-a-calendar"></a>Dates instantanées basées sur un calendrier

Étant donné que les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sont basées sur le calendrier grégorien, vous devez appeler un constructeur surchargé qui inclut un paramètre de type <xref:System.Globalization.Calendar> pour instancier une valeur de date si vous souhaitez utiliser le jour, le mois ou les années d'un calendrier différent. Vous pouvez également appeler une des surcharges d'une méthode <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> d'un calendrier spécifique pour instancier un objet <xref:System.DateTime> en fonction des valeurs d'un calendrier particulier.

L'exemple suivant instancie une valeur <xref:System.DateTime> en passant un objet <xref:System.Globalization.HebrewCalendar> à un constructeur <xref:System.DateTime> et instancie une seconde valeur <xref:System.DateTime> en appelant la méthode <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>. Étant donné que les deux valeurs sont créées avec des valeurs identiques du calendrier hébreu, l'appel de la méthode <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> indique que les deux valeurs <xref:System.DateTime> sont égales.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Représenter les dates dans le calendrier actuel

Les méthodes de mise en forme de la date et de l'heure utilisent toujours le calendrier actuel en convertissant les dates en chaînes. Cela signifie que la représentation sous forme de chaîne de l'année, du mois et du jour du mois reflète le calendrier actuel et pas nécessairement le calendrier grégorien.

L'exemple suivant montre comment le calendrier actuel affecte la représentation sous forme de chaîne d'une date. Il remplace la culture actuelle par le chinois (traditionnel, Taïwan) et instancie une valeur de date. Il affiche ensuite le calendrier actuel et la date, remplace le calendrier actuel par <xref:System.Globalization.TaiwanCalendar> et affiche à nouveau le calendrier actuel et la date . La première fois que la date est affichée, elle est représentée sous la forme d'une date du calendrier grégorien. La seconde fois qu'elle est affichée, elle est représentée sous la forme d'une date du calendrier taïwanais.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Représenter les dates dans un calendrier non courant

Pour représenter une date à l'aide d'un calendrier qui n'est pas le calendrier actuel d'une culture particulière, vous devez appeler des méthodes de cet objet <xref:System.Globalization.Calendar>. Par exemple, les méthodes <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> et <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> convertissent l'année, le mois et le jour en valeurs qui reflètent un calendrier particulier.

> [!WARNING]
> Étant donné que certains calendriers ne sont les calendriers facultatifs d'aucune culture, la représentation des dates dans ces calendriers requiert toujours l'appel de méthodes de calendrier. C'est le cas de tous les calendriers qui dérivent des classes <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar> et <xref:System.Globalization.PersianCalendar>.

L'exemple suivant utilise un objet <xref:System.Globalization.JulianCalendar> pour instancier une date, le 9 janvier 1905, dans le calendrier julien. Lorsque cette date est affichée à l'aide du calendrier par défaut (grégorien), elle est représentée sous la forme de 22 janvier 1905. Les appels de méthodes <xref:System.Globalization.JulianCalendar> individuelles permettent de représenter la date dans le calendrier julien.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Calendriers et plages de dates

La première date prise en charge par un calendrier est indiquée par la propriété <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> de ce calendrier. Pour la classe <xref:System.Globalization.GregorianCalendar>, cette date est le 1er janvier 0001 (notre ère). La plupart des autres calendriers en .NET prennent en charge une date ultérieure. Le fait d'essayer d'utiliser une valeur de date et d'heure qui précède la première date prise en charge d'un calendrier lève une exception <xref:System.ArgumentOutOfRangeException>.

Toutefois, il existe une exception importante. La valeur par défaut (non initialisée) d'un objet <xref:System.DateTime> et d'un objet <xref:System.DateTimeOffset> est égale à la valeur <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType>. Si vous essayez de formater cette date dans un calendrier qui ne prend pas en charge Janvier 1, 0001 C.E. et vous ne fournissez pas de spécificateur de format, la méthode de formatage utilise le specificateur de format « s » (date/heure triable) au lieu du spécificateur de format « G » (date générale/modèle d’heure). Par conséquent, l'opération de mise en forme ne lève pas d'exception <xref:System.ArgumentOutOfRangeException>. Au lieu de cela, elle retourne la date non prise en charge. L'exemple suivant illustre cela en affichant la valeur <xref:System.DateTime.MinValue?displayProperty=nameWithType> lorsque la culture actuelle est définie sur Japonais (Japon) avec le calendrier japonais, et Arabe (Égypte) avec le calendrier Um Al Qura. Il définit également la culture actuelle sur Anglais (États-Unis) et appelle la méthode <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> à chacun de ces objets <xref:System.Globalization.CultureInfo>. Dans chaque cas, la date est affichée à l’aide du modèle de date/heure pouvant être trié.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Travailler avec les époques

Les calendriers divisent en général les dates en ères. Cependant, <xref:System.Globalization.Calendar> les classes en .NET ne prennent pas en charge <xref:System.Globalization.Calendar> toutes les époques définies par un calendrier, et la plupart des classes ne prennent en charge qu’une seule époque. Seules les classes <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar> prennent en charge plusieurs ères.

> [!IMPORTANT]
> L’ère Reiwa, une <xref:System.Globalization.JapaneseCalendar> nouvelle <xref:System.Globalization.JapaneseLunisolarCalendar>ère dans le et , commence le 1er mai 2019. Ce changement affecte toutes les applications qui utilisent ces calendriers. Pour plus d’informations, consultez les articles suivants :
>
> - [Gérer une nouvelle ère dans le calendrier japonais en .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), qui documente les fonctionnalités ajoutées à .NET pour prendre en charge les calendriers avec des époques multiples et discute des meilleures pratiques à utiliser lors de la manipulation des calendriers multi-ères.
> - [Préparez votre application pour le changement de l’ère japonaise](/windows/uwp/design/globalizing/japanese-era-change), qui fournit des informations sur le test de vos applications sur Windows pour s’assurer qu’ils sont prêts pour le changement d’ère.
> - [Résumé des nouvelles mises à jour de l’ère japonaise pour .NET Framework](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), qui répertorie les mises à jour .NET Framework pour les versions Windows individuelles qui sont liées à la nouvelle ère du calendrier japonais, note de nouvelles fonctionnalités .NET Framework pour le support multi-ère, et comprend des choses à rechercher dans le test de vos applications.

Une époque dans la plupart des calendriers dénote une période de temps extrêmement longue. Dans le calendrier grégorien, par exemple, l’ère actuelle s’étend sur plus de deux millénaires. Pour <xref:System.Globalization.JapaneseCalendar> le <xref:System.Globalization.JapaneseLunisolarCalendar>et le , les deux calendriers qui prennent en charge les époques multiples, ce n’est pas le cas. Une époque correspond à la période du règne d’un empereur. Le soutien à de multiples époques, en particulier lorsque la limite supérieure de l’ère actuelle est inconnue, pose des défis particuliers.

### <a name="eras-and-era-names"></a>Eras et noms d’époque

Dans .NET, les intégrés qui représentent les époques supportées par <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> une implémentation de calendrier particulière sont stockés dans l’ordre inverse dans le tableau. L’ère actuelle (qui est l’ère avec la dernière <xref:System.Globalization.Calendar> plage de temps) est à l’indice zéro, et pour les classes qui soutiennent des époques multiples, chaque indice successif reflète l’ère précédente. La propriété statique <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> définit l'index de l'ère actuelle dans le tableau <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> ; il s'agit d'une constante dont la valeur est toujours zéro. Les classes <xref:System.Globalization.Calendar> individuelles incluent également les champs static qui retournent la valeur de l’ère actuelle. Elles sont répertoriées dans le tableau suivant.

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

Le nom qui correspond à un numéro d'ère particulier peut être extrait en passant le numéro d'ère à la méthode <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> ou <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType>. L'exemple suivant appelle ces méthodes pour extraire des informations sur la prise en charge de l'ère dans la classe <xref:System.Globalization.GregorianCalendar>. Il affiche la date de calendrier grégorienne qui correspond au 1er janvier de la deuxième année de l’ère actuelle, ainsi que la date du calendrier grégorien qui correspond au 1er janvier de la deuxième année de chaque ère de calendrier japonais soutenue.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

En outre, la chaîne de format de date et d'heure personnalisée « g » inclut un nom d'ère du calendrier dans la représentation sous forme de chaîne d'une date et d'une heure. Pour plus d’informations, voir [chaînes de format de date et d’heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiatie-a-date-with-an-era"></a>Instantiatie une date avec une époque

Pour les <xref:System.Globalization.Calendar> deux classes qui soutiennent des époques multiples, une date qui se compose d’une année, d’un mois et d’une valeur du jour du mois peuvent être ambigus. Par exemple, toutes les <xref:System.Globalization.JapaneseCalendar> époques soutenues par les années ont dont le nombre est 1. En règle générale, si une ère n'est pas spécifiée, les méthodes de date et d'heure et de calendrier supposent que les valeurs appartiennent à l'ère actuelle. Cela est vrai <xref:System.DateTime.%23ctor%2A> <xref:System.DateTimeOffset.%23ctor%2A> pour les et les <xref:System.Globalization.Calendar>constructeurs qui comprennent des paramètres de type , ainsi que le [JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) et [japaneseLunisolarCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) méthodes. L’exemple suivant est instantané d’une date qui représente le 1er janvier de la deuxième année d’une époque non précisée. Si vous exécutez l’exemple lorsque l’ère Reiwa est l’ère actuelle, la date est interprétée comme la deuxième année de l’ère Reiwa. L’époque, l’époque, précède l’année de la chaîne retournée par la <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> méthode et correspond au 1er janvier 2020, dans le calendrier grégorien. (L’ère Reiwa commence en 2019 du calendrier grégorien.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Cependant, si l’ère change, l’intention de ce code devient ambigu. La date est-elle destinée à représenter la deuxième année de l’ère actuelle, ou est-elle destinée à représenter la deuxième année de l’ère Heisei ? Il y a deux façons d’éviter cette ambiguïté :

- Instantané de la date et de <xref:System.Globalization.GregorianCalendar> la valeur de l’heure à l’aide de la classe par défaut. Vous pouvez ensuite utiliser le calendrier japonais ou le calendrier japonais Lunisolar pour la représentation des chaînes de dates, comme le montre l’exemple suivant.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Appelez une méthode de date et d’heure qui spécifie explicitement une époque. Celle-ci comprend les méthodes suivantes :

  - La <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> méthode <xref:System.Globalization.JapaneseCalendar> de <xref:System.Globalization.JapaneseLunisolarCalendar> la classe ou.

  - Une <xref:System.DateTime> <xref:System.DateTimeOffset> méthode d’analyse ou <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A>d’analyse, <xref:System.DateTime.ParseExact%2A>comme , , <xref:System.DateTime.TryParseExact%2A>ou , qui <xref:System.Globalization.DateTimeStyles> comprend la chaîne à analyser et optionnellement un argument si la <xref:System.Globalization.JapaneseCalendar>culture actuelle est japonais-Japon ("ja-JP") et le calendrier de cette culture est le . La corde à analyser doit inclure l’époque.

  - Une <xref:System.DateTime> <xref:System.DateTimeOffset> méthode d’analyse ou `provider` d’analyse qui comprend un paramètre de type <xref:System.IFormatProvider>. `provider`doit être <xref:System.Globalization.CultureInfo> soit un objet qui représente la culture japonaise-japonaise ("ja-JP") dont le calendrier actuel <xref:System.Globalization.JapaneseCalendar> est ou <xref:System.Globalization.DateTimeFormatInfo> un objet dont <xref:System.Globalization.DateTimeFormatInfo.Calendar> la propriété est <xref:System.Globalization.JapaneseCalendar>. La corde à analyser doit inclure l’époque.

  L’exemple suivant utilise trois de ces méthodes pour instantané une date et une heure dans l’ère Meiji, qui a commencé le 8 septembre 1868, et a pris fin le 29 juillet 1912.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Lorsque vous travaillez avec des calendriers qui prennent en charge plusieurs époques, utilisez *toujours* la date grégorienne pour instantanér une date, ou spécifiez l’époque où vous instantanéez une date et une heure basées sur ce calendrier.

En spécifiant <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> une ère à la méthode, vous fournissez l’index de l’époque dans la propriété du <xref:System.Globalization.Calendar.Eras> calendrier. Pour les calendriers dont l’époque est sujette à changement, ces indices ne sont pas des valeurs constantes; l’ère actuelle est à l’indice 0, et l’ère la plus ancienne est à l’indice `Eras.Length - 1`. Lorsqu’une nouvelle ère est ajoutée à un calendrier, les indices des époques précédentes augmentent d’un point. Vous pouvez fournir l’indice d’époque approprié comme suit :

- Pour les dates de l’ère actuelle, utilisez toujours la propriété du <xref:System.Globalization.Calendar.CurrentEra> calendrier.

- Pour les dates dans une <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> ère spécifiée, utilisez la méthode pour récupérer l’index qui correspond à un nom d’époque spécifié. Cela exige <xref:System.Globalization.JapaneseCalendar> que le calendrier <xref:System.Globalization.CultureInfo> actuel de l’objet qui représente la culture ja-JP.  (Cette technique fonctionne <xref:System.Globalization.JapaneseLunisolarCalendar> aussi bien, car elle supporte <xref:System.Globalization.JapaneseCalendar>les mêmes époques que le .) L’exemple précédent illustre cette approche.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Calendriers, époques et plages de dates : vérifications de la plage décontractée

Tout comme les calendriers individuels ont pris en <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> charge les plages de date, les époques dans le et les classes ont également pris en charge les gammes. Auparavant, .NET utilisait des contrôles stricts de portée d’époque pour s’assurer qu’une date spécifique à l’ère se situait dans la fourchette de cette époque. Autrement dit, si une date est en dehors de la <xref:System.ArgumentOutOfRangeException>plage de l’ère spécifiée, la méthode jette un . Actuellement, .NET utilise la vérification à distance détendue par défaut. Mises à jour de toutes les versions de .NET introduit des contrôles de plage d’ère détendue; la tentative d’instantanéiser une date spécifique à l’époque qui est en dehors de la portée de l’ère spécifiée "déborde" dans l’ère suivante, et aucune exception n’est jetée.

L’exemple suivant tente d’instantané une date dans la 65e année de l’ère Showa, qui a commencé le 25 Décembre 1926 et a pris fin le 7 Janvier 1989. Cette date correspond au 9 janvier 1990, qui est en dehors <xref:System.Globalization.JapaneseCalendar>de la gamme de l’ère Showa dans le . Comme l’illustre la sortie de l’exemple, la date affichée par l’exemple est le 9 janvier 1990, la deuxième année de l’ère Heisei.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Si les contrôles de plage détendus ne sont pas souhaitables, vous pouvez rétablir des contrôles de portée stricts de plusieurs façons, selon la version de .NET sur laquelle votre application est en cours d’exécution:

- **.NET Core:** Ajoutez ce qui suit au fichier *config .netcore.runtime.json* :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4.6 ou plus tard :** Définissez le commutateur AppContext suivant dans le fichier *app.config* :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 ou plus tôt :** Définissez la valeur du registre suivant :

   |  |  |
   |--|--|
   | **Clé** | **HKEY_LOCAL_MACHINE-Software.Microsoft\\. NETFramework-AppContext** |
   | **Nom   ** | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   | **Type** | REG_SZ |
   | **Valeur** | true |

Avec des contrôles de portée stricts <xref:System.ArgumentOutOfRangeException> activés, l’exemple précédent jette un et affiche la sortie suivante:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Représenter les dates dans les calendriers à plusieurs époques

Si un objet <xref:System.Globalization.Calendar> prend en charge les ères et est le calendrier actuel d’un objet <xref:System.Globalization.CultureInfo>, l’ère est comprise dans la représentation sous forme de chaîne d’une valeur de date et d’heure pour les modèles de date et d’heure complètes, de date longue et de date courte. L’exemple suivant illustre ces modèles de date lorsque la culture actuelle est le japonais (Japon) et le calendrier actuel est le japonais.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> La <xref:System.Globalization.JapaneseCalendar> classe est la seule classe de calendrier en .NET qui prend en charge <xref:System.Globalization.CultureInfo> les dates dans <xref:System.Globalization.CultureInfo> plus d’une époque et qui peut être le calendrier actuel d’un objet - en particulier, d’un objet qui représente la culture japonaise (Japon).

Pour tous les calendriers, le spécificateur de format personnalisé « g » inclut l'ère dans la chaîne de résultat. L'exemple suivant utilise la chaîne de format personnalisé de "MM-jj-aaaa g" pour inclure l'ère dans la chaîne de résultat quand le calendrier actuel est le calendrier grégorien.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Dans les cas où la représentation sous forme de chaîne d'une date est exprimée dans un calendrier qui n'est pas le calendrier en cours, la classe <xref:System.Globalization.Calendar> inclut une méthode <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> qui peut être utilisée avec les méthodes <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> et <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> pour indiquer clairement une date ainsi que l'ère à laquelle elle appartient. L'exemple suivant utilise la classe <xref:System.Globalization.JapaneseLunisolarCalendar> pour fournir une illustration. Toutefois, notez que le fait d'inclure un nom ou une abréviation explicite au lieu d'un entier pour l'ère dans la chaîne de résultat requiert d'instancier un objet <xref:System.Globalization.DateTimeFormatInfo> et de faire de <xref:System.Globalization.JapaneseCalendar> son calendrier actuel. (Le calendrier <xref:System.Globalization.JapaneseLunisolarCalendar> ne peut pas être le calendrier actuel d'une culture, mais dans ce cas, les deux calendriers partagent les mêmes ères.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

Dans les calendriers japonais, la première année d’une époque s’appelle Gannen. Par exemple, au lieu de Heisei 1, la première année de l’ère Heisei peut être décrite comme Heisei Gannen. .NET adopte cette convention dans le formatage des opérations pour les dates et les heures formatées <xref:System.Globalization.CultureInfo> avec les chaînes de format standard ou personnalisés <xref:System.Globalization.JapaneseCalendar> suivantes lorsque elles sont utilisées avec un objet qui représente la culture japonaise-japonaise ("ja-JP") avec la classe:

- [Le modèle de longue date](../base-types/standard-date-and-time-format-strings.md#LongDate), indiqué par la chaîne standard de format de date et d’heure « D ».
- [Le modèle de long terme de date complète](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), indiqué par la chaîne standard de format de date et d’heure « F ».
- [Le modèle de temps court de date complète](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), indiqué par la chaîne standard de format de date et d’heure de « f ».
- [Le modèle d’année/mois](../base-types/standard-date-and-time-format-strings.md#YearMonth), indiqué par le Y" ou "y" chaîne standard de format de date et d’heure.
- [La chaîne de format de [date et d’heure personnalisée](../base-types/custom-date-and-time-format-strings.md)" " " " ggy'" ou « ggy » .

Par exemple, l’exemple suivant affiche une date dans la <xref:System.Globalization.JapaneseCalendar>première année de l’ère Heisei dans le .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Si ce comportement n’est pas souhaitable dans les opérations de formatage, vous pouvez restaurer le comportement précédent, qui représente toujours la première année d’une époque comme "1" plutôt que "Gannen", en faisant ce qui suit, selon la version de .NET:

- **.NET Core:** Ajoutez ce qui suit au fichier *config .netcore.runtime.json* :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4.6 ou plus tard :** Définissez le commutateur AppContext suivant dans le fichier *app.config* :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 ou plus tôt :** Définissez la valeur du registre suivant :

   |  |  |
   |--|--|
   | **Clé** | **HKEY_LOCAL_MACHINE-Software.Microsoft\\. NETFramework-AppContext** |
   | **Nom   ** | Switch.system.Globalization.FormatJapaneseFirstYearAsANumber |
   | **Type** | REG_SZ |
   | **Valeur** | true |

Avec le support gannen dans les opérations de formatage désactivées, l’exemple précédent affiche la sortie suivante :

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET a également été mis à jour de sorte que les chaînes de support des opérations d’analyse de date et d’heure qui contiennent l’année représentée comme «1» ou Gannen. Bien que vous ne devriez pas avoir besoin de le faire, vous pouvez restaurer le comportement précédent pour reconnaître seulement "1" comme la première année d’une époque. Vous pouvez le faire comme suit, en fonction de la version de .NET:

- **.NET Core:** Ajoutez ce qui suit au fichier *config .netcore.runtime.json* :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4.6 ou plus tard :** Définissez le commutateur AppContext suivant dans le fichier *app.config* :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 ou plus tôt :** Définissez la valeur du registre suivant :

   |  |  |
   |--|--|
   | **Clé** | **HKEY_LOCAL_MACHINE-Software.Microsoft\\. NETFramework-AppContext** |
   | **Nom   ** | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   | **Type** | REG_SZ |
   | **Valeur** | true |

## <a name="see-also"></a>Voir aussi

- [Comment: Afficher les dates dans les calendriers non grégoriens](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Exemple : Utilitaire de gamme de semaine civile](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Classe de calendrier](xref:System.Globalization.Calendar)
