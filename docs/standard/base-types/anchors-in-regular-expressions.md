---
title: Ancres dans les expressions régulières .NET
description: Découvrez comment utiliser des ancres dans les modèles d’expressions régulières.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- atomic zero-width assertions
- regular expressions, anchors
- regular expressions, atomic zero-width assertions
- anchors, in regular expressions
- metacharacters, atomic zero-width assertions
- metacharacters, anchors
- .NET regular expressions, anchors
- .NET regular expressions, atomic zero-width assertions
ms.assetid: 336391f6-2614-499b-8b1b-07a6837108a7
ms.openlocfilehash: 5f40270baa70c2b72d768cf0f5c4f8305f8bae7a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825271"
---
# <a name="anchors-in-regular-expressions"></a>Ancres dans les expressions régulières
Les ancres, ou assertions atomiques de largeur nulle, spécifient une position dans la chaîne où une correspondance doit se produire. Quand vous utilisez une ancre dans votre expression de recherche, le moteur des expressions régulières n'avance pas dans la chaîne ou ne consomme pas de caractères ; il recherche uniquement une correspondance à la position spécifiée. Par exemple, `^` spécifie que la correspondance doit commencer au début d'une ligne ou d'une chaîne. Par conséquent, l'expression régulière `^http:` correspond uniquement à « http: » quand elle se produit au début d'une ligne. Le tableau suivant répertorie les ancres prises en charge par les expressions régulières dans .NET.  
  
