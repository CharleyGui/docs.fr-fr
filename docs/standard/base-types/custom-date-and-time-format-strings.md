---
title: Chaînes de format de date et d’heure personnalisées
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET Framework], time
- date and time strings
ms.assetid: 98b374e3-0cc2-4c78-ab44-efb671d71984
ms.openlocfilehash: b33366922677b26f8fe99454206cacd5bb124f32
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159271"
---
# <a name="custom-date-and-time-format-strings"></a>Chaînes de format de date et d’heure personnalisées

Une chaîne de format de date et d’heure définit la représentation textuelle d’une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> résultant d’une opération de mise en forme. Elle peut également définir la représentation d'une valeur de date et d'heure qui est requise dans une opération d'analyse afin de convertir correctement la chaîne sous forme de date et d'heure. Une chaîne de format personnalisée se compose d'un ou de plusieurs spécificateurs de format de date et d'heure personnalisés. Toute chaîne autre qu’une [chaîne de format de date et d’heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) est interprétée comme une chaîne de format de date et d’heure personnalisée.

> [!TIP]
> Vous pouvez télécharger l’**utilitaire de mise en forme**, application .NET Core Windows Forms qui vous permet d’appliquer des chaînes de mise en forme à des valeurs numériques ou à des valeurs de date et d’heure, et d’afficher la chaîne de résultat. Le code source est disponible pour [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) et [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

Les chaînes de format de date et d'heure personnalisées peuvent être utilisées avec les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a> Dans les opérations de mise en forme, les chaînes de format de date et d'heure personnalisées peuvent être utilisées avec la méthode `ToString` d'une instance de date et d'heure ou avec une méthode qui prend en charge la mise en forme composite. L'exemple suivant illustre ces deux types d'utilisation.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

Dans les opérations d'analyse, les chaînes de format de date et d'heure personnalisées peuvent être utilisées avec les méthodes <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>. Pour que l’opération d’analyse aboutisse, il faut qu’une chaîne d’entrée soit parfaitement conforme à un modèle particulier. L'exemple suivant illustre un appel à la méthode <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> pour analyser une date qui doit comprendre un jour, un mois et une année sur deux chiffres.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

Le tableau suivant décrit les spécificateurs de format de date et d'heure personnalisés et affiche une chaîne de résultat produite par chaque spécificateur de format. Par défaut, les chaînes de résultat reflètent les conventions de mise en forme de la culture en-US. Si un spécificateur de format particulier produit une chaîne de résultat localisée, l'exemple indique également la culture à laquelle la chaîne de résultat s'applique. Pour plus d’informations sur les chaînes de format de date et d’heure personnalisées, voir la section [Remarques](#notes).

| Spécificateur de format | Description | Exemples |
| ---------------------- | ----------------- | -------------- |
|"d"|Jour du mois, de 1 à 31.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "d"](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|
|"dd"|Jour du mois, de 01 à 31.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "dd"](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|
|"ddd"|Nom abrégé du jour de la semaine.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "ddd"](#dddSpecifier).|2009-06-15T13:45:30 -> Mon (en-US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|
|"dddd"|Nom complet du jour de la semaine.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "dddd"](#ddddSpecifier).|2009-06-15T13:45:30 -> Monday (en-US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|"f"|Dixièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "f"](#fSpecifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|
|"ff"|Centièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FF"](#ffSpecifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> 00|
|"fff"|Millisecondes dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "fff"](#fffSpecifier).|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|
|"ffff"|Dix millièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "ffff"](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -> 6175<br /><br /> 2009-06-15T13:45:30.0000500  -> 0000|
|"fffff"|Cent millièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "fffff"](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|
|"ffffff"|Millionièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "ffffff"](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> 000000|
|"fffffff"|Dix millionièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "fffffff"](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|
|"F"|Si la valeur est différente de zéro, elle représente les dixièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "F"](#F_Specifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (pas de sortie)|
|"FF"|Si la valeur est différente de zéro, elle représente les centièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FF"](#FF_Specifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (pas de sortie)|
|"FFF"|Si la valeur est différente de zéro, elle représente les millisecondes dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FFF"](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (pas de sortie)|
|"FFFF"|Si la valeur est différente de zéro, elle représente les dix millièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FFFF"](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -> 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (pas de sortie)|
|"FFFFF"|Si la valeur est différente de zéro, elle représente les cent millièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FFFFF"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (pas de sortie)|
|"FFFFFF"|Si la valeur est différente de zéro, elle représente les millionièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (pas de sortie)|
|"FFFFFFF"|Si la valeur est différente de zéro, elle représente les dix millionièmes de seconde dans une valeur de date et d'heure.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "FFFFFFF"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|
|"g", "gg"|Période ou ère.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "g" ou "gg"](#gSpecifier).|2009-06-15T13:45:30.6170000 -> A.D.|
|"h"|Heure, au format de 12 heures, de 1 à 12.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "h"](#hSpecifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|
|"hh"|Heure, au format de 12 heures, de 01 à 12.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "hh"](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|
|"H"|Heure, au format de 24 heures, de 0 à 23.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "H"](#H_Specifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|
|"HH"|Heure, au format de 24 heures, de 00 à 23.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "HH"](#HH_Specifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|
|"K"|Informations de fuseau horaire.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "K"](#KSpecifier).|Avec les valeurs <xref:System.DateTime> :<br /><br /> 2009-06-15T13:45:30, Kind Unspecified -><br /><br /> 2009-06-15T13:45:30, Kind Utc -> Z<br /><br /> 2009-06-15T13:45:30, Kind Local -> -07:00 (dépend des paramètres de l'ordinateur local)<br /><br /> Avec les valeurs <xref:System.DateTimeOffset> :<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|
|"m"|Minute, définie entre 0 et 59.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "m"](#mSpecifier).|2009-06-15T01:09:30 -> 9<br /><br /> 2009-06-15T13:29:30 -> 29|
|"mm"|Minute, définie entre 00 et 59.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "mm"](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|
|"M"|Mois, de 1 à 12.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "M"](#M_Specifier).|2009-06-15T13:45:30 -> 6|
|"MM"|Mois, de 01 à 12.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "MM"](#MM_Specifier).|2009-06-15T13:45:30 -> 06|
|"MMM"|Nom abrégé du mois.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "MMM"](#MMM_Specifier).|2009-06-15T13:45:30 -> Jun (en-US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> Jun (zu-ZA)|
|"MMMM"|Nom complet du mois.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30 -> June (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|
|"s"|Seconde, de 0 à 59.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "s"](#sSpecifier).|2009-06-15T13:45:09 -> 9|
|"ss"|Seconde, de 00 à 59.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "ss"](#ssSpecifier).|2009-06-15T13:45:09 -> 09|
|"t"|Premier caractère de l'indicateur AM/PM.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "t"](#tSpecifier).|2009-06-15T13:45:30 -> P (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 ->  (fr-FR)|
|"tt"|Indicateur AM/PM.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "tt"](#ttSpecifier).|2009-06-15T13:45:30 -> PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30 ->  (fr-FR)|
|"y"|Année, de 0 à 99.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "y"](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yy"|Année, de 00 à 99.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "yy"](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yyy"|Année, avec au minimum trois chiffres.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "yyy"](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyy"|Année, en tant que nombre à quatre chiffres.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "yyyy"](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyyy"|Année, en tant que nombre à cinq chiffres.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "yyyyy"](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|
|"z"|Décalage horaire par rapport à l'heure UTC, sans zéro non significatif.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "z"](#zSpecifier).|2009-06-15T13:45:30-07:00 -> -7|
|"zz"|Décalage horaire par rapport à l'heure UTC, avec un zéro non significatif pour une valeur à un seul chiffre.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "zz"](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|
|"zzz"|Décalage horaire par rapport à l'heure UTC, en heures et minutes.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "zzz"](#zzzSpecifier).|2009-06-15T13:45:30-07:00 -> -07:00|
|":"|Séparateur horaire.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé ":"](#timeSeparator).|2009-06-15T13:45:30 -> : (en-US)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 -> : (ja-JP)|
|"/"|Séparateur de date.<br /><br /> Informations supplémentaires : [Spécificateur de format personnalisé "/"](#dateSeparator).|2009-06-15T13:45:30 -> / (en-US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|
|"*chaîne*"<br /><br /> '*string*'|Délimiteur de chaîne littérale.<br /><br /> Plus d’informations : [Littéraux de caractère](#Literals).|2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P|
|%|Définit le caractère suivant comme spécificateur de format personnalisé.<br /><br /> Informations supplémentaires : [Utilisation de spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|
|&#92;|Caractère d'échappement.<br /><br /> Plus d’informations : [Littéraux de caractère](#Literals) et [Utilisation du caractère d’échappement](#escape).|2009-06-15T13:45:30 (h \h) -> 1 h|
|N'importe quel autre caractère|Le caractère est copié inchangé dans la chaîne de résultat.<br /><br /> Plus d’informations : [Littéraux de caractère](#Literals).|2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A|

Les sections suivantes fournissent des informations supplémentaires sur chaque spécificateur de format de date et d'heure personnalisé. Sauf indication contraire, chaque spécificateur produit une représentation sous forme de chaîne identique qu’il soit utilisé avec une valeur <xref:System.DateTime> ou une valeur <xref:System.DateTimeOffset>.

## <a name="dSpecifier"></a> Le spécificateur de format personnalisé « d »

Le spécificateur de format personnalisé "d" représente le jour du mois sous la forme d'un nombre compris entre 1 et 31. Un jour à un seul chiffre est mis en forme sans zéro non significatif.

Si le spécificateur de format « d » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « d ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "d" dans plusieurs chaînes de format.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Retour au tableau](#table)

## <a name="ddSpecifier"></a> Le spécificateur de format personnalisé « dd »

Le spécificateur de format personnalisé "dd" représente le jour du mois sous la forme d'un nombre compris entre 01 et 31. Un jour à un seul chiffre est mis en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "dd" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Retour au tableau](#table)

## <a name="dddSpecifier"></a> Le spécificateur de format personnalisé « ddd »

Le spécificateur de format personnalisé "ddd" représente le nom abrégé du jour de la semaine. Le nom abrégé localisé du jour de la semaine est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> de la culture actuelle ou spécifiée.

L'exemple suivant inclut le spécificateur de format personnalisé "ddd" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Retour au tableau](#table)

## <a name="ddddSpecifier"></a> Le spécificateur de format personnalisé « dddd »

Le spécificateur de format personnalisé "dddd" (plus n'importe quel nombre de spécificateurs "d" supplémentaires) représente le nom complet du jour de la semaine. Le nom localisé du jour de la semaine est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> de la culture actuelle ou spécifiée.

L'exemple suivant inclut le spécificateur de format personnalisé "dddd" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Retour au tableau](#table)

## <a name="fSpecifier"></a> Le spécificateur de format personnalisé « f »

Le spécificateur de format personnalisé "f" représente le chiffre le plus significatif de la fraction de seconde ; autrement dit, il représente les dixièmes de seconde dans une valeur de date et d'heure.

Si le spécificateur de format « f » est utilisé sans autre spécificateur de format, il est interprété comme le spécificateur de format de date et d’heure standard « f ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

Lorsque vous utilisez "f" dans le cadre d'une chaîne de format fournie à la méthode <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A> ou <xref:System.DateTimeOffset.TryParseExact%2A>, le nombre de spécificateurs de format "f" utilisés indique le nombre des chiffres les plus significatifs de la fraction de seconde requis pour analyser correctement la chaîne.

L'exemple suivant inclut le spécificateur de format personnalisé "f" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Retour au tableau](#table)

## <a name="ffSpecifier"></a> Le spécificateur de format personnalisé « ff »

Le spécificateur de format personnalisé "ff" représente les deux chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les centièmes de seconde dans une valeur de date et d'heure.

L'exemple suivant inclut le spécificateur de format personnalisé "ff" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Retour au tableau](#table)

## <a name="fffSpecifier"></a> Le spécificateur de format personnalisé « fff »

Le spécificateur de format personnalisé "fff" représente les trois chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millisecondes dans une valeur de date et d'heure.

L'exemple suivant inclut le spécificateur de format personnalisé "fff" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Retour au tableau](#table)

## <a name="ffffSpecifier"></a> Le spécificateur de format personnalisé « ffff »

Le spécificateur de format personnalisé "ffff" représente les quatre chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millièmes de seconde dans une valeur de date et d'heure.

Bien qu’il soit possible d’afficher les dix millièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT version 3.5 (et ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="fffffSpecifier"></a> Le spécificateur de format personnalisé « fffff »

Le spécificateur de format personnalisé "fffff" représente les cinq chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les cent millièmes de seconde dans une valeur de date et d'heure.

Bien qu’il soit possible d’afficher les cent millièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="ffffffSpecifier"></a> Le spécificateur de format personnalisé « ffffff »

Le spécificateur de format personnalisé "ffffff" représente les six chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millionièmes de seconde dans une valeur de date et d'heure.

Bien qu’il soit possible d’afficher les millionièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="fffffffSpecifier"></a> Le spécificateur de format personnalisé « fffffff »

Le spécificateur de format personnalisé "fffffff" représente les sept chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millionièmes de seconde dans une valeur de date et d'heure.

Bien qu’il soit possible d’afficher les dix millionièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="F_Specifier"></a> Le spécificateur de format personnalisé « F »

Le spécificateur de format personnalisé "F" représente le chiffre le plus significatif de la fraction de seconde ; autrement dit, il représente les dixièmes de seconde dans une valeur de date et d'heure. Rien ne s'affiche si le chiffre est zéro.

Si le spécificateur de format « F » est utilisé sans autre spécificateur de format, il est interprété comme le spécificateur de format de date et d’heure standard « F ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

Le nombre de spécificateurs de format "F" utilisés avec la méthode <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A> ou <xref:System.DateTimeOffset.TryParseExact%2A> indique le nombre maximum possible des chiffres les plus significatifs de la fraction de seconde pour analyser correctement la chaîne.

L'exemple suivant inclut le spécificateur de format personnalisé "F" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Retour au tableau](#table)

## <a name="FF_Specifier"></a> Le spécificateur de format personnalisé « FF »

Le spécificateur de format personnalisé "FF" représente les deux chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les centièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin et doubles zéros ne sont pas affichés.

L'exemple suivant inclut le spécificateur de format personnalisé "FF" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Retour au tableau](#table)

## <a name="FFF_Specifier"></a> Le spécificateur de format personnalisé « FFF »

Le spécificateur de format personnalisé "FFF" représente les trois chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millisecondes dans une valeur de date et d'heure. Toutefois, les zéros de fin et triples zéros ne sont pas affichés.

L'exemple suivant inclut le spécificateur de format personnalisé "FFF" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Retour au tableau](#table)

## <a name="FFFF_Specifier"></a> Le spécificateur de format personnalisé « FFFF »

Le spécificateur de format personnalisé "FFFF" représente les quatre chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin et quadruples zéros ne sont pas affichés.

Bien qu’il soit possible d’afficher les dix millièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="FFFFF_Specifier"></a> Le spécificateur de format personnalisé « FFFFF »

Le spécificateur de format personnalisé "FFFFF" représente les cinq chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les cent millièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin et quintuples zéros ne sont pas affichés.

Bien qu’il soit possible d’afficher les cent millièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="FFFFFF_Specifier"></a> Le spécificateur de format personnalisé « FFFFFF »

Le spécificateur de format personnalisé "FFFFFF" représente les six chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millionièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin et sextuples zéros ne sont pas affichés.

Bien qu’il soit possible d’afficher les millionièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="FFFFFFF_Specifier"></a> Le spécificateur de format personnalisé « FFFFFFF »

Le spécificateur de format personnalisé "FFFFFFF" représente les sept chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millionièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin et septuples zéros ne sont pas affichés.

Bien qu’il soit possible d’afficher les dix millionièmes du composant « secondes » d’une valeur d’heure, cette valeur n’est pas forcément significative. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur les systèmes d’exploitation Windows NT 3.5 (et versions ultérieures) et Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.

[Retour au tableau](#table)

## <a name="gSpecifier"></a> Le spécificateur de format personnalisé « g » ou « gg »

Les spécificateurs de format personnalisés "g" ou "gg" (plus n'importe quel nombre de spécificateurs "g" supplémentaires) représentent la période ou l'ère, par exemple après J.-C. L’opération de mise en forme ignore ce spécificateur si la date à mettre en forme n’est associée à aucune chaîne de période ou d’ère.

Si le spécificateur de format « g » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « g ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "g" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Retour au tableau](#table)

## <a name="hSpecifier"></a> Le spécificateur de format personnalisé « h »

Le spécificateur de format personnalisé "h" représente l'heure sous la forme d'un nombre compris entre 1 et 12 ; autrement dit, l'heure est représentée au format de 12 heures qui compte les heures entières depuis minuit ou midi. Une heure après minuit se présente de la même manière que la même heure après midi. L'heure n'est pas arrondie et une heure à un seul chiffre est mise en forme sans zéro non significatif. Par exemple, si on considère l'heure 5:43 du matin ou de l'après-midi, ce spécificateur de format personnalisé affiche "5".

Si le spécificateur de format « h » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève une <xref:System.FormatException>. Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "h" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Retour au tableau](#table)

## <a name="hhSpecifier"></a> Le spécificateur de format personnalisé « hh »

Le spécificateur de format personnalisé "hh" (plus n'importe quel nombre de spécificateurs "h" supplémentaires) représente l'heure sous la forme d'un nombre compris entre 01 et 12 ; autrement dit, l'heure est représentée au format de 12 heures qui compte les heures entières depuis minuit ou midi. Une heure après minuit se présente de la même manière que la même heure après midi. L'heure n'est pas arrondie et une heure à un seul chiffre est mise en forme avec un zéro non significatif. Par exemple, si on considère l'heure 5:43 du matin ou de l'après-midi, ce spécificateur de format affiche "05".

L'exemple suivant inclut le spécificateur de format personnalisé "hh" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Retour au tableau](#table)

## <a name="H_Specifier"></a> Le spécificateur de format personnalisé « H »

Le spécificateur de format personnalisé "H" représente l'heure sous la forme d'un nombre compris entre 0 et 23 ; autrement dit, l'heure est représentée au format de 24 heures de base zéro qui compte les heures depuis minuit. Une heure à un seul chiffre est mise en forme sans zéro non significatif.

Si le spécificateur de format « H » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève une <xref:System.FormatException>. Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "H" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Retour au tableau](#table)

## <a name="HH_Specifier"></a> Le spécificateur de format personnalisé « HH »

Le spécificateur de format personnalisé "HH" (plus n'importe quel nombre de spécificateurs "H" supplémentaires) représente l'heure sous la forme d'un nombre compris entre 00 et 23 ; autrement dit, l'heure est représentée au format de 24 heures de base zéro qui compte les heures depuis minuit. Une heure à un seul chiffre est mise en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "HH" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Retour au tableau](#table)

## <a name="KSpecifier"></a> Le spécificateur de format personnalisé « K »

Le spécificateur de format personnalisé "K" représente les informations de fuseau horaire d'une valeur de date et d'heure. Lorsque ce spécificateur de format est utilisé avec les valeurs <xref:System.DateTime>, la chaîne de résultat est définie par la valeur de la propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> :

- Pour le fuseau horaire local (une valeur de propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> de <xref:System.DateTimeKind.Local?displayProperty=nameWithType>), ce spécificateur est équivalent au spécificateur "zzz" et produit une chaîne de résultat contenant l'offset local par rapport au temps universel coordonné (UTC, Universal Time Coordinated) ; par exemple, "-07:00".

- Pour une heure UTC (une valeur de propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> de <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), la chaîne de résultat inclut un caractère "Z" pour représenter une date UTC.

- Pour une heure d'un fuseau horaire non spécifié (une heure dont la propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> a la valeur <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), le résultat est équivalent à <xref:System.String.Empty?displayProperty=nameWithType>.

Pour les valeurs <xref:System.DateTimeOffset>, le spécificateur de format "K" est équivalent au spécificateur de format "zzz", et produit une chaîne de résultat contenant l'offset de la valeur <xref:System.DateTimeOffset> par rapport à l'heure UTC.

Si le spécificateur de format « K » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève une <xref:System.FormatException>. Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant affiche la chaîne qui résulte de l'utilisation du spécificateur de format personnalisé "K" avec différentes valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sur un système situé dans le fuseau horaire Pacifique (États-Unis).

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Retour au tableau](#table)

## <a name="mSpecifier"></a> Le spécificateur de format personnalisé « m »

Le spécificateur de format personnalisé "m" représente la minute sous la forme d'un nombre compris entre 0 et 59. La minute représente les minutes entières qui se sont écoulées depuis la dernière heure. Une minute à un seul chiffre est mise en forme sans zéro non significatif.

Si le spécificateur de format « m » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « m ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "m" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Retour au tableau](#table)

## <a name="mmSpecifier"></a> Le spécificateur de format personnalisé « mm »

Le spécificateur de format personnalisé "mm" (plus n'importe quel nombre de spécificateurs "m" supplémentaires) représente la minute sous la forme d'un nombre compris entre 00 et 59. La minute représente les minutes entières qui se sont écoulées depuis la dernière heure. Une minute à un seul chiffre est mise en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "mm" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Retour au tableau](#table)

## <a name="M_Specifier"></a> Le spécificateur de format personnalisé « M »

Le spécificateur de format personnalisé "M" représente le mois comme un nombre compris entre 1 et 12 (ou entre 1 et 13 pour les calendriers de 13 mois). Un mois à un seul chiffre est mis en forme sans zéro non significatif.

Si le spécificateur de format « M » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « M ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "M" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Retour au tableau](#table)

## <a name="MM_Specifier"></a> Le spécificateur de format personnalisé « MM »

Le spécificateur de format personnalisé "MM" représente le mois comme un nombre compris entre 01 et 12 (ou entre 01 et 13 pour les calendriers de 13 mois). Un mois à un seul chiffre est mis en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "MM" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Retour au tableau](#table)

## <a name="MMM_Specifier"></a> Le spécificateur de format personnalisé « MMM »

Le spécificateur de format personnalisé "MMM" représente le nom abrégé du mois. Le nom abrégé localisé du mois est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> de la culture actuelle ou spécifiée.

L'exemple suivant inclut le spécificateur de format personnalisé "MMM" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Retour au tableau](#table)

## <a name="MMMM_Specifier"></a> Le spécificateur de format personnalisé « MMMM »

Le spécificateur de format personnalisé "MMMM" représente le nom complet du mois. Le nom localisé du mois est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> de la culture actuelle ou spécifiée.

L'exemple suivant inclut le spécificateur de format personnalisé "MMMM" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Retour au tableau](#table)

## <a name="sSpecifier"></a> Le spécificateur de format personnalisé « s »

Le spécificateur de format personnalisé "s" représente les secondes sous la forme d'un nombre compris entre 0 et 59. Le résultat représente les secondes entières qui se sont écoulées depuis la dernière minute. Une seconde à un seul chiffre est mise en forme sans zéro non significatif.

Si le spécificateur de format « s » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « s ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "s" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Retour au tableau](#table)

## <a name="ssSpecifier"></a> Le spécificateur de format personnalisé « ss »

Le spécificateur de format personnalisé "ss" (plus n'importe quel nombre de spécificateurs "s" supplémentaires) représente les secondes sous la forme d'un nombre compris entre 00 et 59. Le résultat représente les secondes entières qui se sont écoulées depuis la dernière minute. Une seconde à un seul chiffre est mise en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "ss" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Retour au tableau](#table)

## <a name="tSpecifier"></a> Le spécificateur de format personnalisé « t »

Le spécificateur de format personnalisé "t" représente le premier caractère de l'indicateur AM/PM. L'indicateur localisé approprié est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> ou <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> de la culture actuelle ou spécifique. L'indicateur AM est utilisé pour toutes les heures comprises entre 0:00:00 (minuit) et 11:59:59.999. L'indicateur PM est utilisé pour toutes les heures comprises entre 12:00:00 (midi) et 23:59:59.999.

Si le spécificateur de format « t » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « t ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "t" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Retour au tableau](#table)

## <a name="ttSpecifier"></a> Le spécificateur de format personnalisé « tt »

Le spécificateur de format personnalisé "tt" (plus n'importe quel nombre de spécificateurs "t" supplémentaires) représente l'intégralité de l'indicateur AM/PM. L'indicateur localisé approprié est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> ou <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> de la culture actuelle ou spécifique. L'indicateur AM est utilisé pour toutes les heures comprises entre 0:00:00 (minuit) et 11:59:59.999. L'indicateur PM est utilisé pour toutes les heures comprises entre 12:00:00 (midi) et 23:59:59.999.

Veillez à utiliser le spécificateur « tt » dans les langues pour lesquelles il est nécessaire de maintenir la distinction entre le matin (AM) et l’après-midi (PM). Un exemple est illustré par la langue japonaise, pour laquelle les indicateurs AM/PM se distinguent dans le deuxième caractère au lieu du premier.

L'exemple suivant inclut le spécificateur de format personnalisé "tt" dans une chaîne de format personnalisée.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Retour au tableau](#table)

## <a name="ySpecifier"></a> Le spécificateur de format personnalisé « y »

Le spécificateur de format personnalisé "y" représente l'année sous la forme d'un nombre à un chiffre ou à deux chiffres. Si l'année comporte plus de deux chiffres, seuls les deux chiffres de poids faible apparaissent dans le résultat. Si le premier chiffre d'une année sur deux chiffres commence par un zéro (par exemple, 2008), le nombre est mis en forme sans zéro non significatif.

Si le spécificateur de format « y » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d’heure standard « y ». Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "y" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Retour au tableau](#table)

## <a name="yySpecifier"></a> Le spécificateur de format personnalisé « yy »

Le spécificateur de format personnalisé "yy" représente l'année sous la forme d'un nombre à deux chiffres. Si l'année comporte plus de deux chiffres, seuls les deux chiffres de poids faible apparaissent dans le résultat. Si l'année à deux chiffres comporte moins de deux chiffres significatifs, le nombre est complété avec des zéros non significatifs pour qu'il possède deux chiffres.

Dans une opération d'analyse, une année à deux chiffres qui est analysée avec le spécificateur de format personnalisé "yy" est interprétée sur la base de la propriété <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> du calendrier actuel du fournisseur de format. L'exemple suivant analyse la représentation sous forme de chaîne d'une date ayant une année à deux chiffres, en utilisant le calendrier grégorien par défaut de la culture en-US, laquelle représente la culture actuelle. Il remplace ensuite l'objet <xref:System.Globalization.CultureInfo> de la culture actuelle afin d'utiliser un objet <xref:System.Globalization.GregorianCalendar> dont la propriété <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> a été modifiée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

L'exemple suivant inclut le spécificateur de format personnalisé "yy" dans une chaîne de format personnalisé.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Retour au tableau](#table)

## <a name="yyySpecifier"></a> Le spécificateur de format personnalisé « yyy »

Le spécificateur de format personnalisé "yyy" représente l'année avec un minimum de trois chiffres. Si l'année comporte plus de trois chiffres significatifs, ils sont inclus dans la chaîne résultante. Si l'année comporte moins de trois chiffres, le nombre est rempli avec des zéros non significatifs pour produire trois chiffres.

> [!NOTE]
> Pour le calendrier bouddhiste thaïlandais, qui peut comporter des années à cinq chiffres, ce spécificateur de format affiche tous les chiffres significatifs.

L'exemple suivant inclut le spécificateur de format personnalisé "yyy" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Retour au tableau](#table)

## <a name="yyyySpecifier"></a> Le spécificateur de format personnalisé « yyyy »

Le spécificateur de format personnalisé "yyyy" représente l'année avec un minimum de quatre chiffres. Si l'année comporte plus de quatre chiffres significatifs, ils sont inclus dans la chaîne résultante. Si l'année comporte moins de quatre chiffres, le nombre est rempli à l'aide de zéros non significatifs pour produire quatre chiffres.

> [!NOTE]
> Pour le calendrier bouddhiste thaïlandais, qui peut comporter des années à cinq chiffres, ce spécificateur de format affiche au minimum quatre chiffres.

L'exemple suivant inclut le spécificateur de format personnalisé "yyyy" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Retour au tableau](#table)

## <a name="yyyyySpecifier"></a> Le spécificateur de format personnalisé « yyyyy »

Le spécificateur de format personnalisé "yyyyy" (plus tout nombre de spécificateurs "y" supplémentaires) représente l'année avec au minimum cinq chiffres. Si l'année comporte plus de cinq chiffres significatifs, ils sont inclus dans la chaîne résultante. Si l'année comporte moins de cinq chiffres, le nombre est rempli avec des zéros non significatifs pour produire cinq chiffres.

S'il existe des spécificateurs "y" supplémentaires, le nombre est rempli avec autant de zéros non significatifs que nécessaire pour produire le nombre de spécificateurs "y".

L'exemple suivant inclut le spécificateur de format personnalisé "yyyyy" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Retour au tableau](#table)

## <a name="zSpecifier"></a> Le spécificateur de format personnalisé « z »

Avec les valeurs <xref:System.DateTime>, le spécificateur de format personnalisé "z" représente l'offset signé du fuseau horaire du système d'exploitation local par rapport au temps universel coordonné (UTC, Coordinated Universal Time), mesuré en heures. Il ne reflète pas la valeur de la propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> d’une instance. C'est pourquoi il n'est pas recommandé d'utiliser le spécificateur de format "z" avec les valeurs <xref:System.DateTime>.

Avec les valeurs <xref:System.DateTimeOffset>, ce spécificateur de format représente l'offset de la valeur <xref:System.DateTimeOffset> par rapport à l'heure UTC, en heures.

L'offset est toujours affiché avec un signe de début. Un signe plus (+) indique les heures avant l'heure UTC, et un signe moins (-) indique les heures après l'heure UTC. Un offset à un seul chiffre est mis en forme sans zéro non significatif.

Si le spécificateur de format « z » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève une <xref:System.FormatException>. Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "z" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Retour au tableau](#table)

## <a name="zzSpecifier"></a> Le spécificateur de format personnalisé « zz »

Avec les valeurs <xref:System.DateTime>, le spécificateur de format personnalisé "zz" représente l'offset signé du fuseau horaire du système d'exploitation local par rapport à l'heure UTC, mesuré en heures. Il ne reflète pas la valeur de la propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> d’une instance. C'est pourquoi il n'est pas recommandé d'utiliser le spécificateur de format "zz" avec les valeurs <xref:System.DateTime>.

Avec les valeurs <xref:System.DateTimeOffset>, ce spécificateur de format représente l'offset de la valeur <xref:System.DateTimeOffset> par rapport à l'heure UTC, en heures.

L'offset est toujours affiché avec un signe de début. Un signe plus (+) indique les heures avant l'heure UTC, et un signe moins (-) indique les heures après l'heure UTC. Un offset à un seul chiffre est mis en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "zz" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Retour au tableau](#table)

## <a name="zzzSpecifier"></a> Le spécificateur de format personnalisé « zzz »

Avec les valeurs <xref:System.DateTime>, le spécificateur de format personnalisé "zzz" représente l'offset signé du fuseau horaire du système d'exploitation local par rapport à l'heure UTC, mesuré en heures et en minutes. Il ne reflète pas la valeur de la propriété <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> d’une instance. C'est pourquoi il n'est pas recommandé d'utiliser le spécificateur de format "zzz" avec les valeurs <xref:System.DateTime>.

Avec les valeurs <xref:System.DateTimeOffset>, ce spécificateur de format représente l'offset de la valeur <xref:System.DateTimeOffset> par rapport à l'heure UTC, en heures et en minutes.

L'offset est toujours affiché avec un signe de début. Un signe plus (+) indique les heures avant l'heure UTC, et un signe moins (-) indique les heures après l'heure UTC. Un offset à un seul chiffre est mis en forme avec un zéro non significatif.

L'exemple suivant inclut le spécificateur de format personnalisé "zzz" dans une chaîne de format personnalisée.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Retour au tableau](#table)

## <a name="timeSeparator"></a> Le spécificateur de format personnalisé « : »
Le spécificateur de format personnalisé ":" représente le séparateur d'heure, lequel est utilisé pour différencier les heures, les minutes et les secondes. Le séparateur d'heure localisé approprié est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> de la culture actuelle ou spécifiée.

> [!NOTE]
> Pour modifier le séparateur horaire d'une chaîne de date et heure, spécifiez le caractère de séparation dans un délimiteur de chaîne littérale. Par exemple, la chaîne de format personnalisée `hh'_'dd'_'ss` produit une chaîne de résultat dans laquelle "\_" (trait de soulignement) est toujours utilisé comme séparateur horaire. Pour modifier le séparateur horaire de toutes les dates d'une culture, modifiez la valeur de la propriété <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> de la culture actuelle, ou instanciez un objet <xref:System.Globalization.DateTimeFormatInfo>, affectez le caractère à sa propriété <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>, puis appelez une surcharge de la méthode de mise en forme qui inclut un paramètre <xref:System.IFormatProvider>.

Si le spécificateur de format « : » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève une <xref:System.FormatException>. Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

[Retour au tableau](#table)

## <a name="dateSeparator"></a> Le spécificateur de format personnalisé « / »

Le spécificateur de format personnalisé "/" représente le séparateur de date, lequel est utilisé pour différencier les années, les mois et les jours. Le séparateur de date localisé approprié est récupéré de la propriété <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> de la culture actuelle ou spécifiée.

> [!NOTE]
> Pour modifier le séparateur de date d'une chaîne de date et heure, spécifiez le caractère de séparation dans un délimiteur de chaîne littérale. Par exemple, la chaîne de format personnalisée `mm'/'dd'/'yyyy` produit une chaîne de résultat dans laquelle "/" est toujours utilisé comme séparateur de date. Pour modifier le séparateur de date de toutes les dates d'une culture, modifiez la valeur de la propriété <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> de la culture actuelle, ou instanciez un objet <xref:System.Globalization.DateTimeFormatInfo>, affectez le caractère à sa propriété <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>, puis appelez une surcharge de la méthode de mise en forme qui inclut un paramètre <xref:System.IFormatProvider>.

Si le spécificateur de format « / » est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève une <xref:System.FormatException>. Pour plus d’informations sur l’utilisation d’un seul spécificateur de format, voir [Utiliser des spécificateurs de format personnalisés uniques](#UsingSingleSpecifiers) plus loin dans cette rubrique.

[Retour au tableau](#table)

## <a name="Literals"></a> Les littéraux de caractère

Les caractères suivants dans une chaîne de format de date et d’heure standard ou personnalisée sont réservés et sont toujours interprétés comme des caractères de mise en forme ou, dans le cas de ", ', / et \\ comme des caractères spéciaux.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|f|g|h|m|s|
|t|y|z|%| :|
|/|« |'|&#92;||

Tous les autres caractères sont toujours interprétés comme des caractères littéraux et, dans une opération de mise en forme, sont inclus inchangés dans la chaîne de résultat.  Dans une opération d’analyse, ils doivent correspondre exactement aux caractères présents dans la chaîne d’entrée. La comparaison respecte la casse.

L’exemple suivant inclut les caractères littéraux « PST » (pour Pacific Standard Time, heure normale du Pacifique) et « PDT » (pour Pacific Daylight Time, heure d’été du Pacifique) pour représenter le fuseau horaire local dans une chaîne de format. Notez que la chaîne est incluse dans la chaîne de résultat, et qu’une chaîne qui inclut la chaîne du fuseau horaire local est également analysée avec succès.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Il existe deux façons d’indiquer que les caractères doivent être interprétés comme des caractères littéraux, et non comme des caractères réservés, pour qu’ils puissent être inclus dans une chaîne de résultat ou analysés correctement dans une chaîne d’entrée :

- En plaçant chaque caractère réservé dans une séquence d’échappement. Pour plus d’informations, consultez [Utilisation du caractère d’échappement](#escape).

L’exemple suivant inclut les caractères littéraux « pst » (pour Pacific Standard Time, heure normale du Pacifique) pour représenter le fuseau horaire local dans une chaîne de format. Étant donné que « s » et « t » sont des chaînes de format personnalisées, les deux caractères doivent être placés dans des séquences d’échappement pour être interprétés comme des littéraux de caractères.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- En plaçant la totalité de la chaîne littérale entre guillemets ou apostrophes. L’exemple suivant est semblable au précédent, excepté que « pst » est placé entre guillemets pour indiquer que la totalité de la chaîne délimitée doit être interprétée comme des littéraux de caractères.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Remarques

### <a name="UsingSingleSpecifiers"></a> Utiliser des spécificateurs de format personnalisés uniques

Une chaîne de format de date et d'heure personnalisée se compose d'au moins deux caractères. Les méthodes de mise en forme de la date et de l'heure interprètent toute chaîne à un caractère comme une chaîne de format de date et d'heure standard. Si elles ne reconnaissent pas le caractère comme un spécificateur de format valide, elles lèvent une <xref:System.FormatException>. Par exemple, une chaîne de format qui se compose uniquement du spécificateur "h" est interprétée comme une chaîne de format de date et d'heure standard. Cependant, dans ce cas particulier, une exception est levée, car il n'existe pas spécificateur de formatde date et d'heure "h" standard.

Pour utiliser tout spécificateur de format de date et d'heure personnalisé comme seul spécificateur dans une chaîne de format (autrement dit, utiliser le spécificateur de format personnalisé "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" ou "/" tout seul), incluez un espace avant ou après le spécificateur, ou incluez un spécificateur de format pourcentage ("%") avant le spécificateur de date et d'heure personnalisé unique.

Par exemple », "`%h"`" est interprété en tant que chaîne de format de date et d'heure personnalisée qui affiche l'heure représentée par la valeur de date et d'heure actuelle. Vous pouvez également utiliser la chaîne de format "h" ou "h", bien que cela inclue un espace avec l'heure dans la chaîne de résultat. L'exemple suivant illustre ces trois chaînes de format.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="escape"></a> Utiliser le caractère d’échappement

Les caractères "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" ou "/" dans une chaîne de format sont interprétés comme des spécificateurs de format personnalisés plutôt que comme des caractères littéraux. Pour éviter qu’un caractère soit interprété comme un spécificateur de format, vous pouvez le faire précéder d’une barre oblique inverse (\\), qui est le caractère d’échappement. Le caractère d'échappement signifie que le caractère suivant est un caractère littéral qui doit être inclus inchangé dans la chaîne de résultat.

Pour inclure une barre oblique inverse dans une chaîne de résultat, vous devez la placer dans une séquence d'échappement avec une autre barre oblique inverse (`\\`).

> [!NOTE]
> Certains compilateurs, tels que les compilateurs C++ et C#, peuvent également interpréter une barre oblique inverse unique comme un caractère d'échappement. Pour garantir l'interprétation correcte d'une chaîne lors de la mise en forme, vous pouvez utiliser le caractère littéral de chaîne textuel(le caractère @) avant la chaîne en C#, ou ajouter une autre barre oblique inverse avant chaque barre oblique inverse en C# et C++. L'exemple C# suivant illustre ces deux approches.

L'exemple suivant utilise le caractère d'échappement pour empêcher l'opération de mise en forme d'interpréter les caractères "h" et "m" comme des spécificateurs de format.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Paramètres du panneau de configuration

Les paramètres **Options régionales et linguistiques** du Panneau de configuration influencent la chaîne de résultat produite par une opération de mise en forme qui inclut une grande partie des spécificateurs de format de date et d’heure personnalisés. Ces paramètres sont utilisés pour initialiser l'objet <xref:System.Globalization.DateTimeFormatInfo> associé à la culture du thread en cours qui fournit des valeurs utilisées pour indiquer la mise en forme. Les ordinateurs qui utilisent des paramètres différents génèrent des chaînes de résultat différentes.

De plus, si vous utilisez le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> pour instancier un nouvel objet <xref:System.Globalization.CultureInfo> qui représente la même culture que la culture système en cours, toutes les personnalisations établies par l'élément **Options régionales et linguistiques** du Panneau de configuration seront appliquées au nouvel objet <xref:System.Globalization.CultureInfo>. Vous pouvez utiliser le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> pour créer un objet <xref:System.Globalization.CultureInfo> qui ne reflète pas les personnalisations d’un système.

### <a name="datetimeformatinfo-properties"></a>Propriétés DateTimeFormatInfo

La mise en forme dépend des propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> actif, qui est fourni implicitement par la culture actuelle du thread ou explicitement par le paramètre <xref:System.IFormatProvider> de la méthode qui appelle la mise en forme. Pour le paramètre <xref:System.IFormatProvider>, vous devez spécifier un objet <xref:System.Globalization.CultureInfo> qui représente une culture, ou un objet <xref:System.Globalization.DateTimeFormatInfo>.

La chaîne de résultat produite par la plupart des spécificateurs de format de date et d'heure personnalisés dépend également des propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> actif. Votre application peut modifier le résultat produit par certains spécificateurs de format de date et d'heure personnalisés en modifiant la propriété <xref:System.Globalization.DateTimeFormatInfo> correspondante. Par exemple, le spécificateur de format "ddd" ajoute à la chaîne de résultat le nom abrégé d'un jour de la semaine trouvé dans le tableau de chaînes <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>. De la même façon, le spécificateur de format "MMMM" ajoute à la chaîne de résultat un nom de mois complet trouvé dans le tableau de chaînes <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>.

## <a name="see-also"></a>Voir aussi

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)
- [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
