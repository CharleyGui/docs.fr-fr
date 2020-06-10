---
title: Options des expressions régulières
description: Découvrez comment utiliser les options des expressions régulières dans .NET, telles que la correspondance non sensible à la casse, le mode multiligne et le mode de droite à gauche.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, options
- constructs, options
- .NET Framework regular expressions, options
- inline option constructs
- options parameter
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
ms.openlocfilehash: 268e05c2212539b030ccc3c7195f618bb3afa707
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662873"
---
# <a name="regular-expression-options"></a>Options des expressions régulières

Par défaut, la comparaison d’une chaîne d’entrée avec des caractères littéraux dans un modèle d’expression régulière respecte la casse, l’espace blanc dans un modèle d’expression régulière est interprété comme un espace blanc littéral et les groupes de capture dans une expression régulière sont nommés de manière implicite aussi bien qu’explicite. Vous pouvez modifier ces aspects, ainsi que d'autres, du comportement par défaut des expressions régulières en spécifiant des options d'expression régulière. Ces options, qui sont répertoriées dans le tableau suivant, peuvent être incluses inline dans le cadre du modèle d’expression régulière ou fournies à un constructeur de classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> ou à une méthode de mise en correspondance de modèle statique en tant que valeur d’énumération <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.

|Membre RegexOptions|Caractère inline|Effet|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Non disponible|Utilise le comportement par défaut. Pour plus d’informations, consultez [Options par défaut](#default-options).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Utilise la correspondance qui ne respecte pas la casse. Pour plus d’informations, consultez [Correspondance qui ne respecte pas la casse](#case-insensitive-matching).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Utilise le mode multiligne, où `^` et `$` correspondent au début et à la fin de chaque ligne (plutôt qu'au début et à la fin de la chaîne d'entrée). Pour plus d’informations, consultez [Mode multiligne](#multiline-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Utilise le mode à ligne simple, où le point (.) correspond à chaque caractère (y compris `\n`). Pour plus d’informations, consultez [mode à ligne simple](#single-line-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Ne capture aucun groupe sans nom. Les seules captures valides sont les groupes explicitement nommés ou numérotés de la forme `(?<`*nom*`>` *sous-expression*`)`. Pour plus d’informations, consultez [Captures explicites uniquement](#explicit-captures-only).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Non disponible|Compile l'expression régulière en un assembly. Pour plus d’informations, consultez [Expressions régulières compilées](#compiled-regular-expressions).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Exclure du modèle l'espace blanc sans séquence d'échappement et autoriser les commentaires après un signe dièse (`#`). Pour plus d’informations, consultez [Ignorer l’espace blanc](#ignore-white-space).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Non disponible|Modifie le sens de la recherche. La recherche s'effectue de droite à gauche au lieu de gauche à droite. Pour plus d’informations, consultez [Mode de recherche de droite à gauche](#right-to-left-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Non disponible|Active le comportement compatible ECMAScript pour l’expression. Pour plus d’informations, consultez [Comportement de correspondance ECMAScript](#ecmascript-matching-behavior).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Non disponible|Ignorer les différences culturelles propres à la langue. Pour plus d’informations, consultez [Comparaison utilisant la culture dite indifférente](#comparison-using-the-invariant-culture).|

## <a name="specifying-the-options"></a>Spécification des options

Vous pouvez spécifier les options des expressions régulières de trois façons :

- Dans le paramètre `options` d’un constructeur de classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> ou d’une méthode de mise en correspondance de modèle statique (`Shared` en Visual Basic), comme <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29> ou <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. Le paramètre `options` est une combinaison OR au niveau du bit de valeurs énumérées <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.

  Quand des options sont fournies à une instance de <xref:System.Text.RegularExpressions.Regex> à l'aide du paramètre `options` d'un constructeur de classe, les options sont affectées à la propriété <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>. Cependant, la propriété <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> ne reflète pas les options inline dans le modèle d'expression régulière lui-même.

  L'exemple suivant en est l'illustration. Il utilise le paramètre `options` de la méthode <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> pour autoriser la correspondance qui ne respecte pas la casse et pour ignorer l’espace blanc du modèle pendant l’identification des mots commençant par la lettre « d ».

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- En appliquant des options inline dans un modèle d'expression régulière avec la syntaxe `(?imnsx-imnsx)`. L’option s’applique au modèle depuis le point où elle est définie jusqu’à la fin du modèle ou jusqu’au point auquel sa définition est annulée par une autre option inline. Notez que la propriété <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> d'une instance de <xref:System.Text.RegularExpressions.Regex> ne reflète pas ces options inline. Pour plus d’informations, consultez la rubrique [Constructions diverses](miscellaneous-constructs-in-regular-expressions.md).

  L'exemple suivant en est l'illustration. Il utilise des options inline pour autoriser la correspondance qui ne respecte pas la casse et pour ignorer l’espace blanc du modèle pendant l’identification des mots commençant par la lettre « d ».

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- En appliquant des options inline dans une construction de regroupement particulière dans un modèle d’expression régulière avec la syntaxe sous- `(?imnsx-imnsx:` *expression* `)` . L'absence de signe avant un jeu d'options active ce dernier, tandis qu'un signe moins le désactive. ( `?` est une partie fixe de la syntaxe de la construction de langage qui est obligatoire, que les options soient activées ou désactivées.) L’option s’applique uniquement à ce groupe. Pour plus d’informations, consultez [Constructions de regroupement](grouping-constructs-in-regular-expressions.md).

  L'exemple suivant en est l'illustration. Il utilise des options inline dans une construction de regroupement pour autoriser la correspondance qui ne respecte pas la casse et pour ignorer l’espace blanc du modèle pendant l’identification des mots commençant par la lettre « d ».

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Si des options sont spécifiées inline, un signe moins (`-`) avant une option ou un jeu d'options désactive ces options. Par exemple, la construction inline `(?ix-ms)` active les options <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> et <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> et désactive les options <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> et <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>. Toutes les options d'expression régulière sont désactivées par défaut.

> [!NOTE]
> Si les options d'expression régulière spécifiées dans le paramètre `options` d'un appel de constructeur ou de méthode entrent en conflit avec les options spécifiées inline dans un modèle d'expression régulière, ces dernières sont utilisées.

Les cinq options d'expression régulière suivantes peuvent être définies avec le paramètre options et inline :

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Les cinq options d'expression régulière suivantes peuvent être définies avec le paramètre `options`, mais ne peuvent pas être définies inline :

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Détermination des options

Vous pouvez déterminer les options initialement fournies à un objet <xref:System.Text.RegularExpressions.Regex> au moment de son instanciation en récupérant la valeur de la propriété <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> en lecture seule. Cette propriété est particulièrement utile pour déterminer les options qui sont définies pour une expression régulière compilée créée par la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>.

Pour tester la présence d'une option autre que <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, effectuez une opération AND avec la valeur de la propriété <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> et la valeur <xref:System.Text.RegularExpressions.RegexOptions> qui vous intéresse. Ensuite, déterminez si le résultat est égal à cette valeur <xref:System.Text.RegularExpressions.RegexOptions>. L'exemple suivant détermine si l'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a été définie.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Pour tester la présence de <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, déterminez si la valeur de la propriété <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> est égale à <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, comme le montre l'exemple suivant.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

Les sections suivantes répertorient les options prises en charge par les expressions régulières dans .NET.

## <a name="default-options"></a>Options par défaut

L'option <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> indique qu'aucune option n'a été spécifiée et que le moteur d'expression régulière utilise son comportement par défaut. Ce dernier est détaillé ci-après :

- Le modèle est interprété en tant qu'expression régulière canonique, plutôt qu'en tant qu'expression régulière ECMAScript.

- Le modèle d'expression régulière est appliqué à la chaîne d'entrée de la gauche vers la droite.

- Les comparaisons respectent la casse.

- Les éléments de langage `^` et `$` correspondent au début et à la fin de la chaîne d'entrée.

- L'élément de langage `.` correspond à chaque caractère à l'exception de `\n`.

- Tout espace blanc dans un modèle d'expression régulière est interprété en tant qu'espace littéral.

- Les conventions de la culture actuelle sont utilisées pendant la comparaison du modèle à la chaîne d'entrée.

- Les groupes de capture dans le modèle d’expression régulière sont implicites aussi bien qu’explicites.

> [!NOTE]
> L'option <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> n'a pas d'équivalent inline. Quand les options d'expression régulière sont appliquées inline, le comportement par défaut est restauré option par option, via la désactivation de chaque option concernée. Par exemple, `(?i)` active la comparaison sans respect de la casse, tandis que `(?-i)` restaure la comparaison avec respect de la casse par défaut.

Comme l'option <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> représente le comportement par défaut du moteur d'expression régulière, elle est rarement spécifiée de manière explicite dans un appel de méthode. Un constructeur ou une méthode de mise en correspondance de modèle statique sans paramètre `options` est appelé à la place.

## <a name="case-insensitive-matching"></a>Correspondance qui ne respecte pas la casse

L'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>, ou l'option inline `i`, fournit une correspondance qui ne respecte pas la casse. Par défaut, les conventions de gestion de la casse de la culture actuelle sont utilisées.

L'exemple suivant définit un modèle d'expression régulière, `\bthe\w*\b`, qui met en correspondance tous les mots commençant par « the ». Comme le premier appel de la méthode <xref:System.Text.RegularExpressions.Regex.Match%2A> utilise la comparaison avec respect de la casse par défaut, la chaîne « The » n'apparaît pas parmi les résultats de ce premier appel. Par contre, elle est trouvée quand la méthode <xref:System.Text.RegularExpressions.Regex.Match%2A> est appelée avec le paramètre options défini sur <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

L'exemple suivant modifie le modèle d'expression régulière proposé dans l'exemple précédent de manière à utiliser des options inline au lieu du paramètre `options` pour effectuer une comparaison sans respect de la casse. Le premier modèle définit l’option de non-respect de la casse dans une construction de regroupement qui s’applique uniquement à la lettre « t » de la chaîne « the ». Comme la construction de l’option intervient au début du modèle, le second modèle applique l’option de non-respect de la casse à l’expression régulière entière.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Mode multiligne

L'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, ou l'option inline `m`, permet au moteur d'expression régulière de gérer une chaîne d'entrée constituée de plusieurs lignes. Elle modifie l'interprétation des éléments de langage `^` et `$` de manière à ce qu'ils correspondent au début et à la fin d'une ligne, et non au début et à la fin de la chaîne d'entrée.

Par défaut, `$` correspond uniquement à la fin de la chaîne d'entrée. Si vous spécifiez l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, elle correspond au caractère de saut de ligne (`\n`) ou à la fin de la chaîne d'entrée. Toutefois, elle ne correspond pas à la combinaison de caractères retour chariot/saut de ligne. Pour les mettre en correspondance, utilisez la sous-expression `\r?$` au lieu de simplement `$`.

L’exemple suivant extrait les prénoms et scores des lanceurs, puis les ajoute à une collection <xref:System.Collections.Generic.SortedList%602> qui les trie dans l’ordre décroissant. La méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A> est appelée deux fois. Dans le premier appel de la méthode, l'expression régulière est `^(\w+)\s(\d+)$` et aucune option n'est définie. Comme le montre la sortie, aucune correspondance n’est trouvée, car le moteur d’expression régulière ne peut pas mettre en correspondance le modèle d’entrée avec le début et la fin de la chaîne d’entrée. Dans le second appel de la méthode, l'expression régulière devient `^(\w+)\s(\d+)\r?$` et les options sont définies sur <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Comme le montre la sortie, les noms et scores sont correctement mis en correspondance, et les scores apparaissent dans l'ordre décroissant.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Le modèle d'expression régulière `^(\w+)\s(\d+)\r*$` est défini comme indiqué dans le tableau suivant.

|Modèle|Description|
|-------------|-----------------|
|`^`|Commencer au début de la ligne.|
|`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|
|`\s`|Mettre en correspondance un espace blanc.|
|`(\d+)`|Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du deuxième groupe de capture.|
|`\r?`|Mettre en correspondance zéro ou un caractère de retour chariot.|
|`$`|Terminer à la fin de la ligne.|

L'exemple suivant est équivalent à l'exemple précédent, à la différence qu'il utilise l'option inline `(?m)` pour définir l'option multiligne.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Mode à ligne simple

L'option <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>, ou l'option inline `s`, indique au moteur d'expression régulière de traiter la chaîne d'entrée comme si elle était composée d'une seule ligne. Pour ce faire, elle modifie le comportement de l'élément de langage point (`.`) de manière à mettre en correspondance chaque caractère, y compris le caractère de saut de ligne `\n` ou \u000A.

L'exemple suivant montre comment l'utilisation de l'option `.` modifie le comportement de l'élément de langage <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>. L'expression régulière `^.+` commence au début de la chaîne et correspond à tous les caractères. Par défaut, la correspondance se termine à la fin de la première ligne ; le modèle d'expression régulière correspond au retour chariot, à `\r` ou à \u000D, mais il ne correspond pas à `\n`. Étant donné que l'option <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> interprète la chaîne d'entrée entière comme une ligne unique, il correspond à chaque caractère de la chaîne d'entrée, notamment `\n`.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

L'exemple suivant est équivalent à l'exemple précédent, à la différence qu'il utilise l'option inline `(?s)` pour activer le mode à ligne simple.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Captures explicites uniquement

Par défaut, les groupes de capture sont définis à l’aide de parenthèses dans le modèle d’expression régulière. Les groupes nommés se voient affecter un nom ou un nombre par l’option de langage nom sous- `(?<` *name* `>` *expression* `)` , tandis que les groupes sans nom sont accessibles par index. Dans l'objet <xref:System.Text.RegularExpressions.GroupCollection>, les groupes sans nom précèdent les groupes nommés.

Les constructions de regroupement sont souvent utilisées pour simplement appliquer des quantificateurs à plusieurs éléments de langage, et les sous-chaînes capturées ne présentent aucun intérêt. Par exemple, si l'expression régulière suivante :

`\b\(?((\w+),?\s?)+[\.!?]\)?`

est uniquement destinée à extraire d'un document les phrases qui se terminent par un point, un point d'exclamation ou un point d'interrogation, seule la phrase résultante (représentée par l'objet <xref:System.Text.RegularExpressions.Match>) présente un intérêt. Les différents mots de la collection n’en présentent pas.

Les groupes de capture qui ne sont pas utilisés par la suite peuvent affecter les performances, car le moteur d’expression régulière doit remplir les deux objets de collection <xref:System.Text.RegularExpressions.GroupCollection> et <xref:System.Text.RegularExpressions.CaptureCollection>. En guise de solution, vous pouvez utiliser l'option <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> ou l'option inline `n` pour indiquer que les seules captures valides sont les groupes explicitement nommés ou numérotés désignés par la construction `(?<`*nom*`>` *sous-expression*`)`.

L’exemple suivant affiche des informations sur les correspondances retournées par le modèle d’expression régulière `\b\(?((\w+),?\s?)+[\.!?]\)?` quand la méthode <xref:System.Text.RegularExpressions.Regex.Match%2A> est appelée avec et sans l’option <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>. Comme le montre la sortie du premier appel de la méthode, le moteur d’expression régulière remplit entièrement les objets de collection <xref:System.Text.RegularExpressions.GroupCollection> et <xref:System.Text.RegularExpressions.CaptureCollection> avec des informations relatives aux sous-chaînes capturées. Comme la seconde méthode est appelée avec `options` défini sur <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, elle ne capture pas d'information sur les groupes.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Le modèle d'expression régulière `\b\(?((?>\w+),?\s?)+[\.!?]\)?` est défini comme indiqué dans le tableau suivant.

|Modèle|Description|
|-------------|-----------------|
|`\b`|Commencer à la limite d'un mot.|
|`\(?`|Mettre en correspondance zéro occurrence, ou plus, de la parenthèse ouvrante (« ( »).|
|`(?>\w+),?`|Mettre en correspondance un ou plusieurs caractères alphabétiques, suivis de zéro virgule, ou plus. Ne pas effectuer de recherches rétroactives quand des caractères alphabétiques sont mis en correspondance.|
|`\s?`|Mettre en correspondance zéro ou des espaces blancs.|
|`((\w+),?\s?)+`|Mettre en correspondance la combinaison d'un ou plusieurs caractères alphabétiques, suivis de zéro ou d'une virgule, suivies de zéro ou d'un espace blanc, une ou plusieurs fois.|
|`[\.!?]\)?`|Mettre en correspondance n'importe lequel des trois symboles de ponctuation, suivi de zéro ou d'une parenthèse fermante (« ) »).|

Vous pouvez également utiliser l'élément inline `(?n)` pour supprimer les captures automatiques. L’exemple suivant modifie le modèle d’expression régulière précédent pour utiliser l’élément inline `(?n)` au lieu de l’option <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Enfin, vous pouvez utiliser l'élément de groupe inline `(?n:)` pour supprimer les captures automatiques groupe par groupe. L'exemple suivant modifie le modèle précédent pour supprimer les captures sans nom du groupe externe, `((?>\w+),?\s?)`. Notez que cette opération supprime également les captures sans nom du groupe interne.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Expressions régulières compilées

Par défaut, les expressions régulières dans .NET sont interprétées. Quand un objet <xref:System.Text.RegularExpressions.Regex> est instancié ou qu'une méthode <xref:System.Text.RegularExpressions.Regex> statique est appelée, le modèle d'expression régulière est analysé de manière à générer un ensemble d'opcodes personnalisés, puis un interpréteur utilise ces opcodes pour exécuter l'expression régulière. Cela implique un compromis : le coût d'initialisation du moteur d'expression régulière est réduit au prix d'une baisse des performances au moment de l'exécution.

Vous pouvez utiliser des expressions régulières compilées à la place d'expressions régulières interprétées en utilisant l'option <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>. Dans ce cas, quand un modèle est transmis au moteur d’expression régulière, il est analysé de manière à générer un ensemble d’opcodes convertis ensuite en un code MSIL (Microsoft Intermediate Language), qui peut être directement communiqué au Common Language Runtime. Les expressions régulières compilées optimisent les performances d'exécution au détriment du temps d'initialisation.

> [!NOTE]
> Pour compiler une expression régulière, vous devez fournir la valeur <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> au paramètre `options` d’un constructeur de classe <xref:System.Text.RegularExpressions.Regex> ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline.

Vous pouvez utiliser des expressions régulières compilées dans les appels d'expressions régulières statiques et d'instance. Dans les expressions régulières statiques, l'option <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> est transmise au paramètre `options` de la méthode de mise en correspondance de modèle d'expression régulière. Dans les expressions régulières d'instance, elle est transmise au paramètre `options` du constructeur de classe <xref:System.Text.RegularExpressions.Regex>. Dans les deux cas, les performances s'en trouvent améliorées.

Toutefois, cette amélioration ne se produit que dans les conditions suivantes :

- Un objet <xref:System.Text.RegularExpressions.Regex> qui représente une expression régulière particulière est utilisé dans plusieurs appels de méthodes de mise en correspondance de modèle d'expression régulière.

- La portée de l'objet <xref:System.Text.RegularExpressions.Regex> est strictement délimitée, ce qui permet sa réutilisation.

- Une expression régulière statique est utilisée dans plusieurs appels de méthodes de mise en correspondance de modèle d’expression régulière. (L'amélioration des performances est possible, car les expressions régulières utilisées dans les appels de méthode statique sont mises en cache par le moteur d'expression régulière.)

> [!NOTE]
> L'option <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> n'est pas liée à la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>, qui crée un assembly à usage particulier contenant des expressions régulières compilées prédéfinies.

## <a name="ignore-white-space"></a>Ignorer l'espace blanc

Par défaut, l’espace blanc dans un modèle d’expression régulière est significatif ; il oblige le moteur d’expression régulière à mettre en correspondance un espace blanc dans la chaîne d’entrée. Ainsi, les expressions régulières « `\b\w+\s` » et « `\b\w+` » sont pratiquement équivalentes. En outre, quand le signe dièse (#) est rencontré dans un modèle d’expression régulière, il est interprété comme un caractère littéral à mettre en correspondance.

L'option <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>, ou l'option inline `x`, modifie ce comportement par défaut comme suit :

- L’espace blanc sans séquence d’échappement dans le modèle d’expression régulière est ignoré. Pour faire partie d’un modèle d’expression régulière, les espaces blancs doivent être inclus dans une séquence d’échappement (par exemple, as `\s` ou « `\` »).

- Le signe dièse (#) est interprété comme le début d'un commentaire, plutôt que comme un caractère littéral. Tout le texte d’un modèle d’expression régulière depuis le caractère # jusqu’à la fin de la chaîne est interprété comme un commentaire.

Toutefois, dans les cas suivants, les espaces blancs d’une expression régulière ne sont pas ignorés, même si vous utilisez l’option <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> :

- L'espace blanc dans une classe de caractères est toujours interprété de façon littérale. Par exemple, le modèle d'expression régulière `[ .,;:]` met en correspondance n'importe quel espace blanc, point, virgule, point-virgule ou symbole deux-points unique.

- L’espace blanc n’est pas autorisé dans un quantificateur entre crochets, tel que `{` *n* `}` , `{` *n* `,}` et `{` *n* `,` *m* `}` . Par exemple, le modèle d'expression régulière `\d{1, 3}` ne peut pas mettre en correspondance les séquences d'un à trois chiffres, car il contient un espace blanc.

- L'espace blanc n'est pas autorisé dans une séquence de caractères qui introduit un élément de langage. Par exemple :

  - L’élément de langage sous- `(?:` *expression* `)` représente un groupe sans capture, et la `(?:` partie de l’élément ne peut pas avoir d’espaces incorporés. Le modèle sous- `(? :` *expression* `)` lève une <xref:System.ArgumentException> au moment de l’exécution, car le moteur d’expression régulière ne peut pas analyser le modèle, et le modèle sous-expression `( ?:` *subexpression* `)` ne parvient pas à faire correspondre *subexpression*la sous-expression.

  - Le nom de l’élément `\p{` *name* `}` de langage, qui représente une catégorie Unicode ou un bloc nommé, ne peut pas inclure d’espaces dans la `\p{` partie de l’élément. Si vous incluez un espace blanc, l'élément lève une <xref:System.ArgumentException> au moment de l'exécution.

L'activation de cette option permet de simplifier les expressions régulières qui sont souvent difficiles à analyser et à comprendre. Elle améliore la lisibilité et rend possible la documentation d'une expression régulière.

L’exemple ci-après définit le modèle d’expression régulière suivant :

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Ce modèle est similaire au modèle défini dans la section [Captures explicites uniquement](#explicit-captures-only), à la différence qu’il utilise l’option <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> pour ignorer l’espace blanc du modèle.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

L'exemple suivant utilise l'option inline `(?x)` pour ignorer l'espace blanc du modèle.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Mode de recherche de droite à gauche

Par défaut, le moteur d'expression régulière recherche de gauche à droite. Vous pouvez inverser le sens de la recherche à l'aide de l'option <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>. La recherche commence automatiquement à la position du dernier caractère de la chaîne. Pour les méthodes de mise en correspondance de modèle qui comprennent un paramètre de position de début, comme <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, la position de début est l’index de la position du caractère le plus à droite à laquelle la recherche doit commencer.

> [!NOTE]
> Pour utiliser le mode de recherche de droite à gauche, vous devez fournir la valeur <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> au paramètre `options` d’un constructeur de classe <xref:System.Text.RegularExpressions.Regex> ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline.

L’option <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> modifie uniquement le sens de la recherche ; elle n’interprète pas le modèle d’expression régulière de droite à gauche. Par exemple, l'expression régulière `\bb\w+\s` met en correspondance les mots qui commencent par la lettre « b » et qui sont suivis d'un espace blanc. Dans l'exemple suivant, la chaîne d'entrée se compose de trois mots qui comprennent un ou plusieurs caractères « b ». Le premier mot commence par « b », le deuxième se termine par « b », tandis que le troisième comprend deux caractères « b » en son milieu. Comme le montre la sortie de l’exemple, seul le premier mot correspond au modèle d’expression régulière.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Notez également que l’assertion de préanalyse (l’élément de langage sous- `(?=` *expression* `)` ) et l’assertion de postanalyse (l' `(?<=` *subexpression* `)` élément de langage sous-expression) ne changent pas le sens. Les assertions de préanalyse recherchent vers la droite, tandis que les assertions de postanalyse recherchent vers la gauche. Par exemple, l'expression régulière `(?<=\d{1,2}\s)\w+,?\s\d{4}` utilise l'assertion de postanalyse pour déterminer si une date précède le nom d'un mois. Ensuite, l'expression régulière met en correspondance le mois et l'année. Pour plus d’informations sur les assertions de préanalyse et de postanalyse, voir [Constructions de regroupement](grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

|Modèle|Description|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Le début de la correspondance doit être précédé d'un ou deux chiffres décimaux suivis d'un espace.|
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|
|`,?`|Mettre en correspondance zéro ou une virgule.|
|`\s`|Mettre en correspondance un espace blanc.|
|`\d{4}`|Mettre en correspondance quatre chiffres décimaux.|

## <a name="ecmascript-matching-behavior"></a>Comportement de correspondance ECMAScript

Par défaut, le moteur d’expression régulière utilise un comportement canonique pour appliquer un modèle d’expression régulière à un texte d’entrée. Toutefois, vous pouvez indiquer au moteur d’expression régulière d’utiliser un comportement de correspondance ECMAScript en spécifiant l’option <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>.

> [!NOTE]
> À cette fin, vous devez fournir la valeur <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> au paramètre `options` d’un constructeur de classe <xref:System.Text.RegularExpressions.Regex> ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline.

L'option <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> ne peut être combinée qu'aux options <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> et <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. L'utilisation d'une autre option dans une expression régulière aboutit à une <xref:System.ArgumentOutOfRangeException>.

Le comportement des expressions régulières ECMAScript et canoniques diffère dans trois domaines : la syntaxe de la classe de caractères, les groupes de capture avec référence circulaire et l’interprétation des séquences d’échappement octales ou des références arrière.

- Syntaxe de la classe de caractères. Comme les expressions régulières canoniques prennent en charge Unicode, contrairement à ECMAScript, les classes de caractères dans ECMAScript possèdent une syntaxe plus limitée, et certains éléments de langage des classes de caractères ont une signification différente. Par exemple, ECMAScript ne prend pas en charge les éléments de langage tels que la catégorie Unicode ou les éléments de bloc `\p` et `\P`. De même, l'élément `\w`, qui correspond à un caractère alphabétique, est équivalent à la classe de caractères `[a-zA-Z_0-9]`, dans le cas de l'utilisation d'ECMAScript, et à `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]`, dans le cas de l'utilisation du comportement canonique. Pour plus d’informations, consultez [classes de caractères](character-classes-in-regular-expressions.md).

  L’exemple suivant illustre la différence entre les mises en correspondance de modèle canonique et ECMAScript. Il définit une expression régulière, `\b(\w+\s*)+`, qui met en correspondance les mots suivis d'espaces blancs. L'entrée se compose de deux chaînes ; l'une d'elles utilise le jeu de caractères latin, l'autre le jeu de caractères cyrillique. Comme le montre la sortie, l’appel de méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> qui utilise la correspondance ECMAScript ne parvient pas à mettre en correspondance les mots cyrilliques, contrairement à l’appel de méthode qui utilise la correspondance canonique.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Groupes de capture avec référence circulaire. Une classe de capture d'expression régulière avec une référence arrière à elle-même doit être mise à jour à chaque itération de capture. Comme le montre l'exemple suivant, cette fonctionnalité permet à l'expression régulière `((a+)(\1) ?)+` de mettre en correspondance la chaîne d'entrée «  aa aaaa aaaaaa  » dans le cas de l'utilisation de la correspondance ECMAScript, mais pas dans le cas de l'utilisation de la correspondance canonique.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  L'expression régulière est définie comme indiqué dans le tableau suivant.

  |Modèle|Description|
  |-------------|-----------------|
  |(a+)|Mettre en correspondance la lettre « a » une ou plusieurs fois. Il s'agit du deuxième groupe de capture.|
  |(\1)|Mettre en correspondance la sous-chaîne capturée par le premier groupe de capture. Il s'agit du troisième groupe de capture.|
  |?|Mettre en correspondance zéro ou un espace.|
  |((a+)(\1) ?)+|Mettre en correspondance le modèle d'un ou plusieurs caractères « a » suivis d'une chaîne correspondant au premier groupe de capture, suivie de zéro ou un espace, une ou plusieurs fois. Il s'agit du premier groupe de capture.|

- Résolution des ambiguïtés entre les séquences d'échappement octales et les références arrière. Le tableau suivant compare la façon dont les expressions régulières canoniques et ECMAScript interprètent les séquences d'échappement octales et les références arrière.

  |Expression régulière|Comportement canonique|Comportement ECMAScript|
  |------------------------|------------------------|-------------------------|
  |`\0` suivi de 0 à 2 chiffres octaux|Interpréter comme un octal. Par exemple, `\044` est toujours interprété comme une valeur octale et signifie « $ ».|Même comportement.|
  |`\` suivi d'un chiffre entre 1 et 9, non suivi de chiffres décimaux.|Interpréter comme une référence arrière. Par exemple, `\9` signifie toujours référence arrière 9, même si un neuvième groupe de capture n'existe pas. Si le groupe de capture n'existe pas, l'analyseur de l'expression régulière lève une <xref:System.ArgumentException>.|Si un groupe de capture avec chiffre décimal unique existe, effectuer une référence arrière au niveau de ce chiffre. Sinon, interpréter la valeur en tant que littéral.|
  |`\` suivi d'un chiffre entre 1 et 9, suivi de chiffres décimaux supplémentaires.|Interpréter les chiffres en tant que valeur décimale. Si ce groupe de capture existe, interpréter l'expression en tant que référence arrière.<br /><br /> Sinon, interpréter les chiffres octaux de début jusqu'à l'octal 377 ; en d'autres termes, ne prendre en compte que les 8 bits de poids faible de la valeur. Interpréter les autres chiffres comme des littéraux. Par exemple, dans l'expression `\3000`, si le groupe de capture 300 existe, interpréter en tant que référence arrière 300, sinon, interpréter en tant qu'octal 300 suivi de 0.|Interpréter en tant que référence arrière en convertissant autant de chiffres que possible en valeur décimale pouvant faire référence à une capture. Si aucun chiffre ne peut être converti, interpréter en tant qu'octal en utilisant les chiffres octaux de début jusqu'à l'octal 377 ; interpréter les autres chiffres en tant que littéraux.|

## <a name="comparison-using-the-invariant-culture"></a>Comparaison utilisant la culture dite indifférente

Par défaut, quand le moteur d'expression régulière effectue des comparaisons sans respect de la casse, il utilise les conventions de gestion de la casse de la culture actuelle pour déterminer les caractères majuscules et minuscules équivalents.

Toutefois, ce comportement n'est pas souhaitable pour certains types de comparaisons, notamment celles entre les entrées utilisateur et les noms de ressources système, comme les mots de passe, les fichiers ou les URL. L'exemple suivant illustre un scénario de ce type. Le code est destiné à bloquer l’accès à toute ressource dont l’URL commence par **FILE://**. Le moteur d'expression régulière essaie d'effectuer une mise en correspondance sans respect de la casse avec la chaîne en utilisant l'expression régulière `$FILE://`. Toutefois, quand la culture système actuelle est tr-TR (Turc-Turquie), « I » n'est pas l'équivalent en majuscule de « i ». L'appel de la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> renvoie donc `false`, et l'accès au fichier est autorisé.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Pour plus d’informations sur les comparaisons de chaînes respectant la casse et utilisant la culture dite indifférente, consultez [Bonnes pratiques pour l’utilisation de chaînes](best-practices-strings.md).

Au lieu d'utiliser les comparaisons sans respect de la casse de la culture actuelle, vous pouvez spécifier l'option <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> pour ignorer les différences culturelles propres à la langue et pour utiliser les conventions de la culture dite indifférente.

> [!NOTE]
> Pour effectuer une comparaison en utilisant la culture Invariant, vous devez fournir la valeur <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> au paramètre `options` d'un constructeur de classe <xref:System.Text.RegularExpressions.Regex> ou d'une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline.

L'exemple suivant est identique à l'exemple précédent, à la différence que la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> statique est appelée avec des options qui incluent <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Même si la culture actuelle est définie sur Turc (Turquie), le moteur d'expression régulière parvient à mettre en correspondance « FILE » et « file » et à bloquer l'accès à la ressource de fichier.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
