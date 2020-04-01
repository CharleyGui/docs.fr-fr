---
title: Comportement d’expression régulière
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
ms.openlocfilehash: 288bf4256670d34c600e23618b62ad81866daadf
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523850"
---
# <a name="details-of-regular-expression-behavior"></a>Comportement détaillé des expressions régulières

Le moteur d’expression régulière du .NET Framework est un analyseur d’expression régulière rétroactive qui incorpore un moteur NFA (Nondeterministic Finite Automaton) tel que celui utilisé par Perl, Python, Emacs et Tcl. Cette particularité le distingue des moteurs d’expression régulière pure DFA (Deterministic Finite Automaton) plus rapides, mais plus limités, comme ceux d’awk, egrep ou lex. Elle le distingue également des moteurs NFA POSIX standardisés, mais plus lents. La section suivante décrit les trois types de moteurs d’expression régulière et explique pourquoi les expressions régulières dans le .NET Framework sont implémentées à l’aide d’un moteur NFA classique.

## <a name="benefits-of-the-nfa-engine"></a>Avantages du moteur NFA

 Quand les moteurs DFA exécutent des critères spéciaux, leur ordre de traitement est piloté par la chaîne d’entrée. Les moteurs commencent au début de la chaîne d’entrée et continuent de manière séquentielle pour déterminer si le caractère suivant correspond au modèle d’expression régulière. Ils peuvent garantir une correspondance avec la chaîne la plus longue possible. Étant donné qu’ils ne testent jamais le même caractère deux fois, les moteurs DFA ne prennent pas en charge la rétroaction. Toutefois, étant donné qu’un moteur DFA contient uniquement un état fini, il ne peut pas rechercher un modèle avec des références arrière, et comme il ne construit pas d’expansion explicite, il ne peut pas capturer de sous-expressions.

 Contrairement aux moteurs DFA, quand les moteurs NFA classiques exécutent des critères spéciaux, leur ordre de traitement est piloté par le modèle d’expression régulière. Lorsqu’il traite un élément de langage particulier, le moteur utilise une correspondance gourmande ; autrement dit, il cherche la chaîne d’entrée la plus longue possible. Mais il enregistre également son état après avoir trouvé la correspondance correcte d’une sous-expression. Si une correspondance finit par échouer, le moteur peut revenir à un état enregistré pour tenter d’autres correspondances. Ce processus consistant à abandonner une correspondance réussie de sous-expression pour que les éléments de langage ultérieurs dans l’expression régulière puissent également correspondre est appelé *rétroaction*. Les moteurs NFA utilisent la rétroaction pour tester toutes les expansions possibles d’une expression régulière dans un ordre spécifique et accepter la première correspondance. Comme un moteur NFA classique construit une expansion spécifique de l’expression régulière pour obtenir une correspondance correcte, il peut capturer des correspondances de sous-expressions et des références arrière correspondantes. Toutefois, comme un moteur NFA classique utilise la rétroaction, il peut visiter le même état plusieurs fois s’il y parvient par différents chemins. Par conséquent, il peut s’exécuter lentement de façon exponentielle dans le pire des cas. Comme un moteur NFA classique accepte la première correspondance trouvée, il peut également en négliger d’autres (éventuellement plus longues).

 Les moteurs NFA POSIX sont comme les moteurs NFA classiques, sauf qu’ils poursuivent la rétroaction jusqu’à garantir qu’ils ont trouvé la correspondance la plus longue possible. Ainsi, un moteur NFA POSIX est plus lent qu’un moteur NFA classique. Quand vous utilisez un moteur NFA POSIX, vous ne pouvez pas favoriser une correspondance plus courte au détriment d’une plus longue en modifiant l’ordre de la recherche rétroactive.

 Les moteurs NFA classiques ont la préférence des programmeurs, car ils offrent un meilleur contrôle sur la mise en correspondance de chaînes que les moteurs DFA ou NFA POSIX. Même si, dans le pire des cas, ils peuvent s’exécuter lentement, vous pouvez les amener à trouver des correspondances sur des durées linéaires ou polynomiales à l’aide de modèles qui réduisent les ambiguïtés et limitent la rétroaction. En d’autres termes, bien que les moteurs NFA échangent des performances pour la puissance et la flexibilité, dans la plupart des cas, ils offrent de bonnes performances acceptables si une expression régulière est bien écrite et évite les cas dans lesquels le retour en arrière dégrade les performances de façon exponentielle.

