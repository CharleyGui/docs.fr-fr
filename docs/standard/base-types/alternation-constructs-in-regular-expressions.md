---
title: Constructions d’alternative dans les expressions régulières .NET
description: Découvrez comment utiliser des constructions d’alternative pour la correspondance conditionnelle dans les expressions régulières.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 506c1cdeb577452628d67ab00df20dd30881f406
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495432"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Constructions d'alternative dans les expressions régulières

Les constructions d'alternative modifient une expression régulière pour permettre la correspondance de type inclusif/exclusif ou conditionnelle. .NET prend en charge trois constructions d’alternative :

- [Utilisation des critères spéciaux avec &#124;](#Either_Or)
- [Correspondance conditionnelle avec (?(expression)oui&#124;non)](#Conditional_Expr)
- [Correspondance conditionnelle selon un groupe capturé valide](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a>Utilisation des critères spéciaux avec &#124;

Vous pouvez utiliser la barre verticale (`|`) pour mettre en correspondance un modèle d’une série, dans laquelle le caractère `|` sépare chaque modèle.

Tout comme la classe de caractères positive, le caractère `|` peut être utilisé pour mettre en correspondance n’importe quel nombre de caractères uniques. L’exemple suivant utilise une classe de caractères positive et des critères spéciaux de type inclusif/exclusif avec le caractère `|` pour trouver des occurrences des mots « gray » ou « grey » dans une chaîne. Dans ce cas, le caractère `|` produit une expression régulière qui est plus détaillée.

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

L’expression régulière qui utilise le `|` caractère, `\bgr(a|e)y\b` , est interprétée comme indiqué dans le tableau suivant :

|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`gr`|Mettre en correspondance les caractères « gr ».|  
|<code>(a&#124;e)</code>|Mettre en correspondance un « a » ou un « e ».|  
|`y\b`|Mettre en correspondance un « y » à la limite d'un mot.|  

Le caractère `|` peut également être utilisé pour effectuer une correspondance de type inclusif/exclusif avec plusieurs caractères ou sous-expressions, qui peuvent inclure toute combinaison de caractère littéraux et éléments de langage d’expressions régulières. (La classe de caractères ne fournit pas cette fonctionnalité.) L’exemple suivant utilise le `|` caractère pour extraire un numéro de sécurité sociale (SSN) américain, qui est un nombre de 9 chiffres au format *DDD* - *JJ* - *dddd*, ou un numéro d’identification d’employeur (Ein) américain, qui est un nombre de 9 chiffres au format *JJ* - *ddddddd*.

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

L’expression régulière `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` est interprétée comme indiqué dans le tableau suivant :
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Mettre en correspondance l'un ou l'autre des éléments suivants : deux chiffres décimaux suivis d'un trait d'union suivi de sept chiffres décimaux, ou alors trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a>Correspondance conditionnelle avec une expression

Cet élément de langage tente de mettre en correspondance un modèle parmi deux fournis selon qu'il parvient ou non à mettre en correspondance un modèle initial. Sa syntaxe est la suivante :  

`(?(`*expression* `)` *Oui* `|` *non*`)`

où *expression* est le modèle initial à faire correspondre, *Oui* est le modèle à faire correspondre si l' *expression* est mise en correspondance, et *no* est le modèle facultatif à faire correspondre si l' *expression* n’est pas mise en correspondance. Le moteur d’expression régulière traite l’*expression* comme une assertion de largeur nulle ; c’est-à-dire que le moteur d’expression régulière n’avance pas dans le flux d’entrée après avoir évalué l’*expression*. Par conséquent, cette construction est équivalente à la suivante :

`(?(?=`*expression* `)` *Oui* `|` *non*`)`

où `(?=` *expression* `)` est une construction d’assertion de largeur nulle. (Pour plus d’informations, consultez [constructions de regroupement](grouping-constructs-in-regular-expressions.md).) Étant donné que le moteur des expressions régulières interprète l' *expression* comme une ancre (assertion de largeur nulle), l' *expression* doit être une assertion de largeur nulle (pour plus d’informations, consultez [ancres](anchors-in-regular-expressions.md)) ou une sous-expression qui est également contenue dans *Oui*. Sinon, aucune correspondance ne peut être établie avec le modèle *oui* .  
  
> [!NOTE]
> Si *expression* est un groupe de capture nommé ou numéroté, la construction alternative est interprétée comme un test de capture. Pour plus d’informations, consultez la section suivante, [Correspondance conditionnelle basée sur un groupe de capture valide](#Conditional_Group). En d'autres termes, le moteur des expressions régulières ne tente pas de mettre en correspondance la sous-chaîne capturée, mais à la place teste la présence ou l'absence du groupe.  
  
L’exemple suivant est une variante de celui donné dans la section [Critères spéciaux de type inclusif/exclusif avec &#124;](#Either_Or). Il utilise la mise en correspondance conditionnelle pour déterminer si les trois premiers caractères après une limite de mot se composent de deux chiffres suivis d'un trait d'union. Si c'est le cas, il tente de mettre en correspondance un numéro d'identification de l'employeur (EIN) américain. Si ce n'est pas le cas, il tente de mettre en correspondance un numéro de sécurité sociale (SSN) américain.

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

Le modèle d’expression régulière `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` est interprété comme indiqué dans le tableau suivant :

|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(?(\d{2}-)`|Déterminer si les trois caractères suivants se composent de deux chiffres suivis d'un trait d'union.|  
|`\d{2}-\d{7}`|Si le modèle précédent correspond, mettre en correspondance deux chiffres suivis d'un trait d'union suivi de sept chiffres.|  
|`\d{3}-\d{2}-\d{4}`|Si le modèle ne correspond pas, faire correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Correspondance conditionnelle selon un groupe capturé valide

Cet élément de langage essaie de faire correspondre l'un de deux modèles selon qu'il peut correspondre à un groupe capturé spécifié. Sa syntaxe est la suivante :

`(?(` *name* `)` *oui* `|` *non* `)`

ou

`(?(` *nombre* `)` *oui* `|` *non* `)`

où *nom* est le nom et *numéro* est le numéro d’un groupe de capture, *Oui* est l’expression à faire correspondre si *nom* ou *nombre* a une correspondance et *non* est l’expression facultative à faire correspondre si ce n’est pas le cas.

Si le *nom* ne correspond pas au nom d'un groupe de capture utilisé dans le modèle d'expression régulière, la construction alternative est interprétée comme un test d'expression, comme expliqué dans la section précédente. En général, cela signifie que l' *expression* prend la valeur `false` . Si le *nombre* ne correspond pas à un groupe de capture numéroté utilisé dans le modèle d'expression régulière, le moteur des expressions régulières lève une <xref:System.ArgumentException>.

L’exemple suivant est une variante de celui donné dans la section [Critères spéciaux de type inclusif/exclusif avec &#124;](#Either_Or). Il utilise un groupe de capture nommé `n2` qui se compose de deux chiffres suivis d'un trait d'union. La construction d'alternative tests si ce groupe de capture a été mis en correspondance dans la chaîne d'entrée. Si c'est le cas, la construction alternative essaie de mettre en correspondance les sept derniers chiffres d'un numéro d'identification de l'employeur (EIN) américain. Si ce n'est le cas, il essaie de faire correspondre un numéro de sécurité sociale (SSN) américain.

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

Le modèle d’expression régulière `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` est interprété comme indiqué dans le tableau suivant :

|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(?<n2>\d{2}-)?`|Mettre en correspondance zéro ou une occurrence de deux chiffres suivis d'un trait d'union. Nommer ce groupe de capture `n2`.|  
|`(?(n2)`|Testez si `n2` a été mis en correspondance dans la chaîne d'entrée.|  
|`\d{7}`|Si `n2` a été mis en correspondance, faites correspondre sept chiffres décimaux.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Si `n2` ne correspondait pas, faites correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  

Une variation de cet exemple qui utilise un groupe numéroté au lieu d'un groupe nommé est illustrée dans l'exemple suivant. Son modèle d'expression régulière est `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
