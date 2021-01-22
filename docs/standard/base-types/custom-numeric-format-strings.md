---
title: Chaînes de format numériques personnalisées
description: Découvrez comment créer une chaîne de format numérique personnalisée pour mettre en forme des données numériques dans .NET. Une chaîne de format numérique personnalisée possède un ou plusieurs spécificateurs numériques personnalisés.
ms.date: 06/25/2018
ms.topic: reference
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET]
- formatting [.NET], numbers
- format strings
- custom numeric format strings
- numbers [.NET], formatting
- format specifiers, numeric
- formatting numbers [.NET]
- format specifiers, custom numeric format strings
ms.assetid: 6f74fd32-6c6b-48ed-8241-3c2b86dea5f4
ms.openlocfilehash: 52cdf8a28a43239d5c218b7154d67a1d0b3c210d
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693005"
---
# <a name="custom-numeric-format-strings"></a>Chaînes de format numériques personnalisées

Vous pouvez créer une chaîne de format numérique personnalisée, qui est composée d'un ou de plusieurs spécificateurs de format numériques personnalisés, pour définir la mise en forme des données numériques. Une chaîne de format numérique personnalisée est toute chaîne autre qu'une [chaîne de format numérique standard](standard-numeric-format-strings.md).

Les chaînes de format numérique personnalisées sont prises en charge par certaines surcharges de la méthode `ToString` de tous les types numériques. Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes <xref:System.Int32.ToString%28System.String%29> et <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> du type <xref:System.Int32> . Les chaînes de format numérique personnalisées sont également prises en charge par la fonctionnalité de [mise en forme composite](composite-formatting.md) .NET, utilisée par certaines méthodes `Write` et `WriteLine` des classes <xref:System.Console> et <xref:System.IO.StreamWriter>, la méthode <xref:System.String.Format%2A?displayProperty=nameWithType> et la méthode <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. La fonctionnalité [Interpolation de chaîne](../../csharp/language-reference/tokens/interpolated.md) prend également en charge les chaînes de format numérique personnalisées.

