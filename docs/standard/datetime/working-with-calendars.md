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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 989c1dec8056502e94e4b9652af89d66a2795dd5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661154"
---
# <a name="working-with-calendars"></a>Utilisation des calendriers

Bien qu'une valeur de date et d'heure représente un moment donné, sa représentation sous forme de chaîne dépend de la culture, des conventions utilisées pour afficher des valeurs de date et d'heure par une culture spécifique et du calendrier utilisé par cette culture. Cette rubrique explore la prise en charge des calendriers dans .NET et explique comment utiliser les classes de calendrier lorsque vous travaillez avec des valeurs de date.

## <a name="calendars-in-net"></a>Calendriers dans .NET

Tous les calendriers dans .NET dérivent la <xref:System.Globalization.Calendar?displayProperty=nameWithType> classe, qui fournit l’implémentation de calendrier de base. Une des classes qui héritent de la classe <xref:System.Globalization.Calendar> est <xref:System.Globalization.EastAsianLunisolarCalendar>, qui constitue la base de tous les calendriers lunisolaires. .NET inclut les implémentations de calendrier suivantes :

* <xref:System.Globalization.ChineseLunisolarCalendar>, qui représente le calendrier lunisolaire chinois.

* <xref:System.Globalization.GregorianCalendar>, qui représente le calendrier grégorien. Ce calendrier est encore divisé en sous-types (tels que l'arabe et le français du Moyen-Orient) qui sont définis par l'énumération <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType>. La propriété <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> spécifie le sous-type du calendrier grégorien.

* <xref:System.Globalization.HebrewCalendar>, qui représente le calendrier hébreu.

* <xref:System.Globalization.HijriCalendar>, qui représente le calendrier Hijri.

* <xref:System.Globalization.JapaneseCalendar>, qui représente le calendrier japonais.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, qui représente le calendrier lunisolaire japonais.

* <xref:System.Globalization.JulianCalendar>, qui représente le calendrier julien.

* <xref:System.Globalization.KoreanCalendar>, qui représente le calendrier coréen.

* <xref:System.Globalization.KoreanLunisolarCalendar>, qui représente le calendrier lunisolaire coréen.

* <xref:System.Globalization.PersianCalendar>, qui représente le calendrier persan.

* <xref:System.Globalization.TaiwanCalendar>, qui représente le calendrier taïwanais.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, qui représente le calendrier lunisolaire taïwanais.

* <xref:System.Globalization.ThaiBuddhistCalendar>, qui représente le calendrier thaï bouddhiste.

* <xref:System.Globalization.UmAlQuraCalendar>, qui représente le calendrier Um Al Qura.

Un calendrier peut être utilisé de deux manières différentes :

* En tant que calendrier utilisé par une culture spécifique. Chaque objet <xref:System.Globalization.CultureInfo> possède un calendrier actuel, qui est celui que l'objet utilise actuellement. Les représentations sous forme de chaîne de toutes les valeurs de date et d'heure reflètent automatiquement la culture actuelle et le calendrier en cours. En général, le calendrier actuel est le calendrier par défaut de la culture. <xref:System.Globalization.CultureInfo> objets possèdent également des calendriers facultatifs, qui comprennent les calendriers supplémentaires utilisables par la culture.

* En tant que calendrier autonome, indépendant d'une culture spécifique. Dans ce cas, les méthodes <xref:System.Globalization.Calendar> sont utilisées pour exprimer des dates sous forme de valeurs qui reflètent le calendrier.

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

### <a name="instantiating-dates-based-on-a-calendar"></a>Instanciation de dates selon un calendrier

Étant donné que les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sont basées sur le calendrier grégorien, vous devez appeler un constructeur surchargé qui inclut un paramètre de type <xref:System.Globalization.Calendar> pour instancier une valeur de date si vous souhaitez utiliser le jour, le mois ou les années d'un calendrier différent. Vous pouvez également appeler une des surcharges d'une méthode <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> d'un calendrier spécifique pour instancier un objet <xref:System.DateTime> en fonction des valeurs d'un calendrier particulier.

L'exemple suivant instancie une valeur <xref:System.DateTime> en passant un objet <xref:System.Globalization.HebrewCalendar> à un constructeur <xref:System.DateTime> et instancie une seconde valeur <xref:System.DateTime> en appelant la méthode <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>. Étant donné que les deux valeurs sont créées avec des valeurs identiques du calendrier hébreu, l'appel de la méthode <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> indique que les deux valeurs <xref:System.DateTime> sont égales.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Représentation des dates dans le calendrier actuel

Les méthodes de mise en forme de la date et de l'heure utilisent toujours le calendrier actuel en convertissant les dates en chaînes. Cela signifie que la représentation sous forme de chaîne de l'année, du mois et du jour du mois reflète le calendrier actuel et pas nécessairement le calendrier grégorien.

L'exemple suivant montre comment le calendrier actuel affecte la représentation sous forme de chaîne d'une date. Il remplace la culture actuelle par le chinois (traditionnel, Taïwan) et instancie une valeur de date. Il affiche ensuite le calendrier actuel et la date, remplace le calendrier actuel par <xref:System.Globalization.TaiwanCalendar> et affiche à nouveau le calendrier actuel et la date . La première fois que la date est affichée, elle est représentée sous la forme d'une date du calendrier grégorien. La seconde fois qu'elle est affichée, elle est représentée sous la forme d'une date du calendrier taïwanais.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Représentation des dates dans un calendrier non actuel

Pour représenter une date à l'aide d'un calendrier qui n'est pas le calendrier actuel d'une culture particulière, vous devez appeler des méthodes de cet objet <xref:System.Globalization.Calendar>. Par exemple, les méthodes <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> et <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> convertissent l'année, le mois et le jour en valeurs qui reflètent un calendrier particulier.

> [!WARNING]
> Étant donné que certains calendriers ne sont les calendriers facultatifs d'aucune culture, la représentation des dates dans ces calendriers requiert toujours l'appel de méthodes de calendrier. C'est le cas de tous les calendriers qui dérivent des classes <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar> et <xref:System.Globalization.PersianCalendar>.

L'exemple suivant utilise un objet <xref:System.Globalization.JulianCalendar> pour instancier une date, le 9 janvier 1905, dans le calendrier julien. Lorsque cette date est affichée à l'aide du calendrier par défaut (grégorien), elle est représentée sous la forme de 22 janvier 1905. Les appels de méthodes <xref:System.Globalization.JulianCalendar> individuelles permettent de représenter la date dans le calendrier julien.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Calendriers et plages de dates

La première date prise en charge par un calendrier est indiquée par la propriété <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> de ce calendrier. Pour la classe <xref:System.Globalization.GregorianCalendar>, cette date est le 1er janvier 0001 (notre ère). La plupart des autres calendriers dans .NET prennent en charge une date ultérieure. Le fait d'essayer d'utiliser une valeur de date et d'heure qui précède la première date prise en charge d'un calendrier lève une exception <xref:System.ArgumentOutOfRangeException>.

Toutefois, il existe une exception importante. La valeur par défaut (non initialisée) d'un objet <xref:System.DateTime> et d'un objet <xref:System.DateTimeOffset> est égale à la valeur <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType>. Si vous essayez de mettre en forme cette date dans un calendrier qui ne prend pas en charge le 1er janvier 0001 (notre ère) et vous ne fournissez pas un spécificateur de format, la méthode de mise en forme utilise le spécificateur de format « s » (modèle de date/heure pouvant être trié) au lieu du spécificateur de format « G » (modèle de date/heure général). Par conséquent, l'opération de mise en forme ne lève pas d'exception <xref:System.ArgumentOutOfRangeException>. Au lieu de cela, elle retourne la date non prise en charge. L'exemple suivant illustre cela en affichant la valeur <xref:System.DateTime.MinValue?displayProperty=nameWithType> lorsque la culture actuelle est définie sur Japonais (Japon) avec le calendrier japonais, et Arabe (Égypte) avec le calendrier Um Al Qura. Il définit également la culture actuelle sur Anglais (États-Unis) et appelle la méthode <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> à chacun de ces objets <xref:System.Globalization.CultureInfo>. Dans chaque cas, la date est affichée à l’aide du modèle de date/heure pouvant être trié.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Utilisation des ères

Les calendriers divisent en général les dates en ères. Toutefois, le <xref:System.Globalization.Calendar> classes dans .NET ne prennent pas en charge chaque ère définie par un calendrier et la plupart de la <xref:System.Globalization.Calendar> classes prennent en charge qu’une seule ère. Seules les classes <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar> prennent en charge plusieurs ères.

> [!IMPORTANT]
> L’ère Reiwa, une nouvelle ère dans la <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar>, commence le 1 mai 2019. Ce changement affecte toutes les applications qui utilisent ces calendriers. Consultez les articles suivants pour plus d’informations :
> - [Gestion d’une nouvelle ère dans le calendrier japonais dans .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), qui documente les fonctionnalités ajoutées à .NET pour prendre en charge plusieurs ères de calendriers et traite des meilleures pratiques à utiliser lors de la gestion des calendriers d’ère multi.
> - [Préparer votre application pour la modification de l’ère japonais](/windows/uwp/design/globalizing/japanese-era-change), qui fournit des informations sur le test de vos applications sur Windows pour garantir leur disponibilité pour la modification de l’ère.
> - [Résumé de la nouvelle ère japonais met à jour pour .NET Framework](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), qui répertorie les mises à jour de .NET Framework pour les différentes versions de Windows qui sont liées à la nouvelle ère de calendrier japonais, note des nouvelles fonctionnalités de .NET Framework pour la prise en charge de l’ère multi et inclut éléments à rechercher dans le test de vos applications.

Une ère dans la plupart des calendriers désigne une période de temps extrêmement long. Dans le calendrier grégorien, par exemple, l’ère actuelle s’étend sur plus de mille ans de deux. Pour le <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar>, les deux calendriers qui prennent en charge plusieurs ères, cela n’est pas le cas. Une ère correspond à la période d’un calendrier d’impérial. Prise en charge de plusieurs ères, en particulier lorsque la limite supérieure de l’ère actuelle est inconnue, pose des défis particuliers.

### <a name="eras-and-era-names"></a>Ères et noms d’ères

Dans .NET, les entiers qui représentent les ères prises en charge par une implémentation particulière de calendrier sont stockées dans l’ordre inverse dans le <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tableau. L’ère actuelle (qui est l’ère avec l’intervalle de temps plus récente) est à l’index zéro et pour <xref:System.Globalization.Calendar> les classes qui prennent en charge plusieurs ères, chaque index successif reflète l’ère précédente. La propriété statique <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> définit l'index de l'ère actuelle dans le tableau <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> ; il s'agit d'une constante dont la valeur est toujours zéro. Les classes <xref:System.Globalization.Calendar> individuelles incluent également les champs static qui retournent la valeur de l’ère actuelle. Elles sont répertoriées dans le tableau suivant.

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

Le nom qui correspond à un numéro d'ère particulier peut être extrait en passant le numéro d'ère à la méthode <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> ou <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType>. L'exemple suivant appelle ces méthodes pour extraire des informations sur la prise en charge de l'ère dans la classe <xref:System.Globalization.GregorianCalendar>. Il affiche la date du calendrier grégorien qui correspond au 1er janvier de la deuxième année de l’ère actuelle, ainsi que la date du calendrier grégorien qui correspond au 1er janvier de la deuxième année de chaque ère prise en charge de calendrier japonais.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

En outre, la chaîne de format de date et d'heure personnalisée « g » inclut un nom d'ère du calendrier dans la représentation sous forme de chaîne d'une date et d'une heure. Pour plus d’informations, consultez [chaînes de format de date personnalisée et heure](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Instanciation d’une date avec une ère

Pour les deux <xref:System.Globalization.Calendar> des classes qui prennent en charge plusieurs ères, une date qui se compose d’une année donnée, le mois et le jour de la valeur de mois peut être ambiguë. Par exemple, tous les ères prises en charge par le <xref:System.Globalization.JapaneseCalendar> comporter des années dont le numéro est 1. En règle générale, si une ère n'est pas spécifiée, les méthodes de date et d'heure et de calendrier supposent que les valeurs appartiennent à l'ère actuelle. Cela est vrai pour les <xref:System.DateTime.%23ctor%2A> et <xref:System.DateTimeOffset.%23ctor%2A> constructeurs qui incluent des paramètres de type <xref:System.Globalization.Calendar>, ainsi que le [JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) et [JapaneseLunisolarCalendar.ToDateTime ](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) méthodes. L’exemple suivant instancie une date qui représente le 1er janvier de la deuxième année d’une ère non spécifiée. Si vous exécutez l’exemple lors de l’ère Reiwa est l’ère actuelle, la date est interprétée comme la deuxième année de l’ère Reiwa. L’ère, 令和, précède l’année dans la chaîne retournée par la <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> (méthode) et correspond à 1 janvier 2020, dans le calendrier grégorien. (L’ère Reiwa commence dans l’exercice 2019 du calendrier grégorien).

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Toutefois, si l’ère change, l’objectif de ce code devient ambigu. La date doit représenter la deuxième année de l’ère actuelle, ou est destiné à représenter la deuxième année de l’ère Heisei ? Il existe deux façons d’éviter cette ambiguïté :

- La valeur de date et l’heure à l’aide de la valeur par défaut d’instancier <xref:System.Globalization.GregorianCalendar> classe. Vous pouvez ensuite utiliser le calendrier japonais ou le calendrier lunisolaire japonais pour la représentation sous forme de chaîne de dates, comme le montre l’exemple suivant.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Appeler une méthode de date et d’heure qui spécifie explicitement une ère. Cela inclut les méthodes suivantes :

  - Le <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> méthode de la <xref:System.Globalization.JapaneseCalendar> ou <xref:System.Globalization.JapaneseLunisolarCalendar> classe.

  - Un <xref:System.DateTime> ou <xref:System.DateTimeOffset> méthode, d’analyse comme <xref:System.DateTime.Parse%2A>, <xref:System.DateTime.TryParse%2A>, <xref:System.DateTime.ParseExact%2A>, ou <xref:System.DateTime.TryParseExact%2A>, qui inclut la chaîne à analyser et éventuellement un <xref:System.Globalization.DateTimeStyles> argument si la culture actuelle est le japonais (Japon) ( » ja-JP ») et le calendrier de cette culture est la <xref:System.Globalization.JapaneseCalendar>. La chaîne à analyser doit inclure l’ère.

  - Un <xref:System.DateTime> ou <xref:System.DateTimeOffset> l’analyse de méthode qui inclut un `provider` paramètre de type <xref:System.IFormatProvider>. `provider` doit être un <xref:System.Globalization.CultureInfo> objet qui représente la culture Japonais (Japon) (« ja-JP ») dont le calendrier actuel est <xref:System.Globalization.JapaneseCalendar> ou un <xref:System.Globalization.DateTimeFormatInfo> de l’objet dont la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar> propriété est <xref:System.Globalization.JapaneseCalendar>. La chaîne à analyser doit inclure l’ère.

  L’exemple suivant utilise trois de ces méthodes pour instancier une date et une heure dans l’ère Meiji, qui a commencé le 8 septembre 1868 et a pris fin le 29 juillet 1912.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Lorsque vous travaillez avec des calendriers qui prennent en charge plusieurs ères, *toujours* la date du calendrier grégorien permet d’instancier une date, ou spécifiez l’ère lorsque vous instanciez une date et heure en fonction de ce calendrier.

Lors de la spécification d’une ère à la <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> (méthode), vous fournissez l’index de l’ère dans le calendrier <xref:System.Globalization.Calendar.Eras> propriété. Pour les calendriers dont ères sont susceptibles de changer, toutefois, ces index n’est pas des valeurs constantes ; l’ère actuelle est à l’index 0 et l’ère la plus ancienne est à l’index `Eras.Length - 1`. Lorsqu’une nouvelle ère est ajoutée à un calendrier, les index des ères précédentes augmenter d’une unité. Vous pouvez fournir l’index de l’ère approprié comme suit :

- Pour les dates dans l’ère actuelle, utilisez toujours le calendrier <xref:System.Globalization.Calendar.CurrentEra> propriété.

- Pour les dates d’une ère spécifiée, utilisez la <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> méthode pour récupérer l’index qui correspond à un nom de l’ère spécifiée. Ceci nécessite que le <xref:System.Globalization.JapaneseCalendar> être le calendrier actuel de la <xref:System.Globalization.CultureInfo> objet qui représente la culture ja-JP.  (Cette technique fonctionne pour le <xref:System.Globalization.JapaneseLunisolarCalendar> également, car il prend en charge les mêmes ères comme le <xref:System.Globalization.JapaneseCalendar>.) L’exemple précédent illustre cette approche.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Calendriers, des ères et plages de dates : Vérifications de la plage souple

Très bien comme des calendriers individuels ont pris en charge les plages de dates, les ères dans le <xref:System.Globalization.JapaneseCalendar> et <xref:System.Globalization.JapaneseLunisolarCalendar> classes également ont pris en charge des plages. Auparavant, .NET utilisé ère strict range vérifie pour s’assurer qu’une date spécifique à l’ère a dans la plage de l’époque. Autrement dit, si une date est en dehors de la plage de l’ère spécifiée, la méthode lève un <xref:System.ArgumentOutOfRangeException>. Actuellement, .NET utilise la vérification par plage souple par défaut. Mises à jour pour toutes les versions de .NET a introduit une ère souple de plage vérifications ; la tentative d’instancier une date spécifique à l’ère qui est en dehors de la plage de l’ère spécifiée « dépassements de capacité » dans l’ère suivant, et aucune exception n’est levée.

L’exemple suivant tente d’instancier une date dans l’année 65e de l’ère Showa, qui a commencé le 25 décembre 1926 et a pris fin le 7 janvier 1989. Cette date correspond à 9 janvier 1990, qui est en dehors de la plage de l’ère Showa dans le <xref:System.Globalization.JapaneseCalendar>. Comme l’illustre la sortie de l’exemple, la date affichée par l’exemple est le 9 janvier 1990, dans la deuxième année de l’ère Heisei.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Si les vérifications de la plage souple sont indésirables, vous pouvez restaurer les vérifications de la plage strict dans une de plusieurs façons, selon la version de .NET sur laquelle votre application est en cours d’exécution :

- **.NET core :** Vous pouvez ajouter le code suivant à la *. netcore.runtime.json* fichier de configuration :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET framework 4.6 ou version ultérieure :** Vous pouvez définir le commutateur AppContext suivant :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET framework 4.5.2 ou version antérieure :** Vous pouvez définir la valeur de Registre suivante :

  |  |  |
  |--|--|
  |Touche | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
  |Nom | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
  |Type | REG_SZ |
  |Value | 1 |

Avec les vérifications de la plage strict est activées, l’exemple précédent lève une <xref:System.ArgumentOutOfRangeException> et affiche la sortie suivante :

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>Représentation des dates dans des calendriers avec plusieurs ères

Si un objet <xref:System.Globalization.Calendar> prend en charge les ères et est le calendrier actuel d’un objet <xref:System.Globalization.CultureInfo>, l’ère est comprise dans la représentation sous forme de chaîne d’une valeur de date et d’heure pour les modèles de date et d’heure complètes, de date longue et de date courte. L’exemple suivant illustre ces modèles de date lorsque la culture actuelle est le japonais (Japon) et le calendrier actuel est le japonais.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Le <xref:System.Globalization.JapaneseCalendar> classe est la seule classe de calendrier dans .NET qui les deux dates prend en charge plusieurs ères et qui peut être le calendrier actuel d’un <xref:System.Globalization.CultureInfo> objet - spécifiquement, d’un <xref:System.Globalization.CultureInfo> objet qui représente la culture Japonais (Japon).

Pour tous les calendriers, le spécificateur de format personnalisé « g » inclut l'ère dans la chaîne de résultat. L'exemple suivant utilise la chaîne de format personnalisé de "MM-jj-aaaa g" pour inclure l'ère dans la chaîne de résultat quand le calendrier actuel est le calendrier grégorien.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Dans les cas où la représentation sous forme de chaîne d'une date est exprimée dans un calendrier qui n'est pas le calendrier en cours, la classe <xref:System.Globalization.Calendar> inclut une méthode <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> qui peut être utilisée avec les méthodes <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> et <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> pour indiquer clairement une date ainsi que l'ère à laquelle elle appartient. L'exemple suivant utilise la classe <xref:System.Globalization.JapaneseLunisolarCalendar> pour fournir une illustration. Toutefois, notez que le fait d'inclure un nom ou une abréviation explicite au lieu d'un entier pour l'ère dans la chaîne de résultat requiert d'instancier un objet <xref:System.Globalization.DateTimeFormatInfo> et de faire de <xref:System.Globalization.JapaneseCalendar> son calendrier actuel. (Le calendrier <xref:System.Globalization.JapaneseLunisolarCalendar> ne peut pas être le calendrier actuel d'une culture, mais dans ce cas, les deux calendriers partagent les mêmes ères.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

Dans les calendriers japonais, la première année d’une ère est appelée Gannen du (元年). Par exemple, au lieu de Heisei 1, la première année de l’ère Heisei peut être décrit comme Heisei Gannen. .NET adopte cette convention de mise en forme des opérations pour les dates et heures avec le format date standard ou personnalisée suivante et format d’heure chaînes lorsqu’ils sont utilisés avec un <xref:System.Globalization.CultureInfo> objet qui représente la culture Japonais (Japon) (« ja-JP ») avec le <xref:System.Globalization.JapaneseCalendar> classe :

- [Le modèle de date longue](../base-types/standard-date-and-time-format-strings.md#LongDate), indiqué par la date et heure de chaîne de format standard « D ».
- [Modèle de la date complète heure longue](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), indiqué par la date et heure de chaîne de format standard « F ».
- [Le modèle d’heure courte de date complet](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), indiqué par la date et heure de chaîne de format standard « f ».
- [Le modèle d’année/mois](../base-types/standard-date-and-time-format-strings.md#YearMonth), indiqué par le Y » ou « y » date et heure standard chaîne de format.
- [La « ggy '年' » ou « ggy年 » [chaîne de format de date et heure](../base-types/custom-date-and-time-format-strings.md).

Par exemple, l’exemple suivant affiche une date dans la première année de l’ère Heisei dans le <xref:System.Globalization.JapaneseCalendar> .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Si ce comportement n’est pas souhaitable dans les opérations de mise en forme, vous pouvez restaurer le comportement précédent, qui représente toujours la première année d’une ère « 1 » au lieu de « Gannen », en procédant comme suit, selon la version de .NET :

- **.NET core :** Vous pouvez ajouter le code suivant à la *. netcore.runtime.json* fichier de configuration :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET framework 4.6 ou version ultérieure :** Vous pouvez définir le commutateur AppContext suivant :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET framework 4.5.2 ou version antérieure :** Vous pouvez définir la valeur de Registre suivante :

  |  |  |
  |--|--|
  |Touche | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
  |Nom | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
  |Type | REG_SZ |
  |Value | 1 |

Prend en charge Gannen du désactivé des opérations de mise en forme, l’exemple précédent affiche la sortie suivante :

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET a également été mis à jour afin que la date et l’heure d’opérations d’analyse prend en charge les chaînes qui contiennent l’année représenté en tant que « 1 » ou Gannen du. Bien que vous ne devez pas pour ce faire, vous pouvez restaurer le comportement précédent à reconnaît uniquement « 1 » en tant que la première année d’une ère. Vous pouvez le faire comme suit, selon la version de .NET :

- **.NET core :** Vous pouvez ajouter le code suivant à la *. netcore.runtime.json* fichier de configuration :

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET framework 4.6 ou version ultérieure :** Vous pouvez définir le commutateur AppContext suivant :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET framework 4.5.2 ou version antérieure :** Vous pouvez définir la valeur de Registre suivante :

  |  |  |
  |--|--|
  |Touche | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
  |Nom | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
  |Type | REG_SZ |
  |Value | 1 |

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Afficher des dates dans des calendriers non grégoriens](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Exemple : Utilitaire de plages de semaine de calendrier](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Classe de calendrier](xref:System.Globalization.Calendar)