|Ancre|Description|  
|------------|-----------------|  
|`^`|Par défaut, la correspondance doit se produire au début de la chaîne ; en mode multiligne, elle doit se produire au début de la ligne. Pour plus d'informations, consultez [Début de chaîne ou de ligne](#start-of-string-or-line-).|  
|`$`|Par défaut, la correspondance doit se produire à la fin de la chaîne ou avant `\n` à la fin de la chaîne ; en mode multiligne, elle doit se produire à la fin de la ligne ou avant `\n` à la fin de la ligne. Pour plus d'informations, consultez [Fin de chaîne ou de ligne](#end-of-string-or-line-).|  
|`\A`|La correspondance doit se produire au début de la chaîne uniquement (aucun support multiligne). Pour plus d'informations, consultez [Début de chaîne uniquement](#start-of-string-only-a).|  
|`\Z`|La correspondance doit se produire à la fin de la chaîne, ou avant `\n` à la fin de la chaîne. Pour plus d'informations, consultez [Fin de chaîne ou avant un saut de ligne final](#end-of-string-or-before-ending-newline-z).|  
|`\z`|La correspondance doit se produire uniquement à la fin de la chaîne. Pour plus d'informations, consultez [Fin de chaîne uniquement](#end-of-string-only-z).|  
|`\G`|La correspondance doit démarrer à la position où la correspondance précédente s'est terminée. Pour plus d'informations, consultez [Correspondances contiguës](#contiguous-matches-g).|  
|`\b`|La correspondance doit se produire à la limite d'un mot. Pour plus d'informations, consultez [Limite de mot](#word-boundary-b).|  
|`\B`|La correspondance ne doit pas se produire à la limite d'un mot. Pour plus d'informations, consultez [Limite n'appartenant pas à un mot](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Début de chaîne ou de ligne : ^  
 Par défaut, l’ancre `^` spécifie que le modèle suivant doit commencer à la première position de caractère de la chaîne. Si vous utilisez `^` avec l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> (consultez [Options des expressions régulières](regular-expression-options.md)), la correspondance doit se trouver au début de chaque ligne.  
  
 L'exemple suivant utilise l'ancre `^` dans une expression régulière qui extrait des informations à propos des années pendant lesquelles certaines équipes de base-ball professionnelles ont existé. L'exemple appelle deux surcharges de la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> :  
  
- L'appel à la surcharge <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> recherche uniquement la première sous-chaîne dans la chaîne d'entrée qui correspond au modèle d'expression régulière.  
  
- L'appel à la surcharge <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> avec le paramètre `options` défini avec la valeur <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> trouve les cinq sous-chaînes.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Le modèle d'expression régulière `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commencer la correspondance au début de la chaîne d'entrée (ou au début de la ligne si la méthode est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ).|  
|`((\w+(\s?)){2,}`|Mettre en correspondance un ou plusieurs caractères de mot suivis de zéro ou d’un espace au moins deux fois. Il s'agit du premier groupe de capture. Cette expression définit également un deuxième et un troisième groupe de capture : le deuxième se compose du mot capturé, et le troisième est constitué de l’espace blanc capturé.|  
|`,\s`|Mettre en correspondance une virgule suivie d'un caractère d'espace blanc.|  
|`(\w+\s\w+)`|Mettre en correspondance un ou plusieurs caractères de mot suivis d'un espace, suivi d'un ou plusieurs caractères de mot. Il s'agit du quatrième groupe de capture.|  
|`,`|Mettre en correspondance une virgule.|  
|`\s\d{4}`|Mettre en correspondance un espace suivi de quatre chiffres décimaux.|  
|<code>(-(\d{4}&#124;present))?</code>|Mettre en correspondance zéro ou une occurrence d'un trait d'union suivie de quatre chiffres décimaux ou de la chaîne « present ». Il s'agit du sixième groupe de capture. Il inclut également un septième groupe de capture.|  
|`,?`|Mettre en correspondance zéro ou une occurrence d'une virgule.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Mettre en correspondance une ou plusieurs occurrences des éléments suivants : un espace, quatre chiffres décimaux, zéro ou une occurrence d'un trait d'union suivie de quatre chiffres décimaux ou de la chaîne « present » et zéro ou une virgule. Il s'agit du cinquième groupe de capture.|

## <a name="end-of-string-or-line-"></a>Fin de chaîne ou de ligne : $  
 L'ancre `$` spécifie que le modèle précédent doit se produire à la fin de la chaîne d'entrée ou avant `\n` à la fin de la chaîne d'entrée.  
  
 Si vous utilisez `$` avec l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> , la correspondance peut également se trouver à la fin d'une ligne. Notez que `$` correspond à `\n` , mais ne correspond pas à `\r\n` (combinaison de caractères de retour chariot et de saut de ligne ou CR/LF). Pour établir une correspondance avec la combinaison de caractères CR/LF, incluez `\r?$` dans le modèle d'expression régulière.  
  
 L'exemple suivant ajoute l'ancre `$` au modèle d'expression régulière utilisé dans l'exemple dans la section [Début de chaîne ou de ligne](#start-of-string-or-line-) . En cas d'utilisation avec la chaîne d'entrée d'origine, qui inclut cinq lignes de texte, la méthode <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> ne peut pas trouver de correspondance, parce que la fin de la première ligne ne correspond pas au modèle `$` . Quand la chaîne d'entrée d'origine est fractionnée dans un tableau de chaînes, la méthode <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> réussit à faire correspondre chacune des cinq lignes. Quand la méthode <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> est appelée avec le paramètre `options` défini avec la valeur <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, aucune correspondance n'est trouvée parce que le modèle d'expression régulière ne représente pas l'élément de retour chariot (\u+000D). Toutefois, quand le modèle d'expression régulière est modifié par le remplacement de `$` par `\r?$`, l'appel de la méthode <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> avec le paramètre `options` défini avec la valeur <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> trouve encore cinq correspondances.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Début de chaîne uniquement : \A  
 L'ancre `\A` spécifie qu'une correspondance doit se produire au début de la chaîne d'entrée. Elle est identique à l'ancre `^` , à la différence près que l'ancre `\A` ignore l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> . Par conséquent, elle peut correspondre uniquement au début de la première ligne dans une chaîne d'entrée multiligne.  
  
 L'exemple suivant est semblable aux exemples des ancres `^` et `$` . Il utilise l'ancre `\A` dans une expression régulière qui extrait des informations sur les années où jouaient certaines équipes de base-ball professionnelles. La chaîne d'entrée inclut cinq lignes. L'appel à la méthode <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> recherche uniquement la première sous-chaîne dans la chaîne d'entrée qui correspond au modèle d'expression régulière. Comme le montre l'exemple, l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline> n'a aucun effet.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Fin de chaîne ou avant un saut de ligne final : \Z  
 L'ancre `\Z` spécifie qu'une correspondance doit se produire à la fin de la chaîne d'entrée ou avant `\n` à la fin de la chaîne d'entrée. Elle est identique à l'ancre `$` , à la différence près que l'ancre `\Z` ignore l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> . Par conséquent, dans une chaîne multiligne, elle peut correspondre uniquement à la fin de la dernière ligne ou à la dernière ligne avant `\n`.  
  
 Notez que `\Z` correspond à `\n` , mais ne correspond pas à `\r\n` (combinaison de caractères CR/LF). Pour établir une correspondance avec les caractères CR/LF, incluez `\r?\Z` dans le modèle d'expression régulière.  
  
 L'exemple suivant utilise l'ancre `\Z` dans une expression régulière qui est semblable à l'exemple dans la section [Début de chaîne ou de ligne](#start-of-string-or-line-) , qui extrait des informations à propos des années pendant lesquelles certaines équipes de base-ball professionnelles ont existé. La sous-expression `\r?\Z` dans l'expression régulière `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` correspond à la fin d'une chaîne et correspond également à une chaîne qui se termine par `\n` ou `\r\n`. Par conséquent, chaque élément du tableau correspond au modèle d’expression régulière.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Fin de chaîne uniquement : \z  
 L'ancre `\z` spécifie qu'une correspondance doit se produire à la fin de la chaîne d'entrée. Comme l'élément de langage `$` , `\z` ignore l'option <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> . Contrairement à l'élément de langage `\Z` , `\z` ne correspond pas à un caractère `\n` à la fin d'une chaîne. Par conséquent, elle peut correspondre uniquement à la dernière ligne de la chaîne d'entrée.  
  
 L'exemple suivant utilise l'ancre `\z` dans une expression régulière qui est sinon identique à l'exemple dans la section précédente, qui extrait des informations à propos des années pendant lesquelles certaines équipes de base-ball professionnelles ont existé. L'exemple essaie de faire correspondre chacun des cinq éléments dans un tableau de chaînes avec le modèle d'expression régulière `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Deux des chaînes se terminent par un retour chariot et des caractères de saut de ligne, l'une se termine par un caractère de saut de ligne, et deux ne se terminent ni par un retour chariot ni par un caractère de saut de ligne. Comme le montre la sortie, seules les chaînes sans retour chariot ou caractère de saut de ligne correspondent au modèle.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Correspondances contiguës : \G  
 L'ancre `\G` spécifie qu'une correspondance doit se produire au point où la correspondance précédente s'est terminée. Quand vous utilisez cette ancre avec la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> , elle vérifie que toutes les correspondances sont contiguës.  
  
 L'exemple suivant utilise une expression régulière pour extraire les noms d'espèces de rongeurs d'une chaîne délimitée par des virgules.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 L'expression régulière `\G(\w+\s?\w*),?` est interprétée comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\G`|Commencer là où la dernière correspondance s'est terminée.|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|`\s?`|Mettre en correspondance zéro ou un espace.|  
|`\w*`|Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.|  
|`(\w+\s?\w*)`|Mettre en correspondance un ou plusieurs caractères de mot suivis de zéro ou d'un espace, suivi de zéro ou davantage de caractères de mot. Il s'agit du premier groupe de capture.|  
|`,?`|Mettre en correspondance zéro ou une occurrence d'une virgule littérale.|

## <a name="word-boundary-b"></a>Limite de mot : \b  
 L'ancre `\b` spécifie que la correspondance doit se produire à la limite entre un caractère de mot (élément de langage `\w` ) et un caractère n'appartenant pas à un mot (élément de langage `\W` ). Les caractères de mot se composent de caractères alphanumériques et de traits de soulignement ; un caractère n'appartenant pas à un mot est un caractère qui n'est pas alphanumérique ou qui n'est pas un trait de soulignement. (Pour plus d’informations, consultez [classes de caractères](character-classes-in-regular-expressions.md).) La correspondance peut également se produire à la limite d’un mot au début ou à la fin de la chaîne.  
  
 L'ancre `\b` est fréquemment utilisée pour faire en sorte qu'une sous-expression corresponde à un mot entier plutôt qu'au début ou à la fin d'un mot uniquement. L'expression régulière `\bare\w*\b` dans l'exemple suivant illustre cette utilisation. Elle correspond à tout mot qui commence par la sous-chaîne « are ». La sortie de l'exemple illustre également que `\b` correspond à la fois au début et la fin de la chaîne d'entrée.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Le modèle d'expression régulière est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`are`|Mettre en correspondance la sous-chaîne « are ».|  
|`\w*`|Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  

## <a name="non-word-boundary-b"></a>Limite n'appartenant pas à un mot : \B  
 L'ancre `\B` spécifie que la correspondance ne doit pas se produire à la limite d'un mot. Elle est le contraire de l'ancre `\b` .  
  
 L'exemple suivant utilise l'ancre `\B` pour trouver des occurrences de la sous-chaîne « qu » dans un mot. Le modèle d'expression régulière `\Bqu\w+` met en correspondance une sous-chaîne qui commence par un « qu » qui n'est pas en début de mot et continue jusqu'à la fin du mot.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Le modèle d'expression régulière est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\B`|Ne pas commencer la correspondance à la limite d'un mot.|  
|`qu`|Mettre en correspondance la sous-chaîne « qu ».|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
  
## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
- [Options des expressions régulières](regular-expression-options.md)