> [!TIP]
> Vous pouvez télécharger l’**utilitaire de mise en forme**, application .NET Core Windows Forms qui vous permet d’appliquer des chaînes de mise en forme à des valeurs numériques ou à des valeurs de date et d’heure, et d’afficher la chaîne de résultat. Le code source est disponible pour [C#](/samples/dotnet/samples/windowsforms-formatting-utility-cs) et [Visual Basic](/samples/dotnet/samples/windowsforms-formatting-utility-vb).

<a name="table"></a> Le tableau suivant décrit les spécificateurs de format numériques personnalisés et affiche un exemple de sortie produite par chaque spécificateur de format. Consultez la section [Remarques](#NotesCustomFormatting) pour plus d'informations sur l'utilisation de chaînes de format numériques personnalisées, et la section [Exemple](#example) pour obtenir une illustration complète de leur utilisation.

|Spécificateur de format|Nom|Description|Exemples|
|----------------------|----------|-----------------|--------------|
|"0"|Espace réservé du zéro|Remplace le zéro par le chiffre correspondant, le cas échéant ; sinon, le zéro s'affiche dans la chaîne de résultat.<br /><br /> Informations supplémentaires : [Spécificateur personnalisé « 0 »](#Specifier0).|1234.5678 ("00000") -> 01235<br /><br /> 0.45678 ("0.00", en-US) -> 0.46<br /><br /> 0.45678 ("0.00", fr-FR) -> 0,46|
|"#"|Espace réservé de chiffre|Remplace le symbole « # » par le chiffre correspondant, le cas échéant ; sinon, aucun chiffre ne s'affiche dans la chaîne de résultat.<br /><br /> Notez qu’aucun chiffre n’apparaît dans la chaîne de résultat si le chiffre correspondant dans la chaîne d’entrée est un 0 non significatif. Exemple : 0003 ("####") -> 3.<br /><br /> Informations supplémentaires : [Spécificateur personnalisé « # »](#SpecifierD).|1234.5678 ("#####") -> 1235<br /><br /> 0.45678 ("#.##", en-US) -> .46<br /><br /> 0.45678 ("#.##", fr-FR) -> ,46|
|"."|Virgule décimale|Détermine l'emplacement du séparateur décimal dans la chaîne de résultat.<br /><br /> Informations supplémentaires : [« . » Spécificateur personnalisé](#SpecifierPt).|0.45678 ("0.00", en-US) -> 0.46<br /><br /> 0.45678 ("0.00", fr-FR) -> 0,46|
|","|Séparateur de groupes et mise à l'échelle des nombres|Sert à la fois de séparateur de groupes et de spécificateur de mise à l'échelle des nombres. En tant que séparateur de groupes, il insère un caractère de séparation des groupes localisé entre chaque groupe. En tant que spécificateur de mise à l'échelle des nombres, il divise un nombre par 1000 pour chaque virgule spécifiée.<br /><br /> Informations supplémentaires : [spécificateur personnalisé « , »](#SpecifierTh).|Spécificateur de séparateur de groupes :<br /><br /> 2147483647 ("##,#", en-US) -> 2,147,483,647<br /><br /> 2147483647 ("##,#", es-ES) -> 2.147.483.647<br /><br /> Spécificateur de mise à l'échelle :<br /><br /> 2147483647 ("#,#,,", en-US) -> 2,147<br /><br /> 2147483647 ("#,#,,", es-ES) -> 2.147|
|"%"|Espace réservé de pourcentage|Multiplie un nombre par 100 et insère un symbole de pourcentage localisé dans la chaîne de résultat.<br /><br /> Informations supplémentaires : [spécificateur personnalisé "%"](#SpecifierPct).|0.3697 ("%#0.00", en-US) -> %36.97<br /><br /> 0.3697 ("%#0.00", el-GR) -> %36,97<br /><br /> 0.3697 ("##.0 %", en-US) -> 37.0 %<br /><br /> 0.3697 ("##.0 %", el-GR) -> 37,0 %|
|"‰"|Espace réservé « pour mille »|Multiplie un nombre par 1000 et insère un symbole « pour mille » localisé dans la chaîne de résultat.<br /><br /> Informations supplémentaires : [spécificateur personnalisé "‰"](#SpecifierPerMille).|0.03697 ("#0.00‰", en-US) -> 36.97‰<br /><br /> 0.03697 ("#0.00‰", ru-RU) -> 36,97‰|
|"E0"<br /><br /> "E+0"<br /><br /> "E-0"<br /><br /> "E0"<br /><br /> "E+0"<br /><br /> "E-0"|Notation exponentielle|Si le spécificateur est suivi d'au moins un zéro (0), met en forme le résultat à l'aide de la notation exponentielle. La casse de « E » ou « e » indique la casse du symbole d'exposant dans la chaîne de résultat. Le nombre des zéros qui suivent le caractère « E » ou « e » détermine le nombre minimal de chiffres dans l'exposant. Un signe plus (+) indique qu'un caractère de signe précède toujours l'exposant. Un signe moins (-) indique qu'un caractère de signe précède uniquement les exposants négatifs.<br /><br /> Informations supplémentaires : [Spécificateurs personnalisés « E » et « e »](#SpecifierExponent).|987654 ("#0.0e0") -> 98.8e4<br /><br /> 1503.92311 ("0.0##e+00") -> 1.504e+03<br /><br /> 1.8901385E-16 ("0.0e+00") -> 1.9e-16|
|"\\"|Caractère d’échappement|Entraîne l'interprétation du caractère suivant comme un littéral plutôt que comme un spécificateur de format personnalisé.<br /><br /> Informations supplémentaires : [Caractère d'échappement « \\ »](#SpecifierEscape).|987654 ("\\###00\\#") -> #987654#|
|'*chaîne*'<br /><br /> «*chaîne*»|Délimiteur de chaîne littérale|Indique que les caractères encadrés doivent être copiés inchangés dans la chaîne de résultat.<br/><br/>Plus d’informations : [Littéraux de caractère](#character-literals).|68 ("# 'degrees'") -> 68 degrees<br /><br /> 68 ("#' degrees'") -> 68 degrees|
|;|Séparateur de section|Définit des sections avec des chaînes de format distinctes pour les nombres positifs, négatifs et nuls.<br /><br /> Informations supplémentaires : [Séparateur de section « ; »](#SectionSeparator).|12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#);-\0-") -> -0-<br /><br /> -12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)<br /><br /> 12.345 ("#0.0#;(#0.0#)") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#)") -> 0.0<br /><br /> -12.345 ("#0.0#;(#0.0#)") -> (12.35)|
|Autre|Tous les autres caractères|Le caractère est copié inchangé dans la chaîne de résultat.<br/><br/>Plus d’informations : [Littéraux de caractère](#character-literals).|68 ("# °") -> 68 °|

Les sections suivantes fournissent des informations détaillées sur chacun des spécificateurs de format numériques personnalisés.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-partial-note.md)]

<a name="Specifier0"></a>

## <a name="the-0-custom-specifier"></a>Spécificateur personnalisé « 0 »

Le spécificateur de format personnalisé "0" sert de symbole d'espace réservé du zéro. Si la valeur qui est mise en forme comprend un chiffre à l'emplacement le zéro apparaît dans la chaîne de format, ce chiffre est copié dans la chaîne de résultant ; sinon, un zéro apparaît dans la chaîne de résultat. L'emplacement du zéro situé à l'extrême gauche avant le séparateur décimal et du zéro situé à l'extrême droite après le séparateur décimal détermine la plage des chiffres qui sont toujours présents dans la chaîne de résultat.

Le spécificateur « 00 » provoque l'arrondissement de la valeur au chiffre le plus proche précédant la virgule ; l'arrondissement à une valeur différente de zéro est toujours utilisé. Par exemple, la mise en forme de 34,5 avec « 00 » produit la valeur 35.

L'exemple suivant affiche plusieurs valeurs qui sont mises en forme à l'aide de chaînes de format personnalisées incluant des espaces réservés du zéro.

[!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
[!code-csharp[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
[!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]

[Retour au tableau](#table)

<a name="SpecifierD"></a>

## <a name="the--custom-specifier"></a>Spécificateur personnalisé « # »

Le spécificateur de format personnalisé "#" sert de symbole d'espace réservé des chiffres. Si la valeur qui est mise en forme comprend un chiffre à l'emplacement où le symbole « # » apparaît dans la chaîne de format, ce chiffre est copié dans la chaîne de résultat. Sinon, rien n'est stocké à cet emplacement dans la chaîne résultante.

Notez que ce spécificateur n'affiche jamais un zéro qui n'est pas un chiffre significatif, même si le zéro est le seul chiffre de la chaîne. Il affichera zéro uniquement s'il s'agit d'un chiffre significatif dans le nombre affiché.

La chaîne de format « ## » provoque l'arrondissement de la valeur au chiffre le plus proche précédant la virgule ; l'arrondissement à une valeur différente de zéro est toujours utilisé. Par exemple, la mise en forme de 34,5 avec « ## » produit la valeur 35.

L'exemple suivant affiche plusieurs valeurs qui sont mises en forme à l'aide de chaînes de format personnalisées incluant des espaces réservés de chiffres.

[!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
[!code-csharp[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
[!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]

Pour retourner une chaîne de résultat dans laquelle les chiffres absents ou les zéros non significatifs sont remplacés par des espaces, utilisez la [fonctionnalité de mise en forme composite](composite-formatting.md) et spécifiez une largeur de champ, comme l’illustre l’exemple suivant.

[!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
[!code-csharp[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
[!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]

[Retour au tableau](#table)

<a name="SpecifierPt"></a>

## <a name="the--custom-specifier"></a>Spécificateur personnalisé « . »

Le spécificateur de format personnalisé "." insère un séparateur décimal localisé dans la chaîne de résultat. Le premier point de la chaîne de format détermine l'emplacement du séparateur décimal dans la valeur mise en forme. Tout autre point est ignoré.

Le caractère qui est utilisé comme séparateur décimal dans la chaîne de résultat n'est pas toujours un point ; il est déterminé par la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> de l'objet <xref:System.Globalization.NumberFormatInfo> qui contrôle la mise en forme.

L'exemple suivant utilise le spécificateur de format "." pour définir l'emplacement de la virgule décimale dans plusieurs chaînes de résultat.

[!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
[!code-csharp[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
[!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]

[Retour au tableau](#table)

<a name="SpecifierTh"></a>

## <a name="the--custom-specifier"></a>Spécificateur personnalisé « , »

Le caractère "," sert à la fois de séparateur de groupes et de spécificateur de mise à l'échelle des nombres.

- Séparateur de groupes : si une ou plusieurs virgules sont spécifiées entre deux espaces réservés de chiffres (0 ou #) qui mettent en forme les chiffres intégraux d'un nombre, un caractère de séparation des groupes est inséré entre chaque groupe de nombres dans la partie intégrale de la sortie.

  Les propriétés <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> et <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> de l'objet <xref:System.Globalization.NumberFormatInfo> en cours déterminent le caractère utilisé comme séparateur de groupes de nombres et la taille de chaque groupe de nombres. Par exemple, si la chaîne « #,# » et la culture indifférente sont utilisées pour mettre en forme le nombre 1000, la sortie est « 1,000 ».

- Spécificateur de mise à l'échelle des nombres : si une ou plusieurs virgules sont spécifiées immédiatement à gauche du séparateur décimal explicite ou implicite, le nombre à mettre en forme est divisé par 1000 pour chaque virgule. Par exemple, si la chaîne « 0,, » est utilisée pour mettre en forme le nombre 100 millions, la sortie est « 100 ».

Vous pouvez utiliser des spécificateurs de séparateur de groupes et de mise à l'échelle des nombres dans la même chaîne de format. Par exemple, si la chaîne « #,0,, » et la culture indifférente sont utilisées pour mettre en forme le nombre 1 milliard, la sortie est « 1,000 ».

L'exemple suivant illustre l'utilisation de la virgule comme séparateur de groupes.

[!code-cpp[Formatting.Numeric.Custom#4](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#4)]
[!code-csharp[Formatting.Numeric.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#4)]
[!code-vb[Formatting.Numeric.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#4)]

L'exemple suivant illustre l'utilisation de la virgule comme spécificateur pour la mise à l'échelle des nombres.

[!code-cpp[Formatting.Numeric.Custom#5](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#5)]
[!code-csharp[Formatting.Numeric.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#5)]
[!code-vb[Formatting.Numeric.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#5)]

[Retour au tableau](#table)

<a name="SpecifierPct"></a>

## <a name="the--custom-specifier"></a>Spécificateur personnalisé « % »

Un signe de pourcentage (%) dans une chaîne de format entraîne la multiplication d'un nombre par 100 avant sa mise en forme. Le symbole de pourcentage localisé est inséré dans le nombre à l'emplacement où le caractère % apparaît dans la chaîne de format. Le caractère de pourcentage utilisé est défini par la propriété <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> de l'objet <xref:System.Globalization.NumberFormatInfo> actif.

L'exemple suivant définit plusieurs chaînes de format personnalisées qui incluent le spécificateur personnalisé "%".

[!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
[!code-csharp[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
[!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]

[Retour au tableau](#table)

<a name="SpecifierPerMille"></a>

## <a name="the--custom-specifier"></a>Spécificateur personnalisé « ‰ »

Un caractère « pour mille » (‰ ou \u2030) dans une chaîne de format entraîne la multiplication d'un nombre par 1 000 avant sa mise en forme. Le symbole « pour mille » approprié est inséré dans la chaîne retournée, à l'emplacement où le symbole ‰ apparaît dans la chaîne de format. Le caractère « pour mille » utilisé est défini par la propriété <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> de l'objet qui fournit les informations de mise en forme spécifique à la culture.

L'exemple suivant définit une chaîne de format personnalisée qui inclut le spécificateur personnalisé "‰".

[!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
[!code-csharp[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
[!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]

[Retour au tableau](#table)

<a name="SpecifierExponent"></a>

## <a name="the-e-and-e-custom-specifiers"></a>Spécificateurs personnalisés « E » et « e »

Si l'une des chaînes "E", "E+", "E-", "e", "e+" ou "e-" est présente dans la chaîne de format et immédiatement suivie d'au moins un zéro, le nombre est mis en forme à l'aide de la notation scientifique, avec un "E" ou un "e" inséré entre le nombre et l'exposant. Le nombre de zéros qui suivent l'indicateur de notation scientifique détermine le nombre minimal de chiffres à afficher pour l'exposant. Les formats "E+" et "e+" indiquent qu'un signe plus ou un signe moins doit toujours précéder l'exposant. Les formats "E", "E-", "e" ou "e-" indiquent qu'un signe ne doit précéder que les exposants négatifs.

L'exemple suivant met en forme plusieurs valeurs numériques à l'aide des spécificateurs pour la notation scientifique.

[!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
[!code-csharp[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
[!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]

[Retour au tableau](#table)

<a name="SpecifierEscape"></a>

## <a name="the--escape-character"></a>Caractère d’échappement « \\ »

Les symboles "#", "0", ".", ",", "%" et "‰" dans une chaîne de format sont interprétés comme des spécificateurs de format plutôt que comme des caractères littéraux. En fonction de leur position dans une chaîne de format personnalisée, les "E" majuscules et minuscules ainsi que les symboles + et - peuvent également être interprétés comme des spécificateurs de format.

Pour éviter qu'un caractère soit interprété comme un spécificateur de format, vous pouvez le faire précéder d'une barre oblique inverse, qui est le caractère d'échappement. Le caractère d'échappement signifie que le caractère suivant est un caractère littéral qui doit être inclus inchangé dans la chaîne de résultat.

Pour inclure une barre oblique inverse dans une chaîne de résultat, vous devez la placer dans une séquence d'échappement avec une autre barre oblique inverse (`\\`).

> [!NOTE]
> Certains compilateurs, tels que les compilateurs C++ et C#, peuvent également interpréter une barre oblique inverse unique comme un caractère d'échappement. Pour garantir l'interprétation correcte d'une chaîne lors de la mise en forme, vous pouvez utiliser le caractère littéral de chaîne textuel(le caractère @) avant la chaîne en C#, ou ajouter une autre barre oblique inverse avant chaque barre oblique inverse en C# et C++. L'exemple C# suivant illustre ces deux approches.

L’exemple suivant utilise le caractère d’échappement pour empêcher l’opération de mise en forme d’interpréter les caractères « # », « 0 » et « \\ » comme des caractères d’échappement ou des spécificateurs de format. L'exemple C# utilise une barre oblique inverse supplémentaire pour garantir qu'une barre oblique inverse est interprétée comme un caractère littéral.

[!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
[!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
[!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]

[Retour au tableau](#table)

<a name="SectionSeparator"></a>

## <a name="the--section-separator"></a>Séparateur de section « ; »

Le point-virgule (;) est un spécificateur de format conditionnel qui applique une mise en forme différente à un nombre suivant que sa valeur est positive, négative ou nulle. Pour entraîner ce comportement, une chaîne de format personnalisée peut contenir jusqu'à trois sections séparées par des points-virgules. Ces sections sont décrites dans le tableau suivant.

|Nombre de sections|Description|
|------------------------|-----------------|
|Une section|La chaîne de format s'applique à toutes les valeurs.|
|Deux sections|La première section s'applique aux valeurs positives et aux zéros, et la deuxième section s'applique aux valeurs négatives.<br /><br /> Si le nombre à mettre en forme est négatif, mais devient nul après l'arrondissement au format de la deuxième section, le zéro résultant est mis en forme en fonction de la première section.|
|Trois sections|La première section s'applique aux valeurs positives, la deuxième section s'applique aux valeurs négatives et la troisième section s'applique aux zéros.<br /><br /> La deuxième section peut rester vide (en n'insérant aucune valeur entre les points-virgules), auquel cas la première section s'applique à toutes les valeurs différentes de zéro.<br /><br /> Si le nombre à mettre en forme est différent de zéro, mais devient nul après l'arrondissement au format de la première ou deuxième section, le zéro résultant est mis en forme en fonction de la troisième section.|

Les séparateurs de section ignorent toute mise en forme préexistante associée à un nombre lorsque la valeur finale est mise en forme. Par exemple, les valeurs négatives sont toujours affichées sans signe moins lorsque des séparateurs de section sont utilisés. Si vous souhaitez que la valeur mise en forme finale soit précédée d'un signe moins, vous devez inclure ce signe explicitement comme élément du spécificateur de format personnalisé.

L'exemple suivant utilise le spécificateur de format ";" pour mettre en forme différemment les nombres positifs, négatifs et nuls.

[!code-cpp[Formatting.Numeric.Custom#8](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#8)]
[!code-csharp-interactive[Formatting.Numeric.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#8)]
[!code-vb[Formatting.Numeric.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#8)]

[Retour au tableau](#table)

## <a name="character-literals"></a>Littéraux de caractère

Les spécificateurs de format qui apparaissent dans une chaîne de format numérique personnalisée sont toujours interprétés comme des caractères de mise en forme, jamais comme des caractères littéraux. Il s’agit notamment des caractères suivants :

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [,](#SpecifierTh)
- [E ou e](#SpecifierExponent), en fonction de sa position dans la chaîne de format.

Tous les autres caractères sont toujours interprétés comme des caractères littéraux et, dans une opération de mise en forme, sont inclus inchangés dans la chaîne de résultat.  Dans une opération d’analyse, ils doivent correspondre exactement aux caractères présents dans la chaîne d’entrée. La comparaison respecte la casse.

L’exemple suivant illustre un usage courant des unités de caractères littéraux (dans ce cas, les milliers) :

[!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
[!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]

Il existe deux façons d’indiquer que les caractères doivent être interprétés comme des caractères littéraux, et non comme des caractères de mise en forme, pour qu’ils puissent être inclus dans une chaîne de résultat ou analysés correctement dans une chaîne d’entrée :

- En échappant un caractère de mise en forme. Pour plus d’informations, consultez [Caractère d’échappement « \\ »](#SpecifierEscape).

- En plaçant la totalité de la chaîne littérale entre apostrophes.

L’exemple suivant utilise les deux approches pour inclure des caractères réservés dans une chaîne de format numérique personnalisée.

[!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal1.cs#1)]
[!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal1.vb#1)]

<a name="NotesCustomFormatting"></a>

## <a name="notes"></a>Remarques

### <a name="floating-point-infinities-and-nan"></a>Infinis à virgule flottante et NaN

Quelle que soit la chaîne de format, si la valeur d'un type à virgule flottante <xref:System.Single> ou <xref:System.Double> est l'infini positif, l'infini négatif ou une valeur non numérique (NaN), la chaîne mise en forme est la valeur de la propriété <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>ou <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> spécifiée par l'objet <xref:System.Globalization.NumberFormatInfo> actuellement applicable.

### <a name="control-panel-settings"></a>Paramètres du panneau de configuration

Les paramètres de l'élément **Options régionales et linguistiques** du Panneau de configuration influencent la chaîne résultante produite par une opération de mise en forme. Ces paramètres sont utilisés pour initialiser l'objet <xref:System.Globalization.NumberFormatInfo> associé à la culture du thread en cours et la culture du thread en cours fournit des valeurs utilisées pour indiquer la mise en forme. Les ordinateurs qui utilisent des paramètres différents génèrent des chaînes de résultat différentes.

De plus, si vous utilisez le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> pour instancier un nouvel objet <xref:System.Globalization.CultureInfo> qui représente la même culture que la culture système en cours, toutes les personnalisations établies par l'élément **Options régionales et linguistiques** du Panneau de configuration seront appliquées au nouvel objet <xref:System.Globalization.CultureInfo> . Vous pouvez utiliser le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> pour créer un objet <xref:System.Globalization.CultureInfo> qui ne reflète pas les personnalisations d'un système.

### <a name="rounding-and-fixed-point-format-strings"></a>Arrondi et chaînes de format à virgule fixe

Pour les chaînes de format à virgule fixe (c'est-à-dire les chaînes de format ne contenant pas de caractères de format de notation scientifique), les nombres sont arrondis au même nombre de décimales que d'espaces réservés de chiffres à droite du séparateur décimal. Si la chaîne de format ne contient pas de virgule décimale, le nombre est arrondi à l'entier le plus proche. Si le nombre possède plus de chiffres que d'espaces réservés de chiffres à gauche de la virgule décimale, les chiffres supplémentaires sont copiés dans la chaîne résultante immédiatement avant le premier espace réservé de chiffre.

[Retour au tableau](#table)

<a name="example"></a>

## <a name="example"></a>Exemple

L'exemple suivant présente deux chaînes de format numériques personnalisées. Dans les deux cas, l'espace réservé de chiffre (`#`) affiche les données numériques, et tous les autres caractères sont copiés dans la chaîne de résultat.

[!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
[!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
[!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]

[Retour au tableau](#table)

## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>
- [Mise en forme des types](formatting-types.md)
- [Chaînes de format numériques standard](standard-numeric-format-strings.md)
- [Comment : remplir un nombre avec des zéros non significatifs](how-to-pad-a-number-with-leading-zeros.md)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (C#)](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (Visual Basic)](/samples/dotnet/samples/windowsforms-formatting-utility-vb)
