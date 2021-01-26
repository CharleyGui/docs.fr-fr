---
title: Chaînes de format de date et d’heure standard
description: Découvrez comment utiliser une chaîne de format de date et d’heure standard pour définir la représentation textuelle d’une valeur de date et d’heure dans .NET.
ms.date: 01/25/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET], time
- date and time strings
ms.topic: reference
ms.custom: contperf-fy21q2
ms.openlocfilehash: f445ee92345fa692e11fc60c658020fc92e55a2e
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794755"
---
# <a name="standard-date-and-time-format-strings"></a>Chaînes de format de date et d’heure standard

Une chaîne de format de date et d’heure standard utilise un caractère unique comme spécificateur de format pour définir la représentation textuelle d’une <xref:System.DateTime> <xref:System.DateTimeOffset> valeur ou. Toute chaîne de format de date et d’heure contenant plusieurs caractères, y compris un espace blanc, est interprétée comme une [chaîne de format de date et d’heure personnalisée](custom-date-and-time-format-strings.md). Une chaîne de format standard ou personnalisée peut être utilisée de deux façons :

- Pour définir la chaîne qui résulte d'une opération de mise en forme.

- Pour définir la représentation textuelle d'une valeur de date et d'heure pouvant être convertie en valeur <xref:System.DateTime> ou en valeur <xref:System.DateTimeOffset> lors d'une opération d'analyse.

> [!TIP]
> Vous pouvez télécharger l' **utilitaire de mise en forme**, une application .NET Windows Forms qui vous permet d’appliquer des chaînes de format à des valeurs numériques ou de date et d’heure et d’afficher la chaîne de résultat. Le code source est disponible pour [C#](/samples/dotnet/samples/windowsforms-formatting-utility-cs) et [Visual Basic](/samples/dotnet/samples/windowsforms-formatting-utility-vb).

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

## <a name="table-of-format-specifiers"></a>Table des spécificateurs de format

