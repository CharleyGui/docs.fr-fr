---
title: Convertir des chaînes en DateTime
description: Découvrez les techniques permettant d’analyser des chaînes qui représentent des dates et des heures pour créer une valeur DateHeure à partir de la chaîne de date et d’heure.
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.openlocfilehash: f6ac4672a81db7047069f726f7eb1b920a82b3db
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889034"
---
# <a name="parse-date-and-time-strings-in-net"></a>Analyser les chaînes de date et d’heure dans .NET

Pour analyser des chaînes pour les convertir en objets <xref:System.DateTime>, vous devez spécifier des informations sur la façon dont les dates et heures sont représentées sous forme de texte. L’ordre du jour, du mois et de l’année est différent selon les cultures. Certaines représentations de l’heure utilisent une horloge de 24 heures, d’autres spécifient « AM » et « PM ». Certaines applications n’ont besoin que de la date. D’autres n’utilisent que l’heure. Et d’autres encore doivent spécifier la date et l’heure. Les méthodes qui convertissent des chaînes en objets <xref:System.DateTime> vous permettent de fournir des informations détaillées sur les formats souhaités et les éléments d’une date et d’une heure dont votre application a besoin. Il existe trois tâches subordonnées pour convertir correctement du texte en <xref:System.DateTime> :

1. Vous devez spécifier le texte qui représente une date et une heure au format attendu.
1. Vous pouvez spécifier la culture qui correspond au format de date et d’heure.
1. Vous pouvez spécifier la façon de définir les composants manquants d’une représentation de texte dans la date et l’heure.

Les méthodes <xref:System.DateTime.Parse%2A> et <xref:System.DateTime.TryParse%2A> convertissent de nombreuses représentations communes de date et d’heure. Les méthodes <xref:System.DateTime.ParseExact%2A> et <xref:System.DateTime.TryParseExact%2A> convertissent une représentation sous forme de chaîne conforme au modèle spécifié par une chaîne de format de date et d’heure. (Consultez les articles sur les [chaînes de format de date et d’heure standard](standard-date-and-time-format-strings.md) et les [chaînes de format de date et d’heure personnalisées](custom-date-and-time-format-strings.md) pour plus d’informations.)

L’objet courant <xref:System.Globalization.DateTimeFormatInfo> fournit davantage de contrôle sur la façon d’interpréter le texte comme une date et une heure. Les propriétés d’un <xref:System.Globalization.DateTimeFormatInfo> décrivent les séparateurs de date et d’heure et les noms de mois, de jours et de zones ainsi que le format des désignations « AM » et « PM ». La culture du thread en cours fournit un <xref:System.Globalization.DateTimeFormatInfo> qui représente la culture actuelle. Si vous souhaitez une culture spécifique ou des paramètres personnalisés, spécifiez le paramètre <xref:System.IFormatProvider> d’une méthode d’analyse. Pour le paramètre <xref:System.IFormatProvider>, vous devez spécifier un objet <xref:System.Globalization.CultureInfo> qui représente une culture, ou un objet <xref:System.Globalization.DateTimeFormatInfo>.

Certaines informations sur le texte représentant une date ou une heure peuvent être manquantes. Par exemple, pour la plupart des gens, la date « mars 12 » correspond à l’année en cours. De même que « mars 2018 » correspond au mois de mars de l’année 2018. Le texte représentant l’heure n’inclut souvent que les heures, les minutes et une désignation AM/PM.  Les méthodes d’analyse gèrent ces informations manquantes à l’aide de valeurs par défaut raisonnables :

- Lorsque seule l’heure est présente, la partie date utilise la date actuelle.
- Lorsque seule la date est présente, la partie heure correspond à minuit.
- Lors de l’année n’est pas spécifiée dans une date, l’année en cours est utilisée.
- Lorsque le jour du mois n’est pas spécifié, le premier jour du mois est utilisé.

Si la date est présente dans la chaîne, elle doit inclure le mois et le jour ou l’année. Si l’heure est présente, elle doit inclure l’heure et soit les minutes soit l’indicateur AM/PM.

