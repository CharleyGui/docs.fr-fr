---
title: Chaînes de format numériques standard
description: Dans cet article, Apprenez à utiliser des chaînes de format numériques standard pour mettre en forme des types numériques communs en représentations textuelles dans .NET.
ms.date: 06/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
ms.openlocfilehash: 605438a5f0e4b5bd9ade96c9db0416ee8611f311
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447119"
---
# <a name="standard-numeric-format-strings"></a>Chaînes de format numériques standard

Les chaînes de format numériques standard sont utilisées pour mettre en forme des types numériques courants. Une chaîne de format numérique standard se présente sous la forme `Axx`, où :

- `A` est un caractère alphabétique unique appelé *spécificateur de format*. Toute chaîne de format numérique contenant plusieurs caractères alphabétiques, y compris un espace blanc, est interprétée comme une chaîne de format numérique personnalisée. Pour plus d’informations, consultez [Chaînes de format numériques personnalisées](custom-numeric-format-strings.md).

- `xx` est un entier facultatif appelé *spécificateur de précision*. Le spécificateur de précision est compris entre 0 et 99 ; il affecte le nombre de chiffres dans le résultat. Notez que le spécificateur de précision contrôle le nombre de chiffres dans la représentation sous forme de chaîne d'un nombre. Il n'arrondit pas le nombre lui-même. Pour exécuter une opération d'arrondi, utilisez la méthode <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType> ou <xref:System.Math.Round%2A?displayProperty=nameWithType>.

  Quand le *spécificateur de précision* contrôle le nombre de chiffres fractionnaires dans la chaîne de résultat, celle-ci reflète un nombre qui est arrondi à un résultat représentable le plus proche du résultat précis à l’infini. S’il existe deux résultats représentables aussi proches l’un que l’autre :
  - **Sur le .NET Framework et .NET Core jusqu’à .NET Core 2.0**, le runtime sélectionne le résultat ayant le chiffre le moins significatif le plus élevé (autrement dit, à l’aide de <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).
  - **Sur .NET Core 2.1 et versions ultérieures**, le runtime sélectionne le résultat ayant un chiffre encore moins significatif (autrement dit, à l’aide de <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>).

  > [!NOTE]
  > Le spécificateur de précision détermine le nombre de chiffres dans la chaîne de résultat. Pour remplir une chaîne de résultat avec des espaces de début ou de fin, utilisez la fonctionnalité de [mise en forme composite](composite-formatting.md) et définissez un *composant d’alignement* dans l’élément de mise en forme.

Les chaînes de format numériques standard sont prises en charge par :

- Certaines surcharges de la méthode `ToString` de tous les types numériques. Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> et <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

- La [fonctionnalité de mise en forme composite](composite-formatting.md) .NET, utilisée par certaines méthodes `Write` et `WriteLine` des classes <xref:System.Console> et <xref:System.IO.StreamWriter>, la méthode <xref:System.String.Format%2A?displayProperty=nameWithType> et la méthode <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. La fonctionnalité de mise en forme composite vous permet d’inclure la représentation sous forme de chaîne de plusieurs éléments de données dans une même chaîne, de spécifier la largeur d’un champ et d’aligner les nombres dans un champ. Pour plus d’informations, consultez [Mise en forme composite](composite-formatting.md).

- Les [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md) en C# et Visual Basic, qui fournissent une syntaxe simplifiée par rapport aux de chaînes de format composite.