> [!NOTE]
> Pour plus d’informations sur la baisse des performances due à la rétroaction excessive et sur les moyens de créer une expression régulière pour y remédier, consultez [Rétroaction](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).

## <a name="net-framework-engine-capabilities"></a>.NET Capacités de moteur-cadre

 Pour tirer parti des avantages d’un moteur NFA classique, le moteur d’expression régulière du .NET Framework inclut un ensemble complet de constructions pour permettre aux programmeurs de diriger le moteur de rétroaction. Ces constructions peuvent être utilisées pour rechercher des correspondances plus rapidement ou pour favoriser des expansions spécifiques par rapport à d’autres.

 Les autres fonctionnalités du moteur d’expression régulière du .NET Framework sont les suivantes :

- Quantificateurs paresseux: `??`, `*?` `+?`, , `{` *n*`,`*m*`}?`. Ces constructions indiquent au moteur de rétroaction de rechercher d’abord le nombre minimal de répétitions. Par opposition, les quantificateurs gourmands ordinaires essaient de trouver d’abord le nombre maximal de répétitions. L’exemple suivant illustre la différence entre les deux. Une expression régulière correspond à une phrase se terminant par un nombre qu’un groupe de capture est destiné à extraire. L’expression régulière `.+(\d+)\.` inclut le quantificateur gourmand `.+`, qui amène le moteur d’expression régulière à capturer uniquement le dernier chiffre du nombre. Par opposition, l’expression régulière `.+?(\d+)\.` inclut le quantificateur paresseux `.+?`, qui amène le moteur d’expression régulière à capturer le nombre entier.

     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]

     Les versions gourmande et paresseuse de cette expression régulière sont définies comme indiqué dans le tableau suivant :

    |Modèle|Description|
    |-------------|-----------------|
    |`.+` (quantificateur gourmand)|Mettre en correspondance au moins une occurrence de n’importe quel caractère. Le moteur d’expression régulière recherche alors la chaîne entière, puis effectue une rétroaction si nécessaire pour trouver le reste du modèle.|
    |`.+?` (quantificateur paresseux)|Mettre en correspondance au moins une occurrence de n’importe quel caractère, mais une quantité la plus petite possible.|
    |`(\d+)`|Mettre en correspondance au moins un caractère numérique et l’assigner au premier groupe de capture.|
    |`\.`|Mettre en correspondance un point.|

     Pour plus d'informations sur les quantificateurs paresseux, voir [Quantificateurs](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).

