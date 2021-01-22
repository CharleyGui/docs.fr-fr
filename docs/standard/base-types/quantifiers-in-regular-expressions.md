---
title: quantificateurs dans les expressions régulières
description: En savoir plus sur les quantificateurs d’expressions régulières, qui spécifient le nombre d’instances d’un caractère, d’un groupe ou d’une classe de caractères devant être présentes dans l’entrée à mettre en correspondance.
ms.date: 03/30/2017
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
ms.openlocfilehash: 5bee54d24726de1a904254dbd33d6d9be539ae09
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692927"
---
# <a name="quantifiers-in-regular-expressions"></a>quantificateurs dans les expressions régulières

Les quantificateurs spécifient le nombre d’instances d’un caractère, groupe ou classe de caractères devant être présentes dans l’entrée pour qu’une correspondance soit trouvée.  Le tableau suivant répertorie les quantificateurs pris en charge par .NET.  
  
|Quantificateur gourmand|Quantificateur paresseux|Description|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Mettre en correspondance zéro occurrence ou plus.|  
|`+`|`+?`|Mettre en correspondance une ou plusieurs occurrences.|  
|`?`|`??`|Mettre en correspondance zéro ou une occurrence.|  
|`{`*n*`}`|`{`*n*`}?`|Mettre en correspondance exactement *n* occurrences.|  
|`{`*n*`,}`|`{`*n*`,}?`|Mettre en correspondance au moins *n* occurrences.|  
|`{`*n* `,` *m*`}`|`{`*n* `,` *m*`}?`|Mettre en correspondance entre *n* et *m* occurrences.|  
  
 Les quantités `n` et `m` sont des constantes entières. Habituellement, les quantificateurs sont gourmands ; ils obligent le moteur d’expression régulière à faire correspondre autant d’occurrences de modèles particuliers que possible. L’ajout du caractère `?` à un quantificateur le rend paresseux ; le moteur d’expression régulière fait alors correspondre aussi peu d’occurrences que possible. Pour une description complète de la différence entre quantificateurs gourmands et paresseux, consultez la section [Quantificateurs gourmands et paresseux](#Greedy) plus loin dans cette rubrique.  
  
> [!IMPORTANT]
> L’imbrication des quantificateurs (par exemple, comme le fait le modèle d’expression régulière `(a*)*`) peut augmenter le nombre de comparaisons que le moteur d’expression régulière doit exécuter, comme une fonction exponentielle du nombre de caractères dans la chaîne d’entrée. Pour plus d’informations sur ce comportement et ses solutions de contournement, consultez [Rétroaction](backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Quantificateurs d’expression régulière  

 Les sections suivantes présentent les quantificateurs pris en charge par les expressions régulières .NET.  
  
> [!NOTE]
> Si les caractères *, +, ?, { et } sont rencontrés dans un modèle d’expressions régulières, le moteur d’expression régulière les interprète comme des quantificateurs ou partie de constructions de quantificateur à moins qu’ils ne soient inclus dans une [classe de caractères](character-classes-in-regular-expressions.md). Pour les interpréter comme des caractères littéraux en dehors d’une classe de caractères, vous devez les placer dans une séquence d’échappement en les faisant précéder d’une barre oblique inverse. Par exemple, la chaîne `\*` dans un modèle d’expression régulière est interprétée comme un caractère astérisque (« \* ») littéral.  
  
### <a name="match-zero-or-more-times-"></a>Mettre en correspondance zéro occurrence ou plus : *  

 Le quantificateur `*` correspond zéro fois, ou plus, à l’élément qui précède. Il équivaut au quantificateur `{0,}`. `*` est un quantificateur gourmand dont l’équivalent paresseux est `*?`.  
  
 L’exemple suivant illustre cette expression régulière. Parmi les neuf groupes de chiffres de la chaîne d’entrée, cinq correspondent au modèle et quatre ( `95` , `929` , `9219` et `9919` ) ne le font pas.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`91*`|Mettre en correspondance un « 9 » suivi de zéro, ou plus, caractère « 1 ».|  
|`9*`|Mettre en correspondance zéro, ou plus, caractère « 9 ».|  
|`\b`|Terminer à une limite de mot.|  
  
### <a name="match-one-or-more-times-"></a>Mettre en correspondance un ou plusieurs chiffres : +  

 Le quantificateur `+` correspond une ou plusieurs fois à l’élément qui précède. Il équivaut à `{1,}`. `+` est un quantificateur gourmand dont l’équivalent paresseux est `+?`.  
  
 Par exemple, l’expression régulière `\ban+\w*?\b` tente d’établir une correspondance avec les mots entiers qui commencent par la lettre `a` suivie d’une ou de plusieurs instances de la lettre `n`. L’exemple suivant illustre cette expression régulière. L’expression régulière établit une correspondance avec les mots `an`, `annual`, `announcement` et `antique`, et pas avec les mots `autumn` et `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`an+`|Mettre en correspondance un « a » suivi d’un ou plusieurs caractères « n ».|  
|`\w*?`|Mettre en correspondance un caractère alphabétique zéro, une ou plusieurs fois, mais le moins de fois possible.|  
|`\b`|Terminer à une limite de mot.|  
  
### <a name="match-zero-or-one-time-"></a>Mettre en correspondance zéro ou une occurrence : ?  

 Le quantificateur `?` correspond zéro ou une fois à l’élément qui précède. Il équivaut à `{0,1}`. `?` est un quantificateur gourmand dont l’équivalent paresseux est `??`.  
  
 Par exemple, l’expression régulière `\ban?\b` tente d’établir une correspondance avec les mots entiers qui commencent par la lettre `a` suivie de zéro ou une instance de la lettre `n`. En d’autres termes, elle tente d’établir une correspondance avec les mots `a` et `an`. L’exemple suivant illustre cette expression régulière.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`an?`|Mettre en correspondance un « a » suivi de zéro ou un caractère « n ».|  
|`\b`|Terminer à une limite de mot.|  
  
### <a name="match-exactly-n-times-n"></a>Mettre en correspondance exactement n occurrences : {n}  

 Le `{`  `}` quantificateur n correspond à l’élément qui précède exactement *n* fois, où *n* est un entier. `{`*n* `}` est un quantificateur gourmand dont l’équivalent paresseux est `{` *n* `}?` .  
  
 Par exemple, l’expression régulière `\b\d+\,\d{3}\b` tente d’établir une correspondance avec une limite de mot suivie d’un ou de plusieurs chiffres décimaux suivis de trois chiffres décimaux suivis d’une limite de mot. L’exemple suivant illustre cette expression régulière.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`\,`|Mettre en correspondance une virgule.|  
|`\d{3}`|Mettre en correspondance trois chiffres décimaux.|  
|`\b`|Terminer à une limite de mot.|  
  
### <a name="match-at-least-n-times-n"></a>Mettre en correspondance au moins n occurrences : {n,}  

 Le `{`  `,}` quantificateur n correspond à l’élément qui précède au moins *n* fois, où *n* est un entier. `{`*n* `,}` est un quantificateur gourmand dont l’équivalent paresseux est `{` *n* `,}?` .  
  
 Par exemple, l’expression régulière `\b\d{2,}\b\D+` tente d’établir une correspondance avec une limite de mot suivie d’au moins deux chiffres suivis d’une limite de mot et d’un caractère non numérique. L’exemple suivant illustre cette expression régulière. L’expression régulière ne peut pas établir de correspondance avec l’expression `"7 days"`, car elle ne contient qu’un chiffre. En revanche, une correspondance est établie les expressions `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`\d{2,}`|Mettre en correspondance au moins deux chiffres décimaux.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
|`\D+`|Mettre en correspondance au moins un chiffre non décimal.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Mettre en correspondance entre n et m fois : {n, m}  

 Le `{` quantificateur *n* `,` *m* `}` correspond à l’élément qui précède au moins *n* fois, mais pas plus de *m* fois, où *n* et *m* sont des entiers. `{`*n* `,` *m* `}` est un quantificateur gourmand dont l’équivalent paresseux est `{` *n* `,` *m* `}?` .  
  
 Dans l’exemple suivant, l’expression régulière `(00\s){2,4}` tente d’établir une correspondance entre deux et quatre occurrences de deux zéros suivis d’un espace. Notez que la partie finale de la chaîne d’entrée inclut ce modèle cinq fois au lieu du maximum de quatre. Toutefois, seule la partie initiale de cette sous-chaîne (jusqu’à l’espace et la cinquième paire de zéros) correspond au modèle d’expression régulière.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Mettre en correspondance zéro occurrence ou plus (correspondance paresseuse) : *?  

 Le quantificateur `*?` établit zéro, une ou plusieurs correspondances avec l’élément qui précède, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand `*`.  
  
 Dans l’exemple suivant, l’expression régulière `\b\w*?oo\w*?\b` correspond à tous les mots qui contiennent la chaîne `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`\w*?`|Correspond à zéro, un ou plusieurs caractères alphabétiques, mais le moins de caractères possible.|  
|`oo`|Mettre en correspondance la chaîne « oo ».|  
|`\w*?`|Correspond à zéro, un ou plusieurs caractères alphabétiques, mais le moins de caractères possible.|  
|`\b`|Terminer sur une limite de mot.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Mettre en correspondance une ou plusieurs occurrences (correspondance paresseuse) : +?  

 Le quantificateur `+?` établit une ou plusieurs correspondances avec l’élément qui précède, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand `+`.  
  
 Par exemple, l’expression régulière `\b\w+?\b` établit une correspondance avec un ou plusieurs caractères séparés par des limites de mot. L’exemple suivant illustre cette expression régulière.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Mettre en correspondance zéro ou une occurrence (correspondance paresseuse) : ??  

 Le quantificateur `??` établit zéro ou une correspondance avec l’élément qui précède, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand `?`.  
  
 Par exemple, l’expression régulière `^\s*(System.)??Console.Write(Line)??\(??` tente d’établir une correspondance avec les chaînes « Console.Write » ou « Console.WriteLine ». La chaîne peut également comprendre « System. » avant « Console », et elle peut être suivie par une parenthèse ouvrante. Elle doit se trouver au début d’une ligne, mais peut être précédée d’un espace blanc. L’exemple suivant illustre cette expression régulière.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Mettre en correspondance le début du flux d’entrée.|  
|`\s*`|Correspond à zéro, un ou plusieurs espaces blancs.|  
|`(System.)??`|Mettre en correspondance zéro ou une occurrence de la chaîne « System. ».|  
|`Console.Write`|Mettre en correspondance la chaîne « Console.Write ».|  
|`(Line)??`|Mettre en correspondance zéro ou une occurrence de la chaîne « Line ».|  
|`\(??`|Mettre en correspondance zéro occurrence, ou plus, de la parenthèse ouvrante.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Mettre en correspondance exactement n occurrences (correspondance paresseuse) : {n}?  

 Le `{`  `}?` quantificateur n correspond exactement à l’élément qui précède `n` , où *n* est un entier. Il s’agit de l’équivalent paresseux du quantificateur gourmand `{` *n* `}` .  
  
 Dans l’exemple suivant, l’expression régulière `\b(\w{3,}?\.){2}?\w{3,}?\b` est utilisée pour identifier une adresse de site web. Notez qu’elle établit une correspondance avec « www.microsoft.com » et « msdn.microsoft.com », mais pas avec « mywebsite » ou « mycompany.com ».  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(\w{3,}?\.)`|Mettre en correspondance au moins 3 caractères alphabétiques, mais le moins de caractères possible, suivis d’un point ou d’un point final. Il s'agit du premier groupe de capture.|  
|`(\w{3,}?\.){2}?`|Mettre en correspondance le modèle dans le premier groupe deux fois, mais le moins de fois possible.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Mettre en correspondance au moins n occurrences (correspondance paresseuse) : {n,}?  

 Le `{`  `,}?` quantificateur n correspond à l’élément qui précède au moins `n` fois, où *n* est un entier, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand `{` *n* `,}` .  
  
 Pour obtenir une illustration, consultez l’exemple du `{` quantificateur *n* `}?` dans la section précédente. L’expression régulière de cet exemple utilise le `{`  `,}` quantificateur n pour faire correspondre une chaîne comportant au moins trois caractères suivis d’un point.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Mettre en correspondance entre n et m fois (correspondance paresseuse) : {n,m}?  

 Le `{` quantificateur *n* `,` *m* `}?` correspond à l’élément qui précède entre `n` et `m` heures, où *n* et *m* sont des entiers, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand `{` *n* `,` *m* `}` .  
  
 Dans l’exemple suivant, l’expression régulière `\b[A-Z](\w*?\s*?){1,10}[.!?]` correspond aux phrases qui contiennent entre un et dix mots. Elle établit une correspondance avec toutes les phrases de la chaîne d’entrée à l’exception d’une phrase qui contient 18 mots.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`[A-Z]`|Mettre en correspondance une majuscule de A à Z.|  
|`(\w*?\s*?)`|Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques, suivis d’un ou plusieurs espaces, mais le moins de fois possible. Il s’agit du premier groupe de capture.|  
|`{1,10}`|Mettre en correspondance le modèle précédent entre 1 et 10 fois.|  
|`[.!?]`|Mettre en correspondance un signe de ponctuation « . », « ! » ou « ? ».|  
  
<a name="Greedy"></a>

## <a name="greedy-and-lazy-quantifiers"></a>Quantificateurs gourmands et paresseux  

 De nombreux quantificateurs existent en deux versions :  
  
- Une version gourmande.  
  
     Un quantificateur gourmand essaie de correspondre à un élément autant de fois que possible.  
  
- Une version non gourmande (ou paresseuse).  
  
     Un quantificateur non gourmand essaie de correspondre à un élément aussi peu de fois que possible. Vous pouvez changer un quantificateur gourmand en quantificateur paresseux en ajoutant simplement un `?`.  
  
 Considérez une expression régulière simple censée extraire les quatre derniers chiffres d’une chaîne de nombres telle qu’un numéro de carte de crédit. La version de l’expression régulière qui utilise le quantificateur gourmand `*` est `\b.*([0-9]{4})\b`. Toutefois, si une chaîne contient deux nombres, cette expression régulière correspond uniquement aux quatre derniers chiffres du deuxième nombre, comme le montre l’exemple suivant.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 L’expression régulière ne parvient pas à établir de correspondance avec le premier nombre ; en effet, comme le quantificateur `*` tente d’établir une correspondance autant de fois que possible avec l’élément qui précède dans la totalité de la chaîne, il trouve une correspondance à la fin de celle-ci.  
  
 Il ne s’agit pas du comportement souhaité. Vous pouvez plutôt utiliser le quantificateur paresseux `*?` pour extraire les chiffres des deux nombres, comme le montre l’exemple suivant.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Dans la plupart des cas, les expressions régulières avec des quantificateurs gourmands et paresseux retournent les mêmes correspondances. Elles retournent le plus souvent des résultats différents quand elles sont utilisées avec le métacaractère (`.`) générique, qui correspond à n’importe quel caractère.  
  
## <a name="quantifiers-and-empty-matches"></a>Quantificateurs et correspondances vides  

 Les quantificateurs `*` , `+` et `{` *n* `,` *m* `}` et leurs équivalents paresseux ne se répètent jamais après une correspondance vide quand le nombre minimal de captures a été trouvé. Cette règle empêche les quantificateurs d’entrer dans des boucles infinies sur des correspondances de sous-expressions vides quand le nombre maximal de captures de groupe possibles est infini ou proche de l’infini.  
  
 Par exemple, le code suivant montre le résultat d’un appel de la méthode <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> avec le modèle d’expression régulière `(a?)*` qui correspond à zéro ou un caractère « a », zéro, une ou plusieurs fois. Notez que le seul groupe de capture capture chaque « a », ainsi que <xref:System.String.Empty?displayProperty=nameWithType>, mais qu’il n’existe aucune deuxième correspondance vide, car la première correspondance vide entraîne l’arrêt de la répétition du quantificateur.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Pour voir la différence pratique entre un groupe de capture qui définit un nombre minimal et un nombre maximal de captures et un groupe de capture qui définit un nombre fixe de captures, examinez les modèles d’expressions régulières `(a\1|(?(1)\1)){0,2}` et `(a\1|(?(1)\1)){2}`. Les deux expressions régulières se composent d’un seul groupe de capture, qui est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`(a\1`|Mettre en correspondance « a » avec la valeur du premier groupe capturé …|  
|<code>&#124;(?(1)</code>|… ou tester si le premier groupe capturé a été défini. (Notez que la construction `(?(1)` ne définit pas un groupe de capture.)|  
|`\1))`|Si le premier groupe capturé existe, établir une correspondance avec sa valeur. Si le groupe n’existe pas, le groupe correspond à <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 La première expression régulière essaie de correspondre à ce modèle entre zéro et deux fois ; la deuxième, exactement deux fois. Étant donné que le premier modèle atteint son nombre minimal de captures avec sa première capture de <xref:System.String.Empty?displayProperty=nameWithType>, il ne se répète jamais pour essayer d’établir une correspondance avec `a\1` ; le quantificateur `{0,2}` autorise uniquement les correspondances vides dans la dernière itération. En revanche, la seconde expression régulière établit une correspondance avec « a », car elle évalue `a\1` une deuxième fois ; le nombre minimal d’itérations, 2, entraîne la répétition du moteur après une correspondance vide.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
- [Rétroaction](backtracking-in-regular-expressions.md)