> [!TIP]
> Vous pouvez télécharger l’**utilitaire de mise en forme**, application .NET Core Windows Forms qui vous permet d’appliquer des chaînes de mise en forme à des valeurs numériques ou à des valeurs de date et d’heure, et d’afficher la chaîne de résultat. Le code source est disponible pour [C#](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs) et [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb).

<a name="table"></a>Le tableau suivant décrit les spécificateurs de format numériques standard et affiche un exemple de sortie produite par chaque spécificateur de format. Consultez la section [Remarques](#NotesStandardFormatting) pour plus d’informations sur l’utilisation de chaînes de format numériques standard, et la section [Exemple](#example) pour obtenir une illustration complète de leur utilisation.

|Spécificateur de format|Nom|Description|Exemples|
|----------------------|----------|-----------------|--------------|
|"C" ou "c"|Devise|Résultat : une valeur monétaire.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres décimaux.<br /><br /> Spécificateur de précision par défaut : défini par <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Informations supplémentaires : [Spécificateur de format monétaire ("C")](#CFormatString).|123,456 ("C", en-US)-> \\ $123,46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123,456 ("C3", en-US)-> ( \\ $123,456)<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|"D" ou "d"|Decimal|Résultat : chiffres entiers avec un signe négatif facultatif.<br /><br /> Pris en charge par : les types intégraux uniquement.<br /><br /> Spécificateur de précision : nombre minimal de chiffres.<br /><br /> Spécificateur de précision par défaut : nombre minimal de chiffres requis.<br /><br /> Informations supplémentaires : [Spécificateur de format décimal ("D")](#DFormatString).|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|
|"E" ou "e"|Exponentiel (scientifique)|Résultat : notation exponentielle.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres décimaux.<br /><br /> Spécificateur de précision par défaut : 6.<br /><br /> Informations supplémentaires : [Spécificateur de format exponentiel ("E")](#EFormatString).|1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1,05E+003|
|"F" ou "f"|Virgule fixe|Résultat : chiffres intégraux et décimaux avec un signe négatif facultatif.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres décimaux.<br /><br /> Spécificateur de précision par défaut : défini par <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Informations supplémentaires : [Spécificateur de format à virgule fixe ("F")](#FFormatString).|1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|
|"G" ou "g"|Général|Résultat : format le plus compact (notation à virgule fixe ou scientifique).<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres significatifs.<br /><br /> Spécificateur de précision par défaut : dépend du type numérique.<br /><br /> Informations supplémentaires : [Spécificateur de format standard ("G")](#GFormatString).|-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|
|"N" ou "n"|Nombre|Résultat : chiffres intégraux et décimaux, séparateurs de groupes et séparateur décimal avec un signe négatif facultatif.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre souhaité de décimales.<br /><br /> Spécificateur de précision par défaut : défini par <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Informations supplémentaires : [Spécificateur de format numérique ("N")](#NFormatString).|1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|
|"P" ou "p"|Pourcentage|Résultat : nombre multiplié par 100 et affiché avec un symbole de pourcentage.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre souhaité de décimales.<br /><br /> Spécificateur de précision par défaut : défini par <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Informations supplémentaires : [Spécificateur de format pourcentage ("P")](#PFormatString).|1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|
|"R" ou "r"|Aller-retour|Résultat : chaîne qui peut effectuer un aller-retour vers un nombre identique.<br /><br /> Pris en charge par : <xref:System.Single>, <xref:System.Double> et <xref:System.Numerics.BigInteger>.<br /><br /> Remarque : recommandé pour le type <xref:System.Numerics.BigInteger> uniquement. Pour les types <xref:System.Double>, utilisez "G17" ; pour les types <xref:System.Single>, utilisez "G9". <br> Spécificateur de précision : ignoré.<br /><br /> Informations supplémentaires : [Spécificateur de format aller-retour ("R")](#RFormatString).|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|
|"X" ou "x"|Valeur hexadécimale|Résultat : chaîne hexadécimale.<br /><br /> Pris en charge par : les types intégraux uniquement.<br /><br /> Spécificateur de précision : nombre de chiffres dans la chaîne de résultat.<br /><br /> Informations supplémentaires : [Spécificateur de format hexadécimal ("X")](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|
|N'importe quel caractère|Spécificateur inconnu|Résultat : lève un <xref:System.FormatException> au moment de l'exécution.||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Utilisation de chaînes de format numériques standard

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Une chaîne de format numérique standard peut être utilisée pour définir la mise en forme d'une valeur numérique de l'une des deux manières suivantes :

- Elle peut être passée à une surcharge de la méthode `ToString` qui a un paramètre `format`. L'exemple suivant met en forme une valeur numérique en tant que chaîne monétaire dans la culture actuelle (dans le cas présent, la culture en-US).

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- Elle peut être fournie comme argument `formatString` dans un élément de mise en forme utilisé avec des méthodes telles que <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> et <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [Mise en forme composite](composite-formatting.md). L'exemple suivant utilise un élément de mise en forme pour insérer une valeur monétaire dans une chaîne.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  Vous pouvez éventuellement fournir un argument `alignment` pour spécifier la largeur du champ numérique et si sa valeur est alignée à droite ou à gauche. L’exemple suivant aligne à gauche une valeur monétaire dans un champ de 28 caractères et aligne à droite une valeur monétaire dans un champ de 14 caractères.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Il peut être fourni en tant qu’argument `formatString` dans un élément d’expression interpolée d’une chaîne interpolée. Pour plus d’informations, consultez la rubrique [Interpolation de chaîne](../../csharp/language-reference/tokens/interpolated.md) dans les informations de référence sur C# ou la rubrique [Chaînes interpolées](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) dans les informations de référence sur Visual Basic.

Les sections suivantes fournissent des informations détaillées sur chacune des chaînes de format numériques standard.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Spécificateur de format monétaire ("C")

Le spécificateur de format "C" (ou monétaire) convertit un nombre en une chaîne qui représente un montant en devise. Le spécificateur de précision indique le nombre souhaité de décimales dans la chaîne de résultat. Si le spécificateur de précision est omis, la précision par défaut est définie par la propriété <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.

Si la valeur à mettre en forme contient un nombre de décimales supérieur au nombre spécifié ou au nombre par défaut, la valeur fractionnaire est arrondie dans la chaîne de résultat. Si la valeur à droite du nombre de décimales est égale à 5 ou supérieure, le dernier chiffre dans la chaîne de résultat est arrondi à une valeur différente de zéro.

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de <xref:System.Globalization.NumberFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Définit la position du symbole monétaire pour les valeurs positives.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Définit la position du symbole monétaire pour les valeurs négatives, et spécifie si le signe négatif est représenté par des parenthèses ou par la propriété <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit le signe négatif utilisé si <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> indique que les parenthèses ne sont pas utilisées.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Définit le symbole monétaire.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Définit le nombre par défaut de chiffres décimaux dans une valeur monétaire. Cette valeur peut être substituée à l'aide du spécificateur de précision.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Définit la chaîne qui sépare les groupes de nombres de la partie entière.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Définit le nombre de chiffres entiers qui s'affichent dans un groupe.|

L’exemple suivant met en forme une <xref:System.Double> valeur avec le spécificateur de format monétaire :

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Retour au tableau](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Spécificateur de format décimal ("D")

Le spécificateur de format "D" (ou décimal) convertit un nombre en une chaîne de chiffres décimaux (0-9), préfixée par un signe moins si le nombre est négatif. Ce format est pris en charge par les types intégraux uniquement.

Le spécificateur de précision indique le nombre minimal de chiffres voulu dans la chaîne résultante. Le cas échéant, des zéros sont ajoutés à la gauche du nombre afin de fournir le nombre de chiffres déterminé par le spécificateur de précision. Si aucun spécificateur de précision n'est spécifié, la valeur par défaut est la valeur minimale requise pour représenter l'entier sans zéros non significatifs.

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Comme le montre le tableau suivant, une seule propriété affecte la mise en forme de la chaîne de résultat.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif.|

L'exemple suivant met en forme une valeur <xref:System.Int32> avec le spécificateur de format décimal.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Retour au tableau](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Spécificateur de format exponentiel ("E")

Le spécificateur de format exponentiel ("E") convertit un nombre en une chaîne au format "-d.ddd…E+ddd" ou "-d.ddd…e+ddd", où chaque "d" correspond à un chiffre (0-9). La chaîne commence par un signe moins si le nombre est négatif. Un chiffre exactement précède toujours la virgule décimale.

Le spécificateur de précision indique le nombre de chiffres voulu après la virgule décimale. Si vous avez omis le spécificateur de précision, une précision par défaut de six chiffres après la virgule décimale est utilisée.

La casse du spécificateur de format indique si le préfixe "E" ou "e" doit être ajouté à l'exposant. L'exposant est toujours constitué d'un signe plus ou moins et d'un minimum de trois chiffres. Le cas échéant, des zéros sont ajoutés à l'exposant pour respecter ce minimum.

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de <xref:System.Globalization.NumberFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif à la fois pour le coefficient et pour l'exposant.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Définit la chaîne qui sépare le chiffre intégral des chiffres décimaux dans le coefficient.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Définit la chaîne qui indique qu'un exposant est positif.|

L’exemple suivant met en forme une <xref:System.Double> valeur avec le spécificateur de format exponentiel :

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Retour au tableau](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Spécificateur de format à virgule fixe ("F")

Le spécificateur de format à virgule fixe ("F") convertit un nombre en chaîne au format "-ddd.ddd…" où chaque "d" correspond à un chiffre (0-9). La chaîne commence par un signe moins si le nombre est négatif.

Le spécificateur de précision indique le nombre de décimales voulu. Si le spécificateur de précision est omis, la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> actuelle fournit la précision numérique.

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l'objet <xref:System.Globalization.NumberFormatInfo> qui peuvent contrôler la mise en forme de la chaîne de résultat.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Définit le nombre par défaut de chiffres décimaux. Cette valeur peut être substituée à l'aide du spécificateur de précision.|

L’exemple suivant met en forme une <xref:System.Double> valeur et une <xref:System.Int32> valeur avec le spécificateur de format à virgule fixe :

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Retour au tableau](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Spécificateur de format général ("G")

Le spécificateur de format général (« G ») convertit un nombre dans le format le plus compact (notation à virgule fixe ou notation scientifique), en fonction du type du nombre et de la présence d'un spécificateur de précision. Le spécificateur de précision définit le nombre maximal des chiffres significatifs qui peuvent s'afficher dans la chaîne de résultat. Si le spécificateur de précision est omis ou est égal à zéro, le type du nombre détermine la précision par défaut, comme indiqué dans le tableau suivant.

|Type numérique|Précision par défaut|
|------------------|-----------------------|
|<xref:System.Byte> ou <xref:System.SByte>|3 chiffres|
|<xref:System.Int16> ou <xref:System.UInt16>|5 chiffres|
|<xref:System.Int32> ou <xref:System.UInt32>|10 chiffres|
|<xref:System.Int64>|19 chiffres|
|<xref:System.UInt64>|20 chiffres|
|<xref:System.Numerics.BigInteger>|Illimité (identique à [« R »](#RFormatString))|
|<xref:System.Single>|7 chiffres|
|<xref:System.Double>|15 chiffres|
|<xref:System.Decimal>|29 chiffres|

La notation à virgule fixe est utilisée si l'exposant résultant de l'expression du nombre en notation scientifique est supérieur à -5 et inférieur au spécificateur de précision ; dans le cas contraire, la notation scientifique est utilisée. Le résultat contient un séparateur décimal si nécessaire et les zéros non significatifs situés après le séparateur décimal sont omis. Si le spécificateur de précision est présent et que le nombre de chiffres significatifs dans le résultat est supérieur à la précision indiquée, les chiffres de fin en trop sont supprimés par arrondi.

Toutefois, si le nombre est un <xref:System.Decimal> et que le spécificateur de précision est omis, la notation à virgule fixe est toujours utilisée et les zéros de fin sont conservés.

Si la notation scientifique est utilisée, l'exposant du résultat est précédé de "E" si le spécificateur de format est "G", ou de "e" si le spécificateur de format est "g". L'exposant contient au minimum deux chiffres. Cela diffère du format utilisé pour la notation scientifique produite par le spécificateur de format exponentiel, lequel inclut un minimum de trois chiffres dans l'exposant.

Notez que, lorsqu’il est utilisé avec une valeur <xref:System.Double>, le spécificateur de format "G17" garantit les allers-retours de la valeur <xref:System.Double> originale. En effet, <xref:System.Double> est un nombre à virgule flottante double précision (`binary64`) et conforme à la norme IEEE 754-2008, qui offre jusqu’à 17 chiffres de précision. Nous vous recommandons de l’utiliser à la place du [spécificateur de format "R"](#RFormatString) car, dans certains cas, "R" ne parvient pas à effectuer un aller-retour avec des valeurs à virgule flottante double précision. L'exemple suivant illustre cette situation.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

Lorsqu’il est utilisé avec une valeur <xref:System.Single>, le spécificateur de format "G9" garantit les allers-retours de la valeur <xref:System.Single> originale. En effet, <xref:System.Single> est un nombre à virgule flottante simple précision (`binary32`) et conforme à la norme IEEE 754-2008, qui offre jusqu’à neuf chiffres de précision. Pour des raisons de performances, nous vous recommandons de l’utiliser à la place du [spécificateur de format "R"](#RFormatString).

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de <xref:System.Globalization.NumberFormatInfo> qui contrôlent la mise en forme de la chaîne de résultat.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Définit la chaîne qui indique qu'un exposant est positif.|

L’exemple suivant met en forme les valeurs à virgule flottante assorties avec le spécificateur de format général :

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Retour au tableau](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Spécificateur de format numérique ("N")

Le spécificateur de format numérique ("N") convertit un nombre en une chaîne au format "-d,ddd,ddd.ddd…", où "-" correspond, le cas échéant, à un symbole de nombre négatif, "d" indique un chiffre (0-9), "," indique un séparateur de groupes et "." correspond à une virgule décimale. Le spécificateur de précision indique le nombre de chiffres voulu après la virgule décimale. Si le spécificateur de précision est omis, le nombre de décimales est défini par la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> actuelle.

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de <xref:System.Globalization.NumberFormatInfo> qui contrôlent la mise en forme de la chaîne de résultat.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Définit le format de valeurs négatives, et spécifie si le signe négatif est représenté par des parenthèses ou par la propriété <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Définit le nombre de chiffres intégraux qui s'affichent entre les séparateurs de groupes.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Définit la chaîne qui sépare les groupes de nombres de la partie entière.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Définit le nombre par défaut de chiffres décimaux. Cette valeur peut être substituée à l'aide d'un spécificateur de précision.|

L’exemple suivant met en forme les valeurs à virgule flottante assorties avec le spécificateur de format de nombre :

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Retour au tableau](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Spécificateur de format pourcentage ("P")

Le spécificateur de format pourcentage ("P") multiplie un nombre par 100 et le convertit en une chaîne qui représente un pourcentage. Le spécificateur de précision indique le nombre de décimales voulu. Si le spécificateur de précision est omis, la précision numérique par défaut fournie par la propriété <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> actuelle est utilisée.

Le tableau suivant répertorie les propriétés de <xref:System.Globalization.NumberFormatInfo> qui contrôlent la mise en forme de la chaîne retournée.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|Définit la position du symbole de pourcentage pour les valeurs positives.|
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|Définit la position du symbole de pourcentage et le symbole négatif pour les valeurs négatives.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif.|
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|Définit le symbole de pourcentage.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|Définit le nombre par défaut de chiffres décimaux dans une valeur de pourcentage. Cette valeur peut être substituée à l'aide du spécificateur de précision.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|Définit la chaîne qui sépare les groupes de nombres de la partie entière.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|Définit le nombre de chiffres entiers qui s'affichent dans un groupe.|

L’exemple suivant met en forme des valeurs à virgule flottante avec le spécificateur de format pourcentage :

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Retour au tableau](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Spécificateur de format aller-retour ("R")

Le spécificateur de format aller-retour ("R") tente de garantir qu'une valeur numérique qui est convertie en chaîne est de nouveau analysée en aboutissant à la même valeur numérique. Ce format est pris en charge uniquement pour les types <xref:System.Single>, <xref:System.Double> et <xref:System.Numerics.BigInteger>.

Pour les valeurs <xref:System.Double>, le spécificateur de format "R" ne parvient pas, dans certains cas, à effectuer un aller-retour de la valeur originale. Pour les valeurs <xref:System.Double> et <xref:System.Single>, il offre également des performances relativement faibles. Nous vous recommandons plutôt d’utiliser le spécificateur de format ["G17"](#GFormatString) pour les valeurs <xref:System.Double>, et le spécificateur de format ["G9"](#GFormatString) pour garantir l’aller-retour des valeurs <xref:System.Single>.

Lorsqu'une valeur <xref:System.Numerics.BigInteger> est mise en forme à l'aide de ce spécificateur, sa représentation sous forme de chaîne contient tous les chiffres significatifs dans la valeur <xref:System.Numerics.BigInteger>.

Bien que vous puissiez inclure un spécificateur de précision, il est ignoré. Les allers-retours prévalent sur la précision lorsque vous utilisez ce spécificateur.
Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de <xref:System.Globalization.NumberFormatInfo> qui contrôlent la mise en forme de la chaîne de résultat.

|Propriété de NumberFormatInfo|Description|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Définit la chaîne qui indique qu'un nombre est négatif.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Définit la chaîne qui indique qu'un exposant est positif.|

L'exemple suivant met en forme une valeur <xref:System.Numerics.BigInteger> avec le spécificateur de format aller-retour.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> Dans certains cas, les valeurs <xref:System.Double> mises en forme avec la chaîne de format numérique standard "R" ne font pas un aller-retour correct si elles sont compilées avec les commutateurs `/platform:x64` ou `/platform:anycpu`, et exécutées sur des systèmes 64 bits. Pour plus d'informations, consultez les paragraphes suivants :

Pour contourner le problème des valeurs <xref:System.Double> mises en forme avec la chaîne de format numérique standard « R » et pour lesquelles l'aller-retour ne fonctionne pas correctement dans le cas d'une compilation avec les indicateurs `/platform:x64` ou `/platform:anycpu` et d'une exécution sur des systèmes 64 bits, vous pouvez mettre en forme ces valeurs <xref:System.Double> en utilisant la chaîne de format numérique standard « G17 ». L’exemple suivant utilise la chaîne de format "R" avec une valeur qui ne parvient pas à effectuer un aller <xref:System.Double> -retour, et utilise également la chaîne de format "G17" pour effectuer un aller-retour correct de la valeur d’origine :

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Retour au tableau](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Spécificateur de format hexadécimal ("X")

Le spécificateur de format hexadécimal ("X") convertit un nombre en une chaîne de chiffres hexadécimaux. La casse du spécificateur de format indique s'il convient d'utiliser des caractères majuscules ou minuscules pour les chiffres hexadécimaux supérieurs à 9. Par exemple, utilisez "X" pour produire "ABCDEF" et "x" pour produire "abcdef". Ce format est pris en charge par les types intégraux uniquement.

Le spécificateur de précision indique le nombre minimal de chiffres voulu dans la chaîne résultante. Le cas échéant, des zéros sont ajoutés à la gauche du nombre afin de fournir le nombre de chiffres déterminé par le spécificateur de précision.

Les informations de mise en forme de l'objet <xref:System.Globalization.NumberFormatInfo> actif n'affectent pas la chaîne de résultat.

L'exemple suivant met en forme des valeurs <xref:System.Int32> avec le spécificateur de format hexadécimal.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Retour au tableau](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Notes

### <a name="control-panel-settings"></a>Paramètres du panneau de configuration

Les paramètres de l'élément **Options régionales et linguistiques** du Panneau de configuration influencent la chaîne résultante produite par une opération de mise en forme. Ces paramètres sont utilisés pour initialiser l'objet <xref:System.Globalization.NumberFormatInfo> associé à la culture du thread actuel, laquelle fournit les valeurs utilisées pour déterminer la mise en forme. Les ordinateurs qui utilisent des paramètres différents génèrent des chaînes de résultat différentes.

De plus, si le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> est utilisé pour instancier un nouvel objet <xref:System.Globalization.CultureInfo> qui représente la même culture que la culture système en cours, toutes les personnalisations établies par l’élément **Options régionales et linguistiques** dans le Panneau de configuration seront appliquées au nouvel objet <xref:System.Globalization.CultureInfo>. Vous pouvez utiliser le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> pour créer un objet <xref:System.Globalization.CultureInfo> qui ne reflète pas les personnalisations d'un système.

### <a name="numberformatinfo-properties"></a>Propriétés NumberFormatInfo

La mise en forme dépend des propriétés de l'objet <xref:System.Globalization.NumberFormatInfo> actuel, qui est fourni implicitement par la culture actuelle du thread ou explicitement par le paramètre <xref:System.IFormatProvider> de la méthode qui appelle la mise en forme. Spécifiez un objet <xref:System.Globalization.NumberFormatInfo> ou <xref:System.Globalization.CultureInfo> pour ce paramètre.

> [!NOTE]
> Pour plus d'informations sur la personnalisation des modèles ou des chaînes utilisés dans la mise en forme des valeurs numériques, consultez la rubrique de la classe <xref:System.Globalization.NumberFormatInfo>.

### <a name="integral-and-floating-point-numeric-types"></a>Types numériques intégraux et à virgule flottante

Certaines descriptions de spécificateurs de format numériques standard font référence à des types numériques intégraux ou à virgule flottante. Les types numériques intégraux sont <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64> et <xref:System.Numerics.BigInteger>. Les types numériques à virgule flottante sont <xref:System.Decimal>, <xref:System.Single> et <xref:System.Double>.

### <a name="floating-point-infinities-and-nan"></a>Infinis à virgule flottante et NaN

Quelle que soit la chaîne de format, si la valeur d'un type à virgule flottante <xref:System.Single> ou <xref:System.Double> est l'infini positif, l'infini négatif ou une valeur non numérique (NaN), la chaîne mise en forme est la valeur de la propriété <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A> ou <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> qui est spécifiée par l'objet <xref:System.Globalization.NumberFormatInfo> actuellement applicable.

## <a name="example"></a>Exemple

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

L'exemple suivant met en forme une valeur numérique intégrale et à virgule flottante en utilisant la culture en-US et tous les spécificateurs de format numériques standard. Cet exemple utilise deux types numériques particuliers (<xref:System.Double> et <xref:System.Int32>), mais produirait des résultats similaires pour n'importe lequel des autres types numériques de base (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal> et <xref:System.Single>).

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization.NumberFormatInfo>
- [Chaînes de format numériques personnalisées](custom-numeric-format-strings.md)
- [Mise en forme des types](formatting-types.md)
- [Procédure : remplir un nombre avec des zéros non significatifs](how-to-pad-a-number-with-leading-zeros.md)
- [Mise en forme composite](composite-formatting.md)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb)
