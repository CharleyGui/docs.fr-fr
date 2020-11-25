---
title: Rétroaction dans les expressions régulières .NET
description: Apprenez à contrôler la rétroaction dans la mise en correspondance de modèle d’expression régulière.
ms.date: 11/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET regular expressions, backtracking
- alternative matching patterns
- optional matching patterns
- searching with regular expressions, backtracking
- pattern-matching with regular expressions, backtracking
- backtracking
- regular expressions [.NET], backtracking
- strings [.NET], regular expressions
- parsing text with regular expressions, backtracking
ms.assetid: 34df1152-0b22-4a1c-a76c-3c28c47b70d8
ms.openlocfilehash: 5c6d9d2e048c2dd89cf18ff7148050ddb6813f40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699701"
---
# <a name="backtracking-in-regular-expressions"></a>Rétroaction dans les expressions régulières

La rétroaction se produit quand un modèle d’expression régulière contient des [quantificateurs](quantifiers-in-regular-expressions.md) ou des [constructions d’alternative](alternation-constructs-in-regular-expressions.md) facultatifs, et que le moteur d’expression régulière retourne à un état enregistré précédent pour poursuivre la recherche d’une correspondance. La rétroaction est essentielle à la puissance des expressions régulières ; elle permet aux expressions d'être puissantes et flexibles et de correspondre à des modèles très complexes. Cependant, cette puissance a un coût. La rétroaction est souvent le facteur le plus important qui affecte les performances du moteur des expressions régulières. Heureusement, le développeur contrôle le comportement du moteur des expressions régulières et comment il utilise la rétroaction. Cette rubrique explique comment la rétroaction fonctionne et comment elle peut être activée.  
  
> [!NOTE]
> En général, un automate fini non déterministe comme le moteur d’expression régulière de .NET fait peser la responsabilité de la conception d’expressions régulières efficaces et rapides sur le développeur.  

## <a name="linear-comparison-without-backtracking"></a>Comparaison linéaire sans rétroaction  

 Si un modèle d'expression régulière ne possède pas de quantificateur facultatif ou de construction d'alternative, le moteur des expressions régulières s'exécute en temps linéaire. Autrement dit, une fois que le moteur des expressions régulières correspond au premier élément de langage dans le modèle avec du texte dans la chaîne d'entrée, il tente de correspondre à l'élément de langage suivant dans le modèle avec le caractère ou le groupe suivant de caractères dans la chaîne d'entrée. Cela se poursuit jusqu'à ce que la correspondance réussisse ou échoue. Dans les deux cas, le moteur des expressions régulières avance d'un caractère à la fois dans la chaîne d'entrée.  
  
 L'exemple suivant illustre cette situation. L'expression régulière `e{2}\w\b` recherche deux occurrences de la lettre « e » suivie de n'importe quel caractère de mot suivi d'une limite de mot.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 Bien que cette expression régulière inclue le quantificateur `{2}`, elle est évaluée de façon linéaire. Le moteur des expressions régulières ne revient pas en arrière, car `{2}` n'est pas un quantificateur facultatif ; il spécifie un nombre exact et pas un nombre variable de fois que la sous-expression précédente doit correspondre. Par conséquent, le moteur des expressions régulières tente de correspondre au modèle d'expression régulière avec la chaîne d'entrée comme indiqué dans le tableau suivant.  
  