<a name="table"></a> Le tableau suivant décrit les spécificateurs de format de date et d’heure standard. Sauf indication contraire, un spécificateur de format de date et d'heure standard particulier produit une représentation sous forme de chaîne identique, qu'il soit utilisé avec une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset>. Consultez [paramètres du panneau de configuration](#control-panel-settings) et [propriétés DateTimeFormatInfo](#datetimeformatinfo-properties) pour plus d’informations sur l’utilisation de chaînes de format de date et d’heure standard.

|Spécificateur de format|Description|Exemples|
|----------------------|-----------------|--------------|
|"d"|Modèle de date courte.<br /><br /> Informations supplémentaires :[spécificateur de format de date abrégée ("d")](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|
|« D »|Modèle de date longue.<br /><br /> Informations supplémentaires :[spécificateur de format de date longue ("D")](#LongDate).|2009-06-15T13:45:30 -> Monday, June 15, 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)|
|"f"|Modèle de date/heure complet (heure courte).<br /><br /> Informations supplémentaires : [spécificateur de format de date complet et d’heure abrégée ("f")](#FullDateShortTime).|2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|
|"F"|Modèle de date/heure complet (heure longue).<br /><br /> Informations supplémentaires : [spécificateur de format de date complet et d’heure longue ("F")](#FullDateLongTime).|2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|
|"g"|Modèle de date/heure général (heure courte).<br /><br /> Informations supplémentaires : [spécificateur de format de date général et d’heure abrégée ("g")](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|
|"G"|Modèle de date/heure général (heure longue).<br /><br /> Informations supplémentaires : [spécificateur de format de date général et d’heure longue ("G")](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|
|"M", "m"|Modèle de mois/jour.<br /><br /> Informations supplémentaires : [spécificateur de format de mois ("m", "m")](#MonthDay).|2009-06-15T13:45:30 -> June 15 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|
|"O", "o"|modèle de date/heure aller-retour.<br /><br /> Informations supplémentaires : [spécificateur de format aller-retour ("o", "o")](#Roundtrip).|Valeurs <xref:System.DateTime> :<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000<br /><br /> Valeurs <xref:System.DateTimeOffset> :<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00|
|"R", "r"|Modèle RFC1123.<br /><br /> Informations supplémentaires : [spécificateur de format RFC1123 ("r", "r")](#RFC1123).|2009-06-15T13:45:30 -> Mon, 15 Jun 2009 20:45:30 GMT|
|"s"|Modèle de date/heure pouvant être trié.<br /><br /> Informations supplémentaires : [spécificateur de format pouvant être trié ("s")](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|
|"t"|Modèle d’heure courte.<br /><br /> Informations supplémentaires : [spécificateur de format d’heure abrégée ("t")](#ShortTime).|2009-06-15T13:45:30 -> 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-EG)|
|"T"|Modèle d’heure longue.<br /><br /> Informations supplémentaires : [spécificateur de format d’heure longue ("T")](#LongTime).|2009-06-15T13:45:30 -> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)|
|"u"|Modèle de date/heure universel pouvant être trié.<br /><br /> Informations supplémentaires : [spécificateur de format universel pouvant être trié ("u")](#UniversalSortable).|Avec une valeur <xref:System.DateTime> : 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> Avec une valeur <xref:System.DateTimeOffset> : 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|
|"U"|Modèle de date/heure complet universel.<br /><br /> Informations supplémentaires : [spécificateur de format complet universel ("U")](#UniversalFull).|2009-06-15T13:45:30 -> Monday, June 15, 2009 8:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|
|"Y", "y"|Modèle d’année/mois.<br /><br /> Informations supplémentaires : [spécificateur de format année mois ("Y")](#YearMonth).|2009-06-15T13:45:30-> juin 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|
|N'importe quel caractère|Spécificateur inconnu.|Lève un <xref:System.FormatException> runtime.|

## <a name="how-standard-format-strings-work"></a>Fonctionnement des chaînes de format standard

Dans une opération de mise en forme, une chaîne de format standard constitue simplement un alias d'une chaîne de format personnalisée. L'utilisation d'un alias pour faire référence à une chaîne de format personnalisée présente l'avantage suivant : bien que l'alias reste invariant, la chaîne de format personnalisée peut varier. Ce point est important car les représentations sous forme de chaîne de valeurs de date et d'heure varient généralement selon la culture. Par exemple, la chaîne de format standard "d" indique qu'une valeur de date et d'heure sera affichée à l'aide d'un modèle de date courte. Pour la culture dite indifférente, ce modèle est "MM/dd/yyyy". Pour la culture fr-FR, il s'agit de "dd/MM/yyyy". Pour la culture ja-JP, il s'agit de "yyyy/MM/dd".

Si, dans une opération de mise en forme, une chaîne de format standard est mappée à une chaîne de format personnalisée d'une culture particulière, votre application peut définir la culture spécifique dont les chaînes de format personnalisées sont utilisées de l'une des manières suivantes :

- Vous pouvez utiliser la culture par défaut (ou actuelle). L'exemple suivant affiche une date à l'aide du format de date courte de la culture actuelle. Dans ce cas, la culture actuelle est en-US.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Vous pouvez passer un objet <xref:System.Globalization.CultureInfo> représentant la culture dont la mise en forme sera utilisée à une méthode qui a un paramètre <xref:System.IFormatProvider>. L'exemple suivant affiche une date à l'aide du format de date courte de la culture pt-BR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- Vous pouvez passer un objet <xref:System.Globalization.DateTimeFormatInfo> qui fournit des informations de mise en forme à une méthode qui a un paramètre <xref:System.IFormatProvider>. L'exemple suivant affiche une date à l'aide du format de date courte d'un objet <xref:System.Globalization.DateTimeFormatInfo> pour la culture hr-HR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Pour plus d'informations sur la personnalisation des chaînes ou des modèles utilisés dans la mise en forme des valeurs numériques, consultez la rubrique de la classe <xref:System.Globalization.NumberFormatInfo>.

Dans certains cas, il est pratique d'utiliser la chaîne de format standard comme abréviation pour les chaînes de format personnalisées plus longues et indifférentes. Quatre chaînes de format standard appartiennent à cette catégorie : "O" (ou "o"), "R" (ou "r"), "s" et "u". Ces chaînes correspondent aux chaînes de format personnalisées définies par la culture dite indifférente. Elles produisent des représentations sous forme de chaîne de valeurs de date et d'heure destinées à être identiques dans toutes les cultures. Le tableau suivant fournit des informations sur ces quatre chaînes de format de date et d'heure standard.

|Chaîne de format standard|Défini par la propriété DateTimeFormatInfo.InvariantInfo|Chaîne de format personnalisée|
|----------------------------|----------------------------------------------------------|--------------------------|
|"O" ou "o"|None|chaîne-personnalisée "YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' fffffffK|
|"R" ou "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Les chaînes de format standard peuvent également utilisées dans les opérations d'analyses avec les méthodes <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>. Pour que l'opération d'analyse aboutisse, ces méthodes requièrent qu'une chaîne d'entrée se conforme exactement à un modèle particulier. De nombreuses chaînes de format standard peuvent être mappées à plusieurs chaînes de format personnalisées, afin qu'une valeur de date et d'heure puisse être représentée dans divers formats et que l'opération d'analyse puisse continuer à aboutir. Vous pouvez déterminer les chaînes de format personnalisées qui correspondent à une chaîne de format standard en appelant la méthode <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType>. L’exemple suivant affiche les chaînes de format personnalisées qui sont mappées à la chaîne de format standard « d » (modèle de date courte).

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

Les sections suivantes décrivent les spécificateurs de format standard pour les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.

## <a name="date-formats"></a>Formats de date

Ce groupe comprend les formats suivants :

- [Spécificateur de format de date abrégée ("d")](#the-short-date-d-format-specifier)
- [Spécificateur de format de date longue ("D")](#the-long-date-d-format-specifier)

<a name="ShortDate"></a>

### <a name="the-short-date-d-format-specifier"></a>Spécificateur de format de date courte ("d")

Le spécificateur de format standard "d" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> d'une culture spécifique. Par exemple, la chaîne de format personnalisée qui est retournée par la propriété <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> de la culture dite indifférente est "MM/dd/yyyy".

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Définit le format global de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Définit la chaîne qui sépare les composants « année », « mois » et « jour » d'une date.|

L'exemple suivant utilise le spécificateur de format "d" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
[!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]

[Retour au tableau](#table)

<a name="LongDate"></a>

### <a name="the-long-date-d-format-specifier"></a>Spécificateur de format de date longue ("D")

Le spécificateur de format standard "D" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "dddd, dd MMMM yyyy".

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Définit le format global de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.|

L'exemple suivant utilise le spécificateur de format "D" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
[!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]

[Retour au tableau](#table)

## <a name="date-and-time-formats"></a>Formats de date et d’heure

Ce groupe comprend les formats suivants :

- [Spécificateur de format de date complet et d’heure abrégée ("f")](#the-full-date-short-time-f-format-specifier)
- [Spécificateur de format de date complet et d’heure longue ("F")](#the-full-date-long-time-f-format-specifier)
- [Spécificateur de format d’heure abrégée de date générale ("g")](#the-general-date-short-time-g-format-specifier)
- [Spécificateur de format de date général et d’heure longue ("G")](#the-general-date-long-time-g-format-specifier)
- [Spécificateur de format aller-retour ("O", "o")](#the-round-trip-o-o-format-specifier)
- [Spécificateur de format RFC1123 ("R", "r")](#the-rfc1123-r-r-format-specifier)
- [Spécificateur de format pouvant être trié ("s")](#the-sortable-s-format-specifier)
- [Spécificateur de format universel pouvant être trié ("u")](#the-universal-sortable-u-format-specifier)
- [Spécificateur de format complet universel ("U")](#the-universal-full-u-format-specifier)

<a name="FullDateShortTime"></a>

### <a name="the-full-date-short-time-f-format-specifier"></a>Spécificateur de format de date complet et d’heure courte ("f")

Le spécificateur de format standard "f" représente une combinaison des modèles de date longue ("D") et d’heure courte ("t"), séparés par un espace.

Les informations de mise en forme d'un objet <xref:System.Globalization.DateTimeFormatInfo> spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé retourné par les propriétés <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> et <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Définit le format du composant « date » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Définit le format du composant « heure » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

L'exemple suivant utilise le spécificateur de format "f" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#3)]
[!code-vb[Formatting.DateAndTime.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#3)]

[Retour au tableau](#table)

<a name="FullDateLongTime"></a>

### <a name="the-full-date-long-time-f-format-specifier"></a>Spécificateur de format de date complet et d’heure longue ("F")

Le spécificateur de format standard "F" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "dddd, dd MMMM yyyy HH:mm:ss".

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Définit le format global de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

L'exemple suivant utilise le spécificateur de format "F" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#4)]
[!code-vb[Formatting.DateAndTime.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#4)]

[Retour au tableau](#table)

<a name="GeneralDateShortTime"></a>

### <a name="the-general-date-short-time-g-format-specifier"></a>Spécificateur de format de date général et d’heure courte ("g")

Le spécificateur de format standard "g" représente une combinaison des modèles de date courte ("d") et d’heure courte ("t"), séparés par un espace.

Les informations de mise en forme d'un objet <xref:System.Globalization.DateTimeFormatInfo> spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par les propriétés <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> et <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Définit le format du composant « date » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Définit le format du composant « heure » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Définit la chaîne qui sépare les composants « année », « mois » et « jour » d'une date.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

L'exemple suivant utilise le spécificateur de format "g" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#5)]
[!code-vb[Formatting.DateAndTime.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#5)]

[Retour au tableau](#table)

<a name="GeneralDateLongTime"></a>

### <a name="the-general-date-long-time-g-format-specifier"></a>Spécificateur de format de date général et d’heure longue ("G")

Le spécificateur de format standard "G" représente une combinaison des modèles de date courte ("d") et d’heure longue ("T"), séparés par un espace.

Les informations de mise en forme d'un objet <xref:System.Globalization.DateTimeFormatInfo> spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par les propriétés <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> et <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Définit le format du composant « date » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Définit le format du composant « heure » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Définit la chaîne qui sépare les composants « année », « mois » et « jour » d'une date.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

L'exemple suivant utilise le spécificateur de format "G" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#6)]
[!code-vb[Formatting.DateAndTime.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#6)]

[Retour au tableau](#table)

<a name="Roundtrip"></a>

### <a name="the-round-trip-o-o-format-specifier"></a>Spécificateur de format aller-retour ("O", "o")

Le spécificateur de format standard "O" ou "o" représente une chaîne de format de date et d’heure personnalisée à l’aide d’un modèle qui conserve les informations de fuseau horaire et génère une chaîne de résultat conforme à la norme ISO 8601. Pour les valeurs <xref:System.DateTime>, ce spécificateur de format est conçu pour conserver des valeurs de date et d'heure avec la propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> dans le texte. La chaîne mise en forme peut être de nouveau analysée à l'aide de la méthode <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> ou <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> si le paramètre `styles` a la valeur <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.

Le spécificateur de format standard "O" ou "o" correspond à la chaîne de format personnalisée "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" pour les valeurs <xref:System.DateTime> et à la chaîne de format personnalisée "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzzz" pour les valeurs <xref:System.DateTimeOffset>. Dans cette chaîne, les paires de guillemets simples qui délimitent des caractères individuels, comme les traits d'union, les deux-points et la lettre "T", indiquent que le caractère individuel est un littéral qui ne peut pas être modifié. Les apostrophes n'apparaissent pas dans la chaîne de sortie.

Le spécificateur de format standard "O" ou "o" et la chaîne de format personnalisée "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" tirent parti des trois façons dont la norme ISO 8601 représente les informations de fuseau horaire pour conserver la propriété <xref:System.DateTime.Kind%2A> des valeurs <xref:System.DateTime> :

- Le composant de fuseau horaire des valeurs de date et d'heure <xref:System.DateTimeKind.Local?displayProperty=nameWithType> est un décalage par rapport à l'heure UTC (par exemple, +01:00, -07:00). Toutes les valeurs <xref:System.DateTimeOffset> sont également représentées dans ce format.

- Le composant de fuseau horaire des valeurs de date et d'heure <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> utilise "Z" (soit zéro décalage) pour représenter l'heure UTC.

- Les valeurs de date et d'heure <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ne possèdent aucune information de fuseau horaire.

Comme le spécificateur de format standard « O » ou « o » est conforme à une norme internationale, l’opération de mise en forme ou d’analyse qui recourt au spécificateur utilise toujours la culture dite indifférente et le calendrier grégorien.

Les chaînes transmises aux méthodes `Parse`, `TryParse`, `ParseExact`, et `TryParseExact` de <xref:System.DateTime> et <xref:System.DateTimeOffset> peuvent être analysées à l'aide du spécificateur de format "O" ou "o" si elles sont définies dans l'un de ces formats. Dans le cas des objets <xref:System.DateTime>, la surcharge d'analyse que vous appelez doit également inclure un paramètre `styles` avec une valeur de <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Notez que si vous appelez une méthode d'analyse avec la chaîne de format personnalisée qui correspond au spécificateur de format "O" ou "o", vous n'obtenez pas les mêmes résultats que "O" ou "o". En effet, les méthodes d'analyse qui utilisent une chaîne de format personnalisée ne peuvent pas analyser la représentation sous forme de chaîne des valeurs de date et d'heure auxquelles fait défaut un composant de fuseau horaire ou qui recourent à "Z" pour indiquer l'heure UTC.

L’exemple suivant utilise le spécificateur de format "o" pour afficher une série de <xref:System.DateTime> valeurs et une <xref:System.DateTimeOffset> valeur sur un système situé dans le fuseau horaire Pacifique (États-Unis).

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

L'exemple suivant utilise le spécificateur de format "o" pour créer une chaîne mise en forme, puis restaure la valeur de date et d'heure d'origine en appelant une méthode `Parse` de date et d'heure.

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Retour au tableau](#table)

<a name="RFC1123"></a>

### <a name="the-rfc1123-r-r-format-specifier"></a>Spécificateur de format RFC1123 ("R", "r")

Le spécificateur de format standard "R" ou "r" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> actuelle. Le modèle reflète une norme définie, et la propriété est en lecture seule. Par conséquent, il s'agit toujours du même, quels que soient la culture utilisée ou le fournisseur de format spécifié. La chaîne de format personnalisée est "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Lorsque ce spécificateur de format standard est utilisé, l'opération de mise en forme ou d'analyse utilise toujours la culture dite indifférente.

La chaîne de résultat est affectée par les propriétés suivantes de l'objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> qui représente la culture dite indifférente.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Définit le format de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Définit les noms de jours abrégés qui peuvent s'afficher dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Définit les noms de mois abrégés qui peuvent s'afficher dans la chaîne de résultat.|

Bien que la norme RFC 1123 exprime une heure au format de temps universel coordonné (UTC, Coordinated Universal Time), l'opération de mise en forme ne modifie pas la valeur de l'objet <xref:System.DateTime> qui est mis en forme. Par conséquent, vous devez convertir la valeur <xref:System.DateTime> en temps UTC en appelant la méthode <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> avant d'exécuter l'opération de mise en forme. En revanche, les valeurs <xref:System.DateTimeOffset> exécutent cette conversion automatiquement ; il n'est pas nécessaire d'appeler la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> avant l'opération de mise en forme.

L'exemple suivant utilise le spécificateur de format "r" pour afficher une valeur <xref:System.DateTime> et une valeur <xref:System.DateTimeOffset> sur un système situé dans le fuseau horaire Pacifique (États-Unis).

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Retour au tableau](#table)

<a name="Sortable"></a>

### <a name="the-sortable-s-format-specifier"></a>Spécificateur de format pouvant être trié ("s")

Le spécificateur de format standard "s" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> actuelle. Le modèle reflète une norme définie (ISO 8601), et la propriété est en lecture seule. Par conséquent, il s'agit toujours du même, quels que soient la culture utilisée ou le fournisseur de format spécifié. La chaîne de format personnalisée est "yyyy'-'MM'-'dd'T'HH':'mm':'ss".

L'objectif du spécificateur de format "s" est de produire des chaînes de résultats qui trient de façon cohérente par ordre croissant ou décroissant en fonction des valeurs de date et d'heure. Par conséquent, bien que le spécificateur de format standard "s" représente une valeur de date et d'heure dans un format cohérent, l'opération de mise en forme ne modifie pas la valeur de l'objet de date et d'heure qui est mise en forme de façon à refléter sa propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> ou sa valeur <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType>. Par exemple, les chaînes de résultat produites par la mise en forme des valeurs de date et d'heure 2014-11-15T18:32:17 + 00:00 et 2014-11-15T18:32:17 + 08:00 sont identiques.

Lorsque ce spécificateur de format standard est utilisé, l'opération de mise en forme ou d'analyse utilise toujours la culture dite indifférente.

L'exemple suivant utilise le spécificateur de format "s" pour afficher une valeur <xref:System.DateTime> et une valeur <xref:System.DateTimeOffset> sur un système situé dans le fuseau horaire Pacifique (États-Unis).

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Retour au tableau](#table)

<a name="UniversalSortable"></a>

### <a name="the-universal-sortable-u-format-specifier"></a>Spécificateur de format universel pouvant être trié ("u")

Le spécificateur de format standard "u" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> actuelle. Le modèle reflète une norme définie, et la propriété est en lecture seule. Par conséquent, il s'agit toujours du même, quels que soient la culture utilisée ou le fournisseur de format spécifié. La chaîne de format personnalisée est "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Lorsque ce spécificateur de format standard est utilisé, l'opération de mise en forme ou d'analyse utilise toujours la culture dite indifférente.

Bien que la chaîne de résultat doive exprimer une heure au format de temps universel coordonné (UTC, Coordinated Universal Time), aucune conversion de la valeur <xref:System.DateTime> d'origine n'est effectuée pendant l'opération de mise en forme. Par conséquent, vous devez convertir une valeur <xref:System.DateTime> en temps UTC en appelant la méthode <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> avant de la mettre en forme.  En revanche, les valeurs <xref:System.DateTimeOffset> exécutent cette conversion automatiquement ; il n'est pas nécessaire d'appeler la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> avant l'opération de mise en forme.

L'exemple suivant utilise le spécificateur de format « u » pour afficher une valeur de date et d'heure.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Retour au tableau](#table)

<a name="UniversalFull"></a>

### <a name="the-universal-full-u-format-specifier"></a>Spécificateur de format complet universel ("U")

Le spécificateur de format standard "U" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> d'une culture spécifiée. Le modèle est identique au modèle "F". Toutefois, la valeur <xref:System.DateTime> est automatiquement convertie en temps UTC avant d'être mise en forme.

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Définit le format global de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

Le spécificateur de format "U" n'est pas pris en charge par le type <xref:System.DateTimeOffset> et lève un <xref:System.FormatException> s'il est utilisé pour mettre en forme une valeur <xref:System.DateTimeOffset>.

L'exemple suivant utilise le spécificateur de format "U" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Retour au tableau](#table)

## <a name="time-formats"></a>Formats d’horodatage

Ce groupe comprend les formats suivants :

- [Spécificateur de format d’heure abrégée ("t")](#the-short-time-t-format-specifier)
- [Spécificateur de format d’heure longue ("T")](#the-long-time-t-format-specifier)

<a name="ShortTime"></a>

### <a name="the-short-time-t-format-specifier"></a>Spécificateur de format d’heure courte ("t")

Le spécificateur de format standard "t" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "HH:mm".

Les informations de mise en forme d'un objet <xref:System.Globalization.DateTimeFormatInfo> spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Définit le format du composant « heure » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

L'exemple suivant utilise le spécificateur de format "t" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
[!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]

[Retour au tableau](#table)

<a name="LongTime"></a>

### <a name="the-long-time-t-format-specifier"></a>Spécificateur de format d’heure longue ("T")

Le spécificateur de format standard "T" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> d'une culture spécifique. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "HH:mm:ss".

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> de certaines cultures ne peut pas utiliser toutes les propriétés.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Définit le format du composant « heure » de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Définit la chaîne qui sépare les composants « heure », « minute » et « seconde » d'une heure.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.|

L'exemple suivant utilise le spécificateur de format "T" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
[!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]

[Retour au tableau](#table)

## <a name="partial-date-formats"></a>Formats de date partiels

Ce groupe comprend les formats suivants :

- [Spécificateur de format month ("M", "m")](#the-month-m-m-format-specifier)
- [Spécificateur de format année mois ("Y", "y")](#the-year-month-y-y-format-specifier)

<a name="MonthDay"></a>

### <a name="the-month-m-m-format-specifier"></a>Spécificateur de format de mois ("M", "m")

Le spécificateur de format standard "M" ou "m" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "MMMM dd".

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Définit le format global de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.|

L'exemple suivant utilise le spécificateur de format "m" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
[!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]

[Retour au tableau](#table)

<a name="YearMonth"></a>

### <a name="the-year-month-y-y-format-specifier"></a>Spécificateur de format Année Mois ("Y", "y")

Le spécificateur de format standard "Y" ou "y" représente une chaîne de format de date et d'heure personnalisée définie par la propriété <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> d'une culture spécifiée. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "yyyy MMMM".

Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété|Description|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Définit le format global de la chaîne de résultat.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.|

L'exemple suivant utilise le spécificateur de format "y" pour afficher une valeur de date et d'heure.

[!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
[!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]

[Retour au tableau](#table)

<a name="Notes"></a>

## <a name="control-panel-settings"></a>Paramètres du panneau de configuration

Dans Windows, les paramètres de l’élément **Options régionales et linguistiques** du panneau de configuration influencent la chaîne de résultat produite par une opération de mise en forme. Ces paramètres sont utilisés pour initialiser l'objet <xref:System.Globalization.DateTimeFormatInfo> associé à la culture du thread en cours qui fournit des valeurs utilisées pour indiquer la mise en forme. Les ordinateurs qui utilisent des paramètres différents génèrent des chaînes de résultat différentes.

De plus, si vous utilisez le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> pour instancier un nouvel objet <xref:System.Globalization.CultureInfo> qui représente la même culture que la culture système en cours, toutes les personnalisations établies par l'élément **Options régionales et linguistiques** du Panneau de configuration seront appliquées au nouvel objet <xref:System.Globalization.CultureInfo> . Vous pouvez utiliser le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> pour créer un objet <xref:System.Globalization.CultureInfo> qui ne reflète pas les personnalisations d'un système.

## <a name="datetimeformatinfo-properties"></a>Propriétés DateTimeFormatInfo

La mise en forme dépend des propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> actif, qui est fourni implicitement par la culture actuelle du thread ou explicitement par le paramètre <xref:System.IFormatProvider> de la méthode qui appelle la mise en forme. Pour le paramètre <xref:System.IFormatProvider>, votre application doit spécifier un objet <xref:System.Globalization.CultureInfo>, qui représente une culture, ou un objet <xref:System.Globalization.DateTimeFormatInfo>, qui représente les conventions de présentation de la date et de l'heure d'une culture particulière. La plupart des spécificateurs de format de date et d’heure standard sont des alias des modèles de mise en forme définis par les propriétés de l’objet <xref:System.Globalization.DateTimeFormatInfo> en cours. Votre application peut modifier le résultat produit par certains spécificateurs de format de date et d'heure standard en modifiant les modèles de format de date et d'heure correspondants de la propriété <xref:System.Globalization.DateTimeFormatInfo> correspondante.

## <a name="see-also"></a>Voir aussi

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Mise en forme des types](formatting-types.md)
- [Chaînes de format de date et d’heure personnalisées](custom-date-and-time-format-strings.md)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (C#)](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (Visual Basic)](/samples/dotnet/samples/windowsforms-formatting-utility-vb)
