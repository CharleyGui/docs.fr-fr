---
title: Chaînes de format TimeSpan personnalisées
description: Comprendre les chaînes de format TimeSpan personnalisées dans .NET. Une chaîne de format personnalisée contient un ou plusieurs spécificateurs de format TimeSpan & un nombre quelconque de caractères littéraux.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, custom time interval
- format strings
- formatting [.NET], time interval
- custom time interval format strings
- formatting [.NET], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
ms.openlocfilehash: b760e7ab7f39d4e4682d5d4c3a6421b9843e1d59
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888683"
---
# <a name="custom-timespan-format-strings"></a>Chaînes de format TimeSpan personnalisées

Une chaîne de format <xref:System.TimeSpan> définit la représentation sous forme de chaîne d’une valeur <xref:System.TimeSpan> qui résulte d’une opération de mise en forme. Une chaîne de format personnalisée se compose d’un ou de plusieurs spécificateurs de format <xref:System.TimeSpan> personnalisé et d’un nombre quelconque de caractères littéraux. Toute chaîne qui n’est pas une [chaîne de format TimeSpan standard](standard-timespan-format-strings.md) est interprétée comme une <xref:System.TimeSpan> chaîne de format personnalisée.

> [!IMPORTANT]
> Les spécificateurs de format <xref:System.TimeSpan> personnalisés ne comportent pas de symboles de séparation de type espace réservé, comme ceux qui séparent les jours des heures, les heures des minutes ou les secondes des fractions de seconde. Au lieu de cela, ces symboles doivent figurer dans la chaîne de format personnalisée comme littéraux de chaîne. Par exemple, `"dd\.hh\:mm"` définit un point (.) comme séparateur entre les jours et les heures et un signe deux-points (:) comme séparateur entre les heures et les minutes.
>
> Les spécificateurs de format <xref:System.TimeSpan> personnalisés ne comportent pas non plus de symbole de signe permettant de faire la distinction entre les intervalles de temps positifs et négatifs. Pour inclure un symbole de signe, vous devez construire une chaîne de format à l’aide d’une logique conditionnelle. La section [autres caractères](#other-characters) contient un exemple.

Les représentations sous forme de chaîne de valeurs <xref:System.TimeSpan> sont produites par des appels aux surcharges de la méthode <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType>, ainsi que par les méthodes qui prennent en charge la mise en forme composite, telles que <xref:System.String.Format%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [Mise en forme des types](formatting-types.md) et [Mise en forme composite](composite-formatting.md). L'exemple suivant illustre l'utilisation de chaînes de format personnalisé dans des opérations de mise en forme.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Les chaînes de format <xref:System.TimeSpan> standard sont également utilisées par les méthodes <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> et <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> pour définir le format requis des chaînes d'entrée pour les opérations d'analyse. (L’analyse convertit la représentation sous forme de chaîne d’une valeur en cette valeur.) L’exemple suivant illustre l’utilisation de chaînes de format standard dans les opérations d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a> Le tableau suivant décrit les spécificateurs de format de date et d'heure personnalisé.

| Spécificateur de format | Description | Exemple |
|----------------------|-----------------|-------------|
|"d", "%d"|Nombre de jours entiers dans l’intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "d"](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"dd" à "dddddddd"|Nombre de jours entiers dans l’intervalle de temps, complété avec des zéros non significatifs en fonction des besoins.<br /><br /> Informations supplémentaires : [spécificateurs de format personnalisé "dd"-"dddddddd"](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "%h"|Nombre d’heures entières de l’intervalle de temps non comptabilisées dans des jours. Les heures à un chiffre n’ont pas de zéro non significatif.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "h"](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|"hh"|Nombre d’heures entières de l’intervalle de temps non comptabilisées dans des jours. Les heures à un chiffre ont un zéro non significatif.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "HH"](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"m", "%m"|Nombre de minutes entières de l’intervalle de temps non comptabilisées dans des jours ou des heures. Les minutes à un chiffre n’ont pas de zéro non significatif.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "m"](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|"mm"|Nombre de minutes entières de l’intervalle de temps non comptabilisées dans des jours ou des heures. Les minutes à un chiffre ont un zéro non significatif.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "mm"](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "%s"|Nombre de secondes entières de l’intervalle de temps non comptabilisées dans des jours, des heures ou des minutes. Les secondes à un chiffre n’ont pas de zéro non significatif.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "s"](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|"ss"|Nombre de secondes entières de l’intervalle de temps non comptabilisées dans des jours, des heures ou des minutes.  Les secondes à un chiffre ont un zéro non significatif.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "SS"](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "%f"|Dixièmes de seconde dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "f"](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|"ff"|Centièmes de seconde dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "FF"](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|"fff"|Millisecondes dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "fff"](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|"ffff"|Dix millièmes de seconde dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "FFFF"](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|"fffff"|Cent millièmes de seconde dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "fffff"](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|"ffffff"|Millionièmes de seconde dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "FFFFFF"](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|"fffffff"|Dix millionièmes de seconde (ou nombre fractionnaire de graduations) dans un intervalle de temps.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "fffffff"](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "%F"|Dixièmes de seconde dans un intervalle de temps. Rien ne s'affiche si le chiffre est zéro.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "F"](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Centièmes de seconde dans un intervalle de temps. Les éventuels zéros de fin fractionnaires et doubles zéros ne sont pas affichés.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Millisecondes dans un intervalle de temps. Les éventuels zéros de fin fractionnaires ne sont pas affichés.<br /><br /> Plus d’informations :|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|Dix millièmes de seconde dans un intervalle de temps. Les éventuels zéros de fin fractionnaires ne sont pas affichés.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Cent millièmes de seconde dans un intervalle de temps. Les éventuels zéros de fin fractionnaires ne sont pas affichés.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "fffff"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Millionièmes de seconde dans un intervalle de temps. Les éventuels zéros de fin fractionnaires ne sont pas affichés.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|Dix millionièmes de seconde dans un intervalle de temps. Les éventuels zéros de fin fractionnaires et septuples zéros ne sont pas affichés.<br /><br /> Informations supplémentaires : [spécificateur de format personnalisé "fffffff"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|' *chaîne* '|Délimiteur de chaîne littérale.<br /><br /> Informations supplémentaires : [autres caractères](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|&#92;|Caractère d'échappement.<br /><br /> Informations supplémentaires : [autres caractères](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|N'importe quel autre caractère|Tout autre caractère sans séquence d’échappement est interprété comme un spécificateur de format personnalisé.<br /><br /> Informations supplémentaires : [autres caractères](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

## <a name="the-d-custom-format-specifier"></a><a name="dSpecifier"></a> Le spécificateur de format personnalisé « d »

Le spécificateur de format personnalisé "d" affiche la valeur de la propriété <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType>, qui représente le nombre de jours entiers dans l’intervalle de temps. Il affiche le nombre total de jours dans une valeur <xref:System.TimeSpan>, même si la valeur a plusieurs chiffres. Si la valeur de la propriété <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> est zéro, le spécificateur retourne "0".

Si le spécificateur de format personnalisé « d » est utilisé seul, spécifiez « %d » afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Retour au tableau](#table)

## <a name="the-dd-dddddddd-custom-format-specifiers"></a><a name="ddSpecifier"></a> Spécificateurs de format personnalisé "dd"-"dddddddd"

Les spécificateurs de format personnalisé "dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" et "dddddddd" affichent la valeur de la propriété <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType>, qui représente le nombre de jours entiers dans l’intervalle de temps.

La chaîne de sortie comporte un nombre minimal de chiffres spécifié par le nombre de caractères « d » dans le spécificateur de format ; elle est complétée par des zéros non significatifs si nécessaire. Si les chiffres dans le nombre de jours dépassent le nombre de caractères « d » dans le spécificateur de format, le nombre total de jours est affiché dans la chaîne de résultat.

L’exemple suivant utilise ces spécificateurs de format pour afficher la représentation sous forme de chaîne de deux valeurs <xref:System.TimeSpan>. La valeur du composant « jours » du premier intervalle de temps est zéro ; la valeur du composant « jours » du deuxième est 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Retour au tableau](#table)

## <a name="the-h-custom-format-specifier"></a><a name="hSpecifier"></a> Spécificateur de format personnalisé "h"

Le spécificateur de format personnalisé « h » donne la valeur de la propriété <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType>, qui représente le nombre d’heures entières de l’intervalle de temps non comptabilisées dans son composant « jours ». Il retourne une valeur de chaîne à un chiffre si la valeur de la propriété <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> est comprise entre 0 et 9, ou une valeur de chaîne à deux chiffres si la valeur de la propriété <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> est comprise entre 10 et 23.

Si le spécificateur de format personnalisé « h » est utilisé seul, spécifiez « %h » afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "%h" à la place pour interpréter la chaîne numérique comme nombre d’heures. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Retour au tableau](#table)

## <a name="the-hh-custom-format-specifier"></a><a name="hhSpecifier"></a> Spécificateur de format personnalisé "HH"

Le spécificateur de format personnalisé « hh » donne la valeur de la propriété <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType>, qui représente le nombre d’heures entières de l’intervalle de temps non comptabilisées dans son composant « jours ». Pour les valeurs 0 à 9, la chaîne de sortie inclut un zéro non significatif.

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "hh" à la place pour interpréter la chaîne numérique comme nombre d’heures. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "hh".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Retour au tableau](#table)

## <a name="the-m-custom-format-specifier"></a><a name="mSpecifier"></a> Spécificateur de format personnalisé "m"

Le spécificateur de format personnalisé « mm » donne la valeur de la propriété <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType>, qui représente le nombre de minutes entières de l’intervalle de temps non comptabilisées dans son composant « jours ». Il retourne une valeur de chaîne à un chiffre si la valeur de la propriété <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> est comprise entre 0 et 9, ou une valeur de chaîne à deux chiffres si la valeur de la propriété <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> est comprise entre 10 et 59.

Si le spécificateur de format personnalisé « m » est utilisé seul, spécifiez « %m » afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "%m" à la place pour interpréter la chaîne numérique comme nombre de minutes. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Retour au tableau](#table)

## <a name="the-mm-custom-format-specifier"></a><a name="mmSpecifier"></a> Spécificateur de format personnalisé "mm"

Le spécificateur de format personnalisé « mm » donne la valeur de la propriété <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType>, qui représente le nombre de minutes entières de l’intervalle de temps non comptabilisées dans son composant « jours » ou « heures ». Pour les valeurs 0 à 9, la chaîne de sortie inclut un zéro non significatif.

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "mm" à la place pour interpréter la chaîne numérique comme nombre de minutes. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Retour au tableau](#table)

## <a name="the-s-custom-format-specifier"></a><a name="sSpecifier"></a> Spécificateur de format personnalisé "s"

Le spécificateur de format personnalisé « s » donne la valeur de la propriété <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType>, qui représente le nombre de secondes entières de l’intervalle de temps non comptabilisées dans son composant « jours », « heures » ou « minutes ». Il retourne une valeur de chaîne à un chiffre si la valeur de la propriété <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> est comprise entre 0 et 9, ou une valeur de chaîne à deux chiffres si la valeur de la propriété <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> est comprise entre 10 et 59.

Si le spécificateur de format personnalisé « s » est utilisé seul, spécifiez « %s » afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "%s" à la place pour interpréter la chaîne numérique comme nombre de secondes. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Retour au tableau](#table)

## <a name="the-ss-custom-format-specifier"></a><a name="ssSpecifier"></a> Spécificateur de format personnalisé "SS"

Le spécificateur de format personnalisé « ss » donne la valeur de la propriété <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType>, qui représente le nombre de secondes entières de l’intervalle de temps non comptabilisées dans son composant « jours », « heures » ou « minutes ». Pour les valeurs 0 à 9, la chaîne de sortie inclut un zéro non significatif.

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "ss" à la place pour interpréter la chaîne numérique comme nombre de secondes. L'exemple suivant illustre cette situation.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "ss".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Retour au tableau](#table)

## <a name="the-f-custom-format-specifier"></a><a name="fSpecifier"></a> Spécificateur de format personnalisé "f"

Le spécificateur de format personnalisé "f" affiche les dixièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement un chiffre fractionnaire.

Si le spécificateur de format personnalisé « f » est utilisé seul, spécifiez « %f » afin qu’il ne soit pas interprété à tort comme une chaîne de format standard.

L’exemple suivant utilise le spécificateur de format personnalisé "f" pour afficher les dixièmes de seconde dans une valeur <xref:System.TimeSpan>. "f" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-ff-custom-format-specifier"></a><a name="ffSpecifier"></a> Spécificateur de format personnalisé "FF"

Le spécificateur de format personnalisé "ff" affiche les centièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement deux chiffres fractionnaires.

L’exemple suivant utilise le spécificateur de format personnalisé "ff" pour afficher les centièmes de seconde dans une valeur <xref:System.TimeSpan>. "ff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-fff-custom-format-specifier"></a><a name="f3Specifier"></a> Le spécificateur de format personnalisé « fff »

Le spécificateur de format personnalisé "fff" (trois caractères « f ») affiche les millisecondes dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement trois chiffres fractionnaires.

L’exemple suivant utilise le spécificateur de format personnalisé "fff" pour afficher les millisecondes dans une valeur <xref:System.TimeSpan>. "fff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-ffff-custom-format-specifier"></a><a name="f4Specifier"></a> Spécificateur de format personnalisé "FFFF"

Le spécificateur de format personnalisé "ffff" (quatre caractères « f ») affiche les dix millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement quatre chiffres fractionnaires.

L’exemple suivant utilise le spécificateur de format personnalisé "ffff" pour afficher les dix millièmes de seconde dans une valeur <xref:System.TimeSpan>. "ffff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-fffff-custom-format-specifier"></a><a name="f5Specifier"></a> Spécificateur de format personnalisé "fffff"

Le spécificateur de format personnalisé "fffff" (cinq caractères « f ») affiche les cent millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement cinq chiffres fractionnaires.

L’exemple suivant utilise le spécificateur de format personnalisé "fffff" pour afficher les cent millièmes de seconde dans une valeur <xref:System.TimeSpan>. "fffff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-ffffff-custom-format-specifier"></a><a name="f6Specifier"></a> Spécificateur de format personnalisé "FFFFFF"

Le spécificateur de format personnalisé "ffffff" (six caractères « f ») affiche les millionièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement six chiffres fractionnaires.

L’exemple suivant utilise le spécificateur de format personnalisé "ffffff" pour afficher les millionièmes de seconde dans une valeur <xref:System.TimeSpan>. Il est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-fffffff-custom-format-specifier"></a><a name="f7Specifier"></a> Spécificateur de format personnalisé "fffffff"

Le spécificateur de format personnalisé "fffffff" (sept caractères « f ») affiche les dix millionièmes de seconde (ou le nombre fractionnaire de graduations) dans un intervalle de temps. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la chaîne d’entrée doit contenir exactement sept chiffres fractionnaires.

L’exemple suivant utilise le spécificateur de format personnalisé "fffffff" pour afficher le nombre fractionnaire de graduations dans une valeur <xref:System.TimeSpan>. Il est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Retour au tableau](#table)

## <a name="the-f-custom-format-specifier"></a><a name="F_Specifier"></a> Spécificateur de format personnalisé "F"

Le spécificateur de format personnalisé "F" affiche les dixièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Si la valeur des dixièmes de seconde de l’intervalle de temps est égale à zéro, elle n’est pas incluse dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence du chiffre des dixièmes de seconde est facultative.

Si le spécificateur de format personnalisé « F » est utilisé seul, spécifiez « %F » afin qu’il ne soit pas interprété à tort comme une chaîne de format standard.

L’exemple suivant utilise le spécificateur de format personnalisé "F" pour afficher les dixièmes de seconde dans une valeur <xref:System.TimeSpan>. Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Retour au tableau](#table)

## <a name="the-ff-custom-format-specifier"></a><a name="FF_Specifier"></a> Spécificateur de format personnalisé "FF"

Le spécificateur de format personnalisé "FF" affiche les centièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les éventuels zéros de fin fractionnaires ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence du chiffre des dixièmes et des centièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FF" pour afficher les centièmes de seconde dans une valeur <xref:System.TimeSpan>. Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Retour au tableau](#table)

## <a name="the-fff-custom-format-specifier"></a><a name="F3_Specifier"></a> Spécificateur de format personnalisé "FFF"

Le spécificateur de format personnalisé "FFF" (trois caractères « F ») affiche les millisecondes dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les éventuels zéros de fin fractionnaires ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence du chiffre des dixièmes, des centièmes et des millièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFF" pour afficher les millièmes de seconde dans une valeur <xref:System.TimeSpan>. Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Retour au tableau](#table)

## <a name="the-ffff-custom-format-specifier"></a><a name="F4_Specifier"></a> Spécificateur de format personnalisé "FFFF"

Le spécificateur de format personnalisé "FFFF" (quatre caractères « F ») affiche les dix millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les éventuels zéros de fin fractionnaires ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence du chiffre des dixièmes, des centièmes, des millièmes et des dix millièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFF" pour afficher les dix millièmes de seconde dans une valeur <xref:System.TimeSpan>. Il utilise également le spécificateur de format personnalisé "FFFF" dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Retour au tableau](#table)

## <a name="the-fffff-custom-format-specifier"></a><a name="F5_Specifier"></a> Spécificateur de format personnalisé "FFFFF"

Le spécificateur de format personnalisé "FFFFF" (cinq caractères « F ») affiche les cent millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les éventuels zéros de fin fractionnaires ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence du chiffre des dixièmes, des centièmes, des millièmes, des dix millièmes et des cent millièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFFF" pour afficher les cent millièmes de seconde dans une valeur <xref:System.TimeSpan>. Il utilise également le spécificateur de format personnalisé "FFFFF" dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Retour au tableau](#table)

## <a name="the-ffffff-custom-format-specifier"></a><a name="F6_Specifier"></a> Spécificateur de format personnalisé "FFFFFF"

Le spécificateur de format personnalisé "FFFFFF" (six caractères « F ») affiche les millionièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les éventuels zéros de fin fractionnaires ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence du chiffre des dixièmes, des centièmes, des millièmes, des dix millièmes, des cent millièmes et des millionièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFFFF" pour afficher les millionièmes de seconde dans une valeur <xref:System.TimeSpan>. Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Retour au tableau](#table)

## <a name="the-fffffff-custom-format-specifier"></a><a name="F7_Specifier"></a> Spécificateur de format personnalisé "FFFFFFF"

Le spécificateur de format personnalisé "FFFFFFF" (sept caractères « F ») affiche les dix millionièmes de seconde (ou le nombre fractionnaire de graduations) dans un intervalle de temps. Les éventuels zéros de fin fractionnaires ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ou <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, la présence des sept chiffres fractionnaires dans la chaîne d’entrée est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFFFFF" pour afficher les parties fractionnaires d’une seconde dans une valeur <xref:System.TimeSpan>. Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Retour au tableau](#table)

## <a name="other-characters"></a>Les autres caractères

Tout autre caractère sans séquence d’échappement dans une chaîne de format, y compris un espace blanc, est interprété comme un spécificateur de format personnalisé. Dans la plupart des cas, la présence de tout autre caractère sans séquence d’échappement aboutit à une <xref:System.FormatException>.

Vous pouvez inclure un caractère littéral dans une chaîne de format de deux façons :

- Mettez-le entre guillemets simples (délimiteur de chaîne littérale).

- Faites-le précéder d’une barre oblique inverse (« \\ »), qui est interprétée comme un caractère d’échappement. Cela signifie que, en C#, soit la chaîne de format doit être @-quoted, puis placée entre guillemets, soit le caractère littéral doit être précédé d’une barre oblique inverse supplémentaire.

  Dans certains cas, vous devrez peut-être utiliser une logique conditionnelle pour inclure un littéral avec séquence d’échappement dans une chaîne de format. L’exemple suivant utilise une logique conditionnelle pour inclure un symbole de signe pour les intervalles de temps négatifs.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET ne définit pas de grammaire pour les séparateurs des intervalles de temps. Cela signifie que les séparateurs entre les jours et les heures, entre les heures et les minutes, entre les minutes et les secondes et entre les secondes et les fractions de seconde doivent tous être traités comme des littéraux de caractère dans une chaîne de format.

L’exemple suivant utilise le caractère d’échappement et le guillemet simple pour définir une chaîne de format personnalisée qui inclut le mot « minutes » dans la chaîne de sortie.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Retour au tableau](#table)

## <a name="see-also"></a>Voir aussi

- [Mise en forme des types](formatting-types.md)
- [Chaînes de format TimeSpan standard](standard-timespan-format-strings.md)