- Lookahead positif: `(?=` *sous-expression*`)`. Cette fonctionnalité permet au moteur de rétroaction de revenir au même endroit dans le texte après avoir mis en correspondance une sous-expression. Elle s’avère utile pour effectuer une recherche dans le texte en vérifiant plusieurs modèles qui démarrent à la même position. Elle permet également au moteur de vérifier qu’une sous-chaîne existe à la fin de la correspondance sans inclure cette sous-chaîne dans le texte correspondant. L’exemple suivant utilise la préanalyse positive pour extraire les mots d’une phrase qui ne sont pas suivis de symboles de ponctuation.

     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]

     L'expression régulière `\b[A-Z]+\b(?=\P{P})` est définie comme indiqué dans le tableau suivant.

    |Modèle|Description|
    |-------------|-----------------|
    |`\b`|Commencer la correspondance à la limite d'un mot.|
    |`[A-Z]+`|Mettre en correspondance un caractère alphabétique une ou plusieurs fois. Cette comparaison ne respecte pas la casse car la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.|
    |`\b`|Terminer la correspondance à la limite d'un mot.|
    |`(?=\P{P})`|Préanalyser pour déterminer si le caractère suivant est un symbole de ponctuation. Dans la négative, la correspondance réussit.|

     Pour plus d’informations sur les assertions de préanalyse positive, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Lookahead négatif: `(?!` *sous-expression*`)`. Cette fonctionnalité ajoute la possibilité de mettre en correspondance une expression uniquement si une sous-expression ne correspond pas. Elle s’avère particulièrement efficace pour affiner une recherche, car il est souvent plus simple de fournir une expression pour un cas à éliminer qu’une expression pour les cas à inclure. Par exemple, il est difficile d’écrire une expression pour les mots qui ne commencent pas par « non ». L’exemple suivant utilise la préanalyse négative pour les exclure.

     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]

     Le modèle d'expression régulière `\b(?!non)\w+\b` est défini comme indiqué dans le tableau suivant.

    |Modèle|Description|
    |-------------|-----------------|
    |`\b`|Commencer la correspondance à la limite d'un mot.|
    |`(?!non)`|Préanalyser pour garantir que la chaîne actuelle ne commence pas par « non ». Si c’est le cas, la correspondance échoue.|
    |`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|
    |`\b`|Terminer la correspondance à la limite d'un mot.|

     Pour plus d’informations sur les assertions de préanalyse négative, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Évaluation conditionnelle: `(?(` *expression*`)` `(?(`*oui*`|`*non* `)` et *nom*`)`*oui*`|`*non*`)`, lorsque *l’expression* est une sous-expression pour correspondre, le *nom* est le nom d’un groupe de capture, *oui* est la chaîne à assortir si *l’expression* est assortie ou le *nom* est un valide, non vide groupe capturé, et *non* est la sous-expression pour correspondre si *l’expression* n’est pas appariée ou le *nom* n’est pas un valide, non vide groupe capturé. Grâce à cette fonctionnalité, le moteur peut rechercher à l’aide de plusieurs autres modèles, selon le résultat d’une correspondance de sous-expression précédente ou le résultat d’une assertion de largeur nulle. Cette fonctionnalité permet une forme plus puissante de référence arrière qui permet, par exemple, de rechercher une sous-expression en fonction d’une sous-expression précédente trouvée. L’expression régulière utilisée dans l’exemple suivant trouve les paragraphes destinés à une utilisation à la fois interne et publique. Les paragraphes destinés à un usage interne uniquement commencent par une balise `<PRIVATE>`. Le modèle d’expression régulière `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` utilise une évaluation conditionnelle pour assigner le contenu des paragraphes destinés à une utilisation publique et interne à des groupes de capture distincts. Ces paragraphes peuvent ensuite être gérés différemment.

     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]

     Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

    |Modèle|Description|
    |-------------|-----------------|
    |`^`|Commencer la correspondance au début d’une ligne.|
    |`(?<Pvt>\<PRIVATE\>\s)?`|Mettre en correspondance zéro ou une occurrence de la chaîne `<PRIVATE>` suivie d’un espace blanc. Assigner la correspondance à un groupe de capture nommé `Pvt`.|
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Si le groupe de capture `Pvt` existe, mettre en correspondance une ou plusieurs occurrences d’un ou plusieurs caractères de mot suivis de zéro ou un séparateur de ponctuation suivi d’un espace blanc. Assigner la sous-chaîne au premier groupe de capture.|
    |<code>&#124;((\w+\p{P}?\s)+))</code>|Si le groupe de capture `Pvt` n’existe pas, mettre en correspondance une ou plusieurs occurrences d’un ou plusieurs caractères de mot suivis de zéro ou un séparateur de ponctuation suivi d’un espace blanc. Assigner la sous-chaîne au troisième groupe de capture.|
    |`\r?$`|Mettre en correspondance la fin d’une ligne ou la fin de la chaîne.|

     Pour plus d’informations sur l’évaluation conditionnelle, consultez [Constructions d’alternative](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).

- Équilibrer les définitions de groupe `(?<`: *nom1*`-`*2* `>` *sous-expression*`)`. Cette fonctionnalité permet au moteur d’expression régulière d’effectuer un suivi des constructions imbriquées telles que les parenthèses ou les crochets ouvrants et fermants. Pour obtenir un exemple, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Groupes atomiques : `(?>` *sousexpression*`)`. Cette fonctionnalité permet au moteur de rétroaction de garantir qu’une sous-expression correspond uniquement à la première correspondance trouvée pour cette sous-expression, comme si l’expression s’exécutait indépendamment de l’expression qui la contient. Si vous n’utilisez pas cette construction, les recherches rétroactives à partir de la plus grande expression peuvent modifier le comportement d’une sous-expression. Par exemple, l’expression `(a+)\w` régulière correspond à un ou plusieurs caractères « a », ainsi qu’un personnage de mot qui suit la séquence de « a » caractères, et attribue la séquence de « a » caractères au premier groupe de capture. Toutefois, si le caractère final de la chaîne d’entrée `\w` est également un « a », il est égalé par l’élément linguistique et n’est pas inclus dans le groupe capturé.

     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]

     L’expression régulière `((?>a+))\w` empêche ce comportement. Étant donné que tous les caractères « a » consécutifs sont trouvés sans rétroaction, le premier groupe de capture inclut tous les caractères « a » consécutifs. Si les caractères « a » ne sont pas suivis d’au moins un caractère autre que « a », la correspondance échoue.

     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]

     Pour plus d’informations sur les groupes [atomiques, voir Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- La mise en correspondance de droite à gauche est spécifiée en fournissant l’option <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> à une méthode de mise en correspondance de constructeur de classe ou d’instance statique <xref:System.Text.RegularExpressions.Regex>. Cette fonctionnalité s’avère utile lors de la recherche de droite à gauche au lieu de gauche à droite, ou dans les cas où il est plus efficace de commencer une correspondance dans la partie droite du modèle plutôt que la partie gauche. Comme l’illustre l’exemple suivant, l’utilisation de la mise en correspondance de droite à gauche peut modifier le comportement des quantificateurs gourmands. L’exemple effectue deux recherches d’une phrase qui se termine par un nombre. La recherche de gauche à droite qui utilise le quantificateur gourmand `+` trouve l’un des six chiffres dans la phrase, tandis que la recherche de droite à gauche trouve les six chiffres. Pour une description du modèle d’expression régulière, voir l’exemple qui illustre les quantificateurs paresseux plus tôt dans cette section.

     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]

     Pour plus d’informations sur la mise en correspondance de droite à gauche, consultez [Options des expressions régulières](../../../docs/standard/base-types/regular-expression-options.md).

- Lookbehind positif et `(?<=`négatif : *sousexpression* `)` pour `(?<!`lookbehind positif, et *sousexpression* `)` pour lookbehind négatif. Cette fonctionnalité est semblable à la préanalyse décrite précédemment dans cette rubrique. Comme le moteur d’expression régulière autorise une mise en correspondance complète de droite à gauche, les expressions régulières autorisent les postanalyses illimitées. La postanalyse positive et négative peut également servir à éviter d’imbriquer des quantificateurs lorsque la sous-expression imbriquée est un sur-ensemble d’une expression externe. Les expressions régulières comportant ces quantificateurs imbriqués offrent souvent des performances médiocres. L’exemple suivant vérifie qu’une chaîne commence et se termine par un caractère alphanumérique et que tout autre caractère contenu dans la chaîne fait partie d’un sur-ensemble plus grand. Il forme une partie de l’expression régulière utilisée pour valider des adresses e-mail. Pour plus d’informations, consultez [Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]

     L'expression régulière ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` est définie comme indiqué dans le tableau suivant.

    |Modèle|Description|
    |-------------|-----------------|
    |`^`|Commencer la correspondance au début de la chaîne.|
    |`[A-Z0-9]`|Mettre en correspondance n’importe quel caractère numérique ou alphanumérique. (La comparaison respecte la casse.)|
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Assortissez zéro ou plus d’occurrences de n’importe quel personnage de mot, ou de l’un des caractères suivants : -, !,, $, &, ', ., \*,, /, ', ', ', &#96;, ', &#124;, ou '.|
    |`(?<=[A-Z0-9])`|Postanalyser jusqu’au caractère précédent, qui doit être numérique ou alphanumérique. (La comparaison respecte la casse.)|
    |`$`|Termine la correspondance à la fin de la chaîne.|

     Pour plus d’informations sur la postanalyse positive et négative, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="related-articles"></a>Articles connexes

|Intitulé|Description|
|-----------|-----------------|
|[Rétroaction](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Fournit des informations sur la manière dont la rétroaction d’expression régulière se ramifie pour trouver d’autres correspondances.|
|[Compilation et réutilisation](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Fournit des informations sur la compilation et la réutilisation des expressions régulières pour augmenter les performances.|
|[Sécurité des threads](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Fournit des informations sur la sécurité des threads d’expression régulière et explique quand vous devez synchroniser l’accès aux objets d’expression régulière.|
|[Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)|Fournit une vue d’ensemble de l’aspect du langage de programmation des expressions régulières.|
|[Modèle objet d'expression régulière](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Fournit des informations et des exemples de code illustrant l’utilisation des classes d’expression régulière.|
|[Langage des expressions régulières - Aide-mémoire](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Fournit des informations sur le jeu de caractères, d’opérateurs et de constructions permettant de définir des expressions régulières.|

## <a name="reference"></a>Référence

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