|Opération|Position dans le modèle|Position dans la chaîne|Résultats|  
|---------------|-------------------------|------------------------|------------|  
|1|e|"besoin d'un roseau" (index 0)|Pas de correspondance.|  
|2|e|"esoin d'un roseau" (index 1)|Correspondance possible.|  
|3|e{2}|"soin d'un roseau" (index 2)|Correspondance possible.|  
|4|\w|"oin d'un roseau" (index 3)|Correspondance possible.|  
|5|\b|"in d'un roseau" (index 4)|Échecs de correspondance possibles.|  
|6|e|"soin d'un roseau" (index 2)|Correspondance possible.|  
|7|e{2}|"oin d'un roseau" (index 3)|Échecs de correspondance possibles.|  
|8|e|"oin d'un roseau" (index 3)|Échec de la correspondance.|  
|9|e|"in d'un roseau" (index 4)|Pas de correspondance.|  
|10|e|"n d'un roseau" (index 5)|Pas de correspondance.|  
|11|e|"d'un roseau" (index 6)|Pas de correspondance.|  
|12|e|" un roseau" (index 7)|Pas de correspondance.|  
|13|e|"un roseau" (index 8)|Pas de correspondance.|  
|14|e|" roseau" (index 9)|Pas de correspondance.|  
|15|e|"roseau" (index 10)|Pas de correspondance|  
|16|e|"seau" (index 11)|Correspondance possible.|  
|17|e{2}|"au" (index 12)|Correspondance possible.|  
|18|\w|"u" (index 13)|Correspondance possible.|  
|19|\b|"" (index 14)|Correspondance|  
  
 Si un modèle d'expression régulière n'inclut aucun quantificateur facultatif ou construction d'alternative, le nombre maximal de comparaisons requises pour correspondre au modèle d'expression régulière avec la chaîne d'entrée équivaut à peu près au nombre de caractères dans la chaîne d'entrée. Dans ce cas, le moteur des expressions régulières utilise 19 comparaisons pour identifier les correspondances possibles dans cette chaîne de 13 caractères.  En d'autres termes, le moteur des expressions régulières s'exécute en temps quasi linéaire s'il ne contient pas de quantificateur facultatif ou de construction d'alternative.

## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>Rétroaction avec des quantificateurs facultatifs ou des constructions d'alternative  

 Lorsqu'une expression régulière inclut des quantificateurs facultatifs ou des constructions d'alternative, l'évaluation de la chaîne d'entrée n'est plus linéaire. Les critères spéciaux avec un moteur NFA sont pilotés par les éléments de langage dans l'expression régulière et non par des caractères de correspondance dans la chaîne d'entrée. Par conséquent, le moteur des expressions régulières tente de correspondre complètement aux sous-expressions facultatives ou alternatives. Lorsqu'il avance à l'élément de langage suivant dans la sous-expression et que la correspondance échoue, le moteur des expressions régulières peut abandonner une partie de sa correspondance trouvée et retourner à un état enregistré précédent afin de mettre en correspondance l'expression régulière dans son ensemble avec la chaîne d'entrée. Ce processus de retour à un état enregistré précédent pour rechercher une correspondance est appelé rétroaction.  
  
 Considérons, par exemple, le modèle d'expression régulière `.*(es)`, qui correspond aux caractères « es » et tous caractères qui précèdent. Comme l'exemple suivant l'indique, si la chaîne d'entrée est « Des services essentiels sont fournis par les expressions régulières. », le modèle correspond à la chaîne entière jusqu'à « es » dans « expressions ».  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 Pour cela, le moteur des expressions régulières utilise la rétroaction comme suit :  
  