Vous pouvez spécifier la constante <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> pour remplacer ces valeurs par défaut. Lorsque vous utilisez cette constante, toute propriété manquante de l’année, du mois ou du jour est définie sur la valeur `1`. Le [dernier exemple](#styles-example) qui utilise <xref:System.DateTime.Parse%2A> illustre ce comportement.

Outre le composant de date et d’heure, la représentation sous forme de chaîne d’une date et d’une heure peut inclure un offset qui indique le décalage horaire par rapport au temps universel coordonné (UTC, Coordinated Universal Time). Par exemple, la chaîne « 2/14/2007 5:32:00 -7:00 » définit une heure qui est sept heures plus tôt que l’heure UTC. Si la représentation d’une heure sous forme de chaîne n’inclut pas d’offset, l’analyse retourne un objet <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Si un offset est spécifié, l’analyse retourne un objet <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind.Local?displayProperty=nameWithType> et dont la valeur est ajustée en fonction du fuseau horaire local de votre ordinateur. Vous pouvez modifier ce comportement en utilisant une valeur <xref:System.Globalization.DateTimeStyles> avec la méthode d’analyse.

Le fournisseur de format est également utilisé pour interpréter une date numérique ambiguë. Il n’est pas évident de savoir quels composants de la date représentée par la chaîne « 02/03/04 » correspondent au mois, au jour et à l’année. Les composants sont interprétés d’après l’ordre des formats de date similaires dans le fournisseur de format.

## <a name="parse"></a>Analyser

L’exemple suivant illustre l’utilisation de la méthode <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> pour convertir une `string` en <xref:System.DateTime>. Cet exemple fait appel à la culture associée au thread actuel. Si l’objet <xref:System.Globalization.CultureInfo> associé à la culture actuelle ne peut pas analyser la chaîne d’entrée, une exception <xref:System.FormatException> est levée.

> [!TIP]
> Tous les exemples c# de cet article s’exécutent dans votre navigateur. Appuyez sur le bouton **Exécuter** pour afficher la sortie. Vous pouvez également les modifier pour vous entrainer.

> [!NOTE]
> Ces exemples sont disponibles dans GitHub docs référentiel pour [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/conversions) et [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/how-to/conversions).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Vous pouvez également définir explicitement la culture dont les conventions de mise en forme sont utilisées lorsque vous analysez une chaîne. Spécifiez l’un des objets standard <xref:System.Globalization.DateTimeFormatInfo> renvoyés par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. L’exemple suivant utilise un fournisseur de format pour analyser une chaîne en allemand dans <xref:System.DateTime>. Il crée une <xref:System.Globalization.CultureInfo> représentant la culture `de-DE`. Cet objet `CultureInfo` garantit la réussite de l’analyse de cette chaîne particulière. Ceci exclut tous les paramètres contenus dans <xref:System.Threading.Thread.CurrentCulture> de <xref:System.Threading.Thread.CurrentThread>.

[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Toutefois, bien que vous puissiez utiliser les surcharges de la méthode <xref:System.DateTime.Parse%2A> pour spécifier des fournisseurs de format personnalisé, la méthode ne prend pas en charge l’analyse de formats non standard. Pour analyser une date et une heure exprimées dans un format non standard, utilisez à la place la méthode <xref:System.DateTime.ParseExact%2A>.

<a name="styles-example"></a>L’exemple suivant utilise l’énumération <xref:System.Globalization.DateTimeStyles> pour spécifier que les informations de date et d’heure actuelles ne doivent pas être ajoutées à <xref:System.DateTime> pour les champs non spécifiés.

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>ParseExact

La méthode <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> convertit une chaîne en un objet <xref:System.DateTime> si elle est conforme à l’un des modèles de chaîne spécifiés. Quand une chaîne qui ne correspond pas aux formats spécifiés est transmise vers cette méthode, une <xref:System.FormatException> est levée. Vous pouvez spécifier un des spécificateurs de format standard de date et d’heure ou une combinaison de spécificateurs de format personnalisé de date et d’heure. En utilisant les spécificateurs de format personnalisé, vous pouvez construire une chaîne de reconnaissance personnalisée. Pour obtenir une explication des spécificateurs, consultez les rubriques relatives aux [chaînes de format de date et d’heure standard](standard-date-and-time-format-strings.md) et aux [chaînes de format de date et d’heure personnalisées](custom-date-and-time-format-strings.md).

Dans l’exemple suivant, la méthode <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> reçoit un objet de chaîne à analyser, suivi par un spécificateur de format, puis un objet <xref:System.Globalization.CultureInfo>. Cette méthode <xref:System.DateTime.ParseExact%2A> peut uniquement analyser des chaînes qui suivent le modèle de date longue dans la culture `en-US`.

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Chaque surcharge des méthodes <xref:System.DateTime.Parse%2A> et <xref:System.DateTime.ParseExact%2A> a un paramètre <xref:System.IFormatProvider> qui fournit des informations spécifiques à la culture sur la mise en forme de la chaîne. Cet objet <xref:System.IFormatProvider> est un objet <xref:System.Globalization.CultureInfo> qui représente une culture standard ou un objet <xref:System.Globalization.DateTimeFormatInfo> qui est renvoyé par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>.  <xref:System.DateTime.ParseExact%2A> utilise également une chaîne supplémentaire ou un argument de tableau de chaînes qui définit un ou plusieurs formats de date et d’heure.

## <a name="see-also"></a>Voir aussi

- [Analyser des chaînes](parsing-strings.md)
- [Mise en forme des types](formatting-types.md)
- [Conversion de types dans .NET](type-conversion.md)
- [Formats de date et d’heure standard](standard-date-and-time-format-strings.md)
- [Chaînes de format de date et d’heure personnalisées](custom-date-and-time-format-strings.md)