- Il établit une correspondance entre `.*` (qui correspond à zéro, une ou plusieurs occurrences d'un caractère) et la chaîne d'entrée entière.  
  
- Il tente de faire correspondre « e » dans le modèle d'expression régulière. Toutefois, il ne reste aucun caractère disponible pour la correspondance dans la chaîne d'entrée.  
  
- Il revient en arrière à la dernière correspondance trouvée, « Des services essentiels sont fournis par les expressions régulières » et tente de faire correspondre « e » avec le point à la fin de la phrase. La correspondance échoue.  
  
- Il continue à revenir en arrière à la correspondance précédente caractère après caractère jusqu'à ce qu'à ce que la sous-chaîne en correspondance provisoire soit « Des services essentiels sont fournis par le les expr ». Il compare ensuite le « e » dans le modèle avec le second « e » dans « expressions » et trouve une correspondance.  
  
- Il compare le « s » dans le modèle avec le « s » qui suit le « e » mis en correspondance (le premier « s » dans « expressions »). La correspondance réussit.  
  
 Lorsque vous utilisez la rétroaction, la mise en correspondance du modèle d'expression régulière avec la chaîne d'entrée, qui comporte 55 caractères, requiert 67 opérations de comparaison. En général, si un modèle d'expression régulière a une seule construction d'alternative ou un seul quantificateur facultatif, le nombre d'opérations de comparaison requises pour correspondre au modèle est supérieur au double du nombre de caractères dans la chaîne d'entrée.

## <a name="backtracking-with-nested-optional-quantifiers"></a>Rétroaction avec des quantificateurs facultatifs imbriqués  

 Le nombre d'opérations de comparaison requises pour correspondre à un modèle d'expression régulière peut augmenter de façon exponentielle si le modèle se compose d'un grand nombre de constructions d'alternative, s'il est constitué de constructions d'alternative imbriquées ou, le plus souvent, s'il inclut des quantificateurs facultatifs imbriqués. Par exemple, le modèle d'expression régulière `^(a+)+$` est conçu pour une correspondance avec une chaîne complète qui contient un ou plusieurs caractères « a ». L'exemple fournit deux chaînes d'entrée de longueurs identiques, mais seule la première chaîne correspond au modèle. La classe <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> est utilisée pour déterminer la durée de l'opération de correspondance.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 Comme la sortie de l'exemple indique, il a fallu presque deux fois plus de temps au moteur des expressions régulières pour constater qu'une chaîne d'entrée ne correspondait pas au modèle que pour identifier une chaîne correspondante. Cela est dû au fait qu'une correspondance infructueuse représente toujours le pire des scénarios. Le moteur des expressions régulières doit utiliser l'expression régulière pour suivre tous les chemins d'accès possibles dans les données avant qu'il puisse conclure que la correspondance est infructueuse, et les parenthèses imbriquées créent plusieurs chemins d'accès supplémentaires dans les données. Le moteur des expressions régulières conclut que la deuxième chaîne ne correspondait pas au modèle en procédant comme suit :  
  
- Il vérifie qu'il était au début de la chaîne, puis fait correspondre les cinq premiers caractères dans la chaîne avec le modèle `a+`. Il détermine ensuite qu'il n'y a aucun groupe supplémentaire de caractères « a » dans la chaîne. Enfin, il effectue en test pour déterminer la fin de la chaîne. Étant donné qu'il reste un caractère supplémentaire dans la chaîne, la correspondance échoue. Cette correspondance infructueuse requiert 9 comparaisons. Le moteur des expressions régulières enregistre également des informations d'état de ses correspondances de « a » (que nous appellerons correspondance 1), « aa » (correspondance 2), « aaa » (correspondance 3) et « aaaa » (correspondance 4).  
  
- Il revient à la correspondance 4 enregistrée précédemment. Il détermine qu'il y a un caractère « a » supplémentaire à assigner à un groupe capturé supplémentaire. Enfin, il effectue en test pour déterminer la fin de la chaîne. Étant donné qu'il reste un caractère supplémentaire dans la chaîne, la correspondance échoue. Cette correspondance infructueuse requiert 4 comparaisons. Jusqu'à présent, un total de 13 comparaisons ont été effectuées.  
  
- Il revient à la correspondance 3 enregistrée précédemment. Il détermine qu'il y a deux caractères « a » supplémentaires à assigner à un groupe capturé supplémentaire. Toutefois, le test de fin de chaîne échoue. Il revient ensuite à la correspondance 3 et tente de faire correspondre les deux caractères « a » supplémentaire dans deux groupes capturés supplémentaires. Le test de fin de chaîne échoue encore. Ces correspondances infructueuses requièrent 12 comparaisons. Jusqu'à présent, un total de 25 comparaisons ont été effectuées.  
  
 La comparaison de la chaîne d'entrée avec l'expression régulière continue de cette façon jusqu'à ce que le moteur des expressions régulières ait tenté toutes les combinaisons possibles des correspondances et conclue qu'il n'existe aucune correspondance. En raison des quantificateurs imbriqués, cette comparaison est une opération O (2 <sup>n</sup>) ou exponentielle, où *n* est le nombre de caractères dans la chaîne d’entrée. Cela signifie que dans le pire des cas, une chaîne d'entrée de 30 caractères requiert environ 1 073 741 824 comparaisons et une chaîne d'entrée de 40 caractères requiert environ 1 099 511 627 776 comparaisons. Si vous utilisez des chaînes de longueurs identiques ou supérieures, l'exécution des méthodes d'expression régulières peut prendre très longtemps lorsqu'elles traitent une entrée qui ne correspond pas au modèle d'expression régulière.

## <a name="controlling-backtracking"></a>Contrôle de la rétroaction  

 La rétroaction vous permet de créer des expressions régulières puissantes et flexibles. Toutefois, comme la section précédente l'indiquait, ces avantages peuvent s'accompagner de performances médiocres. Pour empêcher la rétroaction excessive, vous devez définir un intervalle de délai d'attente lorsque vous instanciez un objet <xref:System.Text.RegularExpressions.Regex> ou appelez une méthode de mise en correspondance statique d'expression régulière. Cette situation est présentée dans la section suivante. En outre, .NET prend en charge trois éléments de langage d’expression régulière qui limitent ou suppriment la rétroaction et qui prennent en charge des expressions régulières complexes avec peu ou pas de dégradation des performances : les [groupes atomiques](#atomic-groups), les [assertions de postanalyse](#lookbehind-assertions)et les [assertions de préanalyse](#lookahead-assertions). Pour plus d’informations sur chaque élément de langage, consultez [Grouping Constructs](grouping-constructs-in-regular-expressions.md).  

### <a name="defining-a-time-out-interval"></a>Définir un intervalle de délai d'attente  

 À partir de .NET Framework 4.5, vous pouvez définir un intervalle de délai d’attente qui représente la durée maximale pendant laquelle le moteur d’expression régulière recherche une correspondance avant d’abandonner la tentative et de lever une exception <xref:System.Text.RegularExpressions.RegexMatchTimeoutException>. Vous spécifiez l'intervalle de délai d'attente en donnant une valeur <xref:System.TimeSpan> au constructeur <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29> pour les expressions régulières d'instances. De plus, chaque méthode de mise en correspondance statique possède une surcharge avec un paramètre <xref:System.TimeSpan> qui vous permet de spécifier une valeur de délai d'attente. Par défaut, l'intervalle de délai d'attente est défini sur <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> et le moteur des expressions régulières n'expire pas.  
  
> [!IMPORTANT]
> Il est recommandé de toujours définir un intervalle de délai d'attente si votre expression régulière repose sur la restauration.  
  
 Une exception <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> indique que le moteur des expressions régulières n’a pas pu trouver de correspondance dans l’intervalle de délai d’attente spécifié, mais n’indique pas pourquoi l’exception a été levée. Cela peut provenir de la rétroaction excessive, mais il est possible que l'intervalle de délai d'attente était trop faible étant donné la charge système au moment où l'exception a été levée. Lorsque vous gérez l'exception, vous pouvez choisir d'abandonner d'autres correspondances avec la chaîne d'entrée ou augmenter l'intervalle de délai d'attente et de retenter l'opération de mise en correspondance.  
  
 Par exemple, le code suivant appelle le constructeur <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29> pour instancier un objet <xref:System.Text.RegularExpressions.Regex> avec un délai d'attente d'une seconde. Le modèle d'expression régulière `(a+)+$`, qui correspond à une ou plusieurs séquences d'un ou plusieurs caractères « a » à la fin d'une ligne, est soumis à une rétroaction excessive. Si une <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> est levée, l'exemple augmente la valeur du délai d'attente jusqu'à un intervalle maximal de trois secondes. Après cela, il abandonne la tentative pour mettre en correspondance le modèle.  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  

### <a name="atomic-groups"></a>Groupes atomiques

 L’élément de langage sous- `(?>` *expression* `)` supprime la rétroaction dans la sous-expression. Une fois qu’il a été mis en correspondance, il n’accorde aucune partie de sa correspondance à la rétroaction suivante. Par exemple, dans le modèle `(?>\w*\d*)1` , si le `1` ne peut pas être mis en correspondance, le n' `\d*` abandonnera aucune de ses correspondances, même si cela signifie qu’il autorisera la `1` correspondance avec. Les groupes atomiques peuvent aider à éviter les problèmes de performances associés aux correspondances ayant échoué.
  
 L'exemple suivant montre comment la suppression de la rétroaction améliore les performances lors de l'utilisation de quantificateurs imbriqués. Il mesure le temps nécessaire pour que le moteur des expressions régulières détermine qu'une chaîne d'entrée ne correspond pas à deux expressions régulières. La première expression régulière utilise la rétroaction pour tenter de mettre en correspondance une chaîne qui contient une ou plusieurs occurrences d'un ou plusieurs chiffres hexadécimaux, suivi d'un signe deux-points, suivi d'un ou plusieurs chiffres hexadécimaux, suivi de deux signes deux-points. La seconde expression régulière est identique à la première, à ceci près qu'elle désactive la rétroaction. Comme la sortie de l'exemple l'indique, l'amélioration des performances due à la désactivation de la rétroaction est considérable.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  

### <a name="lookbehind-assertions"></a>assertions de postanalyse  

 .NET comprend deux éléments de langage, sous- `(?<=` *expression* `)` et sous- `(?<!` *expression* `)` , qui correspondent au ou aux caractères précédents de la chaîne d’entrée. Les deux éléments de langage sont des assertions de largeur nulle ; c’est-à-dire qu’ils déterminent si le ou les caractères qui précèdent immédiatement le caractère actuel peuvent être mis en correspondance par la *sous-expression*, sans avancer ou utiliser la rétroaction.  
  
 `(?<=`sous- *expression* `)` est une assertion de postanalyse positive ; autrement dit, le ou les caractères situés avant la position actuelle doivent correspondre à la sous- *expression*. `(?<!`sous- *expression* `)` est une assertion de postanalyse négative ; autrement dit, le ou les caractères situés avant la position actuelle ne doivent pas correspondre à la sous- *expression*. Les assertions de postanalyse positive et négative sont très utiles quand la sous- *expression* est un sous-ensemble de la sous-expression précédente.  
  
 L'exemple suivant utilise deux modèles d'expressions régulières équivalents qui valident le nom d'utilisateur dans une adresse e-mail. Le premier modèle est sujet à des performances médiocres dues à une rétroaction excessive. Le second modèle modifie la première expression régulière en remplaçant un quantificateur imbriqué par une assertion de postanalyse positive. La sortie de l'exemple indique la durée d'exécution de la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> .  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 Le premier modèle d'expression régulière, `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`, est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Démarrer la correspondance au début de la chaîne.|  
|`[0-9A-Z]`|Mettre en correspondance un caractère alphanumérique. Cette comparaison ne respecte pas la casse, parce que la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .|  
|`[-.\w]*`|Mettre en correspondance zéro, une ou plusieurs occurrences d'un trait d'union, d'un point ou d'un caractère alphabétique.|  
|`[0-9A-Z]`|Mettre en correspondance un caractère alphanumérique.|  
|`([-.\w]*[0-9A-Z])*`|Mettre en correspondance zéro, une ou plusieurs occurrences de la combinaison de zéro ou plus traits d'union, points ou caractères alphabétiques, suivis d'un caractère alphanumérique. Il s'agit du premier groupe de capture.|  
|`@`|Mettre en correspondance une arobase (« \@ »).|  
  
 Le second modèle d'expression régulière, `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`, utilise une assertion de postanalyse positive. Il est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Démarrer la correspondance au début de la chaîne.|  
|`[0-9A-Z]`|Mettre en correspondance un caractère alphanumérique. Cette comparaison ne respecte pas la casse, parce que la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .|  
|`[-.\w]*`|Mettre en correspondance zéro, une ou plusieurs occurrences d'un trait d'union, d'un point ou d'un caractère alphabétique.|  
|`(?<=[0-9A-Z])`|Remonter au dernier caractère mis en correspondance et continuer la mise en correspondances si elle est alphanumérique. Notez que les caractères alphanumériques sont un sous-ensemble du jeu qui se compose de points, de traits d'union et de tous les caractères alphabétiques.|  
|`@`|Mettre en correspondance une arobase (« \@ »).|  

### <a name="lookahead-assertions"></a>assertions de préanalyse  

 .NET comprend deux éléments de langage, sous- `(?=` *expression* `)` et sous- `(?!` *expression* `)` , qui correspondent au ou aux caractères suivants dans la chaîne d’entrée. Les deux éléments de langage sont des assertions de largeur nulle ; c’est-à-dire qu’ils déterminent si le ou les caractères qui suivent immédiatement le caractère actuel peuvent être mis en correspondance par la *sous-expression*, sans avancer ou utiliser la rétroaction.  
  
 `(?=`sous- *expression* `)` est une assertion de préanalyse positive ; autrement dit, le ou les caractères situés après la position actuelle doivent correspondre à la sous- *expression*. `(?!`sous- *expression* `)` est une assertion de préanalyse négative ; autrement dit, le ou les caractères situés après la position actuelle ne doivent pas correspondre à la sous- *expression*. Les assertions de préanalyse positive et négative sont très utiles quand la sous- *expression* est un sous-ensemble de la sous-expression suivante.  
  
 L'exemple suivant utilise deux modèles d'expressions régulières équivalentes qui valident un nom de type qualifié complet. Le premier modèle est sujet à des performances médiocres dues à une rétroaction excessive. Le second modifie la première expression régulière en remplaçant un quantificateur imbriqué par une assertion de préanalyse positive. La sortie de l'exemple indique la durée d'exécution de la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> .  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 Le premier modèle d'expression régulière, `^(([A-Z]\w*)+\.)*[A-Z]\w*$`, est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Démarrer la correspondance au début de la chaîne.|  
|`([A-Z]\w*)+\.`|Mettre en correspondance un caractère alphabétique (A-Z) suivi de zéro, un ou plusieurs caractères alphabétiques une ou plusieurs fois, suivi d'un point. Cette comparaison ne respecte pas la casse, parce que la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .|  
|`(([A-Z]\w*)+\.)*`|Mettre en correspondance le modèle précédent, zéro, une ou plusieurs fois.|  
|`[A-Z]\w*`|Mettre en correspondance un caractère alphabétique suivi de zéro, un ou plusieurs caractères alphabétiques.|  
|`$`|Terminer la correspondance à la fin de la chaîne d'entrée.|  
  
 Le second modèle d'expression régulière, `^((?=[A-Z])\w+\.)*[A-Z]\w*$`, utilise une assertion de préanalyse positive. Il est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Démarrer la correspondance au début de la chaîne.|  
|`(?=[A-Z])`|Effectuer une préanalyse du premier caractère et continuer la mise en correspondance s'il est alphabétique (A-Z). Cette comparaison ne respecte pas la casse, parce que la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .|  
|`\w+\.`|Mettre en correspondance un ou plusieurs caractères alphabétiques suivis d'un point.|  
|`((?=[A-Z])\w+\.)*`|Mettre en correspondance un ou plusieurs caractères alphabétiques suivis d'un point zéro, une ou plusieurs fois. Le caractère alphabétique initial doit être alphabétique.|  
|`[A-Z]\w*`|Mettre en correspondance un caractère alphabétique suivi de zéro, un ou plusieurs caractères alphabétiques.|  
|`$`|Terminer la correspondance à la fin de la chaîne d'entrée.|  
  
## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](regular-expressions.md)
- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
- [Quantificateurs](quantifiers-in-regular-expressions.md)
- [Constructions d’alternative](alternation-constructs-in-regular-expressions.md)
- [Constructions de regroupement](grouping-constructs-in-regular-expressions.md)
