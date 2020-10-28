---
title: Constructions de regroupement dans les expressions régulières
description: Apprenez à utiliser les constructions de regroupement dans .NET. Les constructions de regroupement détourent les sous-expressions d’une expression régulière et capturent les sous-chaînes d’une chaîne d’entrée.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lookbehinds
- regular expressions, grouping constructs
- lookaheads
- .NET regular expressions, grouping constructs
- constructs, grouping
- grouping constructs
ms.assetid: 0fc18634-f590-4062-8d5c-f0b71abe405b
ms.openlocfilehash: de424b4a022a5e2d2f8a9c12b4147383082f019b
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888506"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Constructions de regroupement dans les expressions régulières
Les constructions de regroupement délimitent les sous-expressions d'une expression régulière et capturent les sous-chaînes d'une chaîne d'entrée. Utilisez les constructions de regroupement pour effectuer les opérations suivantes :  
  
- Mettre en correspondance une sous-expression qui est répétée dans la chaîne d'entrée.  
  
- Appliquer un quantificateur à une sous-expression qui possède plusieurs éléments de langage d'expression régulière. Pour plus d'informations sur les quantificateurs, voir [Quantifiers](quantifiers-in-regular-expressions.md).  
  
- Inclure une sous-expression dans la chaîne retournée par les méthodes <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> et <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> .  
  
- Récupérer des sous-expressions spécifiques de la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> et les traiter séparément du texte global mis en correspondance.  
  
 Le tableau suivant répertorie les constructions de regroupement prises en charge par le moteur d’expression régulière de .NET et indique si ce sont des constructions avec ou sans capture.  
  
|Construction de regroupement|Avec ou sans capture|  
|------------------------|-------------------------------|  
|[Sous-expressions mises en correspondance](#matched_subexpression)|Capture|  
|[Sous-expressions mises en correspondance nommées](#named_matched_subexpression)|Capture|  
|[Définitions de groupe d'équilibrage](#balancing_group_definition)|Capture|  
|[Groupes sans capture](#noncapturing_group)|Sans capture|  
|[Options de groupe](#group_options)|Sans capture|  
|[Assertions de préanalyse positive de largeur nulle](#zerowidth_positive_lookahead_assertion)|Sans capture|  
|[Assertions de préanalyse négative de largeur nulle](#zerowidth_negative_lookahead_assertion)|Sans capture|  
|[Assertions de postanalyse positive de largeur nulle](#zerowidth_positive_lookbehind_assertion)|Sans capture|  
|[Assertions de postanalyse négative de largeur nulle](#zerowidth_negative_lookbehind_assertion)|Sans capture|  
|[Groupes atomiques](#atomic_groups)|Sans capture|  
  
 Pour plus d’informations sur les groupes et le modèle objet d’expression régulière, consultez [constructions de regroupement et objets d’expression régulière](#Objects).  
  
<a name="matched_subexpression"></a>
## <a name="matched-subexpressions"></a>Sous-expressions mises en correspondance  
 La construction de regroupement suivante capture une sous-expression mise en correspondance :  
  
 `(`sous- *expression*`)`  
  
 où *subexpression* représente un modèle d'expression régulière valide. Les captures qui utilisent des parenthèses sont numérotées automatiquement de la gauche vers la droite en fonction de l'ordre des parenthèses ouvrantes dans l'expression régulière, à partir de 1. La capture numérotée 0 représente le texte mis en correspondance par le modèle d'expression régulière entier.  
  
> [!NOTE]
> Par défaut, l’élément de langage sous- `(` *expression* `)` capture la sous-expression mise en correspondance. Toutefois, si le paramètre <xref:System.Text.RegularExpressions.RegexOptions> d'une méthode de mise en correspondance de modèle d'expression régulière comprend l'indicateur <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> ou que l'option `n` soit appliquée à cette sous-expression (voir [Options de groupe](#group_options) plus loin dans cette rubrique), la sous-expression mise en correspondance n'est pas capturée.  
  
 Vous pouvez accéder aux groupes capturés de quatre façons :  
  
- En utilisant la construction de référence arrière dans l'expression régulière. La sous-expression mise en correspondance est référencée dans la même expression régulière en utilisant la syntaxe `\` *Number* , où *Number* est le nombre ordinal de la sous-expression capturée.  
  
- En utilisant la construction de référence arrière nommée dans l'expression régulière. La sous-expression mise en correspondance est référencée dans la même expression régulière en utilisant la syntaxe `\k<` *nom* `>` , où *nom* est le nom d’un groupe de capture, ou `\k<` *nombre* `>` , où *nombre* est le nombre ordinal d’un groupe de capture. Un groupe de capture possède un nom par défaut qui est identique à son nombre ordinal. Pour plus d'informations, voir [Sous-expressions mises en correspondance nommées](#named_matched_subexpression) plus loin dans cette rubrique.  
  
- En utilisant la séquence de remplacement `$`*nombre* dans un appel de méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> , où *nombre* est le nombre ordinal de la sous-expression capturée.  
  
- Par programmation, en utilisant l'objet <xref:System.Text.RegularExpressions.GroupCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . Le membre situé à la position zéro dans la collection représente la correspondance de l’expression régulière entière. Chaque membre suivant représente une sous-expression mise en correspondance. Pour plus d'informations, voir la section [Grouping Constructs and Regular Expression Objects](#Objects) .  
  
 L'exemple suivant illustre une expression régulière qui identifie des mots en double dans le texte. Les deux groupes de capture du modèle d'expression régulière représentent les deux instances du mot en double. La capture de la seconde instance permet d'indiquer la position de départ du mot dans la chaîne d'entrée.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Le modèle d'expression régulière est le suivant :  
  
`(\w+)\s(\1)\W`  
  
 Le tableau suivant montre comment le modèle d'expression régulière est interprété.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(\1)`|Mettre en correspondance la chaîne dans le premier groupe capturé. Il s'agit du deuxième groupe de capture. L'exemple l'affecte à un groupe capturé pour que la position de départ du mot en double puisse être récupérée de la propriété `Match.Index` .|  
|`\W`|Mettre en correspondance un caractère n'appartenant pas à un mot, comme un espace blanc ou un signe de ponctuation. Cela empêche le modèle d'expression régulière de mettre en correspondance un mot qui commence par le mot récupéré du premier groupe capturé.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>Sous-expressions mises en correspondance nommées  
 La construction de regroupement suivante capture une sous-expression mise en correspondance et vous permet d'y accéder à partir d'un nom ou d'un nombre :  
  
`(?<name>subexpression)`  
  
 ou :  
  
`(?'name'subexpression)`  
  
 où *name* est un nom de groupe valide, et *subexpression* représente un modèle d'expression régulière valide. *name* ne doit pas contenir de caractères de ponctuation et ne peut pas commencer par un nombre.  
  
> [!NOTE]
> Si le paramètre <xref:System.Text.RegularExpressions.RegexOptions> d'une méthode de mise en correspondance de modèle d'expression régulière comprend l'indicateur <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> ou que l'option `n` soit appliquée à cette sous-expression (voir [Options de groupe](#group_options) plus loin dans cette rubrique), la seule façon de capturer une sous-expression consiste à nommer explicitement des groupes de capture.  
  
 Vous pouvez accéder aux groupes capturés nommés comme suit :  
  
- En utilisant la construction de référence arrière nommée dans l'expression régulière. La sous-expression mise en correspondance est référencée dans la même expression régulière en utilisant la syntaxe `\k<` *nom* `>` , où *nom* est le nom de la sous-expression capturée.  
  
- En utilisant la construction de référence arrière dans l'expression régulière. La sous-expression mise en correspondance est référencée dans la même expression régulière en utilisant la syntaxe `\` *Number* , où *Number* est le nombre ordinal de la sous-expression capturée. Les sous-expressions mises en correspondance nommées sont numérotées de manière consécutive de la gauche vers la droite après les sous-expressions mises en correspondance.  
  
- En utilisant la `${` *name* `}` séquence de remplacement de nom dans un <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> appel de méthode ou, où *nom* est le nom de la sous-expression capturée.  
  
- En utilisant la séquence de remplacement `$`*nombre* dans un appel de méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> , où *nombre* est le nombre ordinal de la sous-expression capturée.  
  
- Par programmation, en utilisant l'objet <xref:System.Text.RegularExpressions.GroupCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . Le membre situé à la position zéro dans la collection représente la correspondance de l’expression régulière entière. Chaque membre suivant représente une sous-expression mise en correspondance. Les groupes capturés nommés sont stockés dans la collection après les groupes capturés numérotés.  
  
- Par programmation, en fournissant le nom de la sous-expression à l'indexeur de l'objet <xref:System.Text.RegularExpressions.GroupCollection> (en C#) ou à sa propriété <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> (en Visual Basic).  
  
 Un modèle d'expression régulière simple permet d'illustrer comment les groupes numérotés (sans nom) et nommés peuvent être référencés par programmation ou à l'aide d'une syntaxe de langage d'expression régulière. L'expression régulière `((?<One>abc)\d+)?(?<Two>xyz)(.*)` génère les groupes de capture suivants en fonction du nombre et du nom. Le premier groupe de capture (nombre 0) fait toujours référence au modèle entier.  
  
|Number|Name|Modèle|  
|------------|----------|-------------|  
|0|0 (nom par défaut)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (nom par défaut)|`((?<One>abc)\d+)`|  
|2|2 (nom par défaut)|`(.*)`|  
|3|Une|`(?<One>abc)`|  
|4|Deux|`(?<Two>xyz)`|  
  
 L'exemple suivant illustre une expression régulière qui identifie les mots en double et le mot qui se trouve juste après chaque mot en double. Le modèle d'expression régulière définit deux sous-expressions nommées : `duplicateWord`, qui représente le mot en double, et `nextWord`, qui représente le mot qui suit le mot en double.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Le modèle d'expression régulière est le suivant :  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 Le tableau suivant montre comment l'expression régulière est interprétée.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Nommer ce groupe de capture `duplicateWord`.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`\k<duplicateWord>`|Mettre en correspondance la chaîne à partir du groupe capturé nommé `duplicateWord`.|  
|`\W`|Mettre en correspondance un caractère n'appartenant pas à un mot, comme un espace blanc ou un signe de ponctuation. Cela empêche le modèle d'expression régulière de mettre en correspondance un mot qui commence par le mot récupéré du premier groupe capturé.|  
|`(?<nextWord>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Nommer ce groupe de capture `nextWord`.|  
  
 Notez qu'un nom de groupe peut être répété dans une expression régulière. Par exemple, il est possible pour plusieurs groupes soient nommés `digit`, comme le montre l'exemple suivant. Dans le cas de noms en doublon, la valeur de l'objet <xref:System.Text.RegularExpressions.Group> est déterminée par la dernière capture réussie dans la chaîne d'entrée. En outre, la collection <xref:System.Text.RegularExpressions.CaptureCollection> est remplie avec des informations sur chaque capture, comme si le nom du groupe n'était pas en doublon.  
  
 Dans l'exemple suivant, l'expression régulière `\D+(?<digit>\d+)\D+(?<digit>\d+)?` comprend deux occurrences d'un groupe nommé `digit`. Le premier groupe nommé `digit` capture un ou plusieurs caractères numériques. Le deuxième groupe nommé `digit` capture zéro ou une occurrence d'un ou plusieurs caractères numériques. Comme la sortie de l'exemple le montre, si le deuxième groupe de capture correspond à du texte, la valeur de ce texte définit la valeur de l'objet <xref:System.Text.RegularExpressions.Group> . Si le deuxième groupe de capture ne correspond pas à la chaîne d'entrée, la valeur de la dernière correspondance définit la valeur de l'objet <xref:System.Text.RegularExpressions.Group> .  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Le tableau suivant montre comment l'expression régulière est interprétée.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\D+`|Mettre en correspondance un ou plusieurs caractères non décimaux.|  
|`(?<digit>\d+)`|Mettre en correspondance un ou plusieurs caractères décimaux. Affecter la correspondance au groupe nommé `digit` .|  
|`\D+`|Mettre en correspondance un ou plusieurs caractères non décimaux.|  
|`(?<digit>\d+)?`|Mettre en correspondance zéro ou une occurrence d'un ou plusieurs caractères numériques décimaux. Affecter la correspondance au groupe nommé `digit` .|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Définitions de groupe d'équilibrage  
 Une définition de groupe d'équilibrage supprime la définition d'un groupe précédemment défini et stocke, dans le groupe actuel, l'intervalle entre le groupe précédemment défini et ce dernier. Cette construction de regroupement se présente sous la forme suivante :  
  
`(?<name1-name2>subexpression)`  
  
 ou :  
  
`(?'name1-name2' subexpression)`
  
 où *name1* est le groupe actuel (facultatif), *name2* un groupe précédemment défini et *subexpression* un modèle d'expression régulière valide. La définition de groupe d'équilibrage supprime la définition de *name2* et stocke l'intervalle entre *name2* et *name1* dans *name1* . Si aucun groupe *name2* n'est défini, la recherche de correspondance s'effectue de façon rétroactive. Comme la suppression de la dernière définition de *name2* révèle la définition antérieure de *name2* , cette construction vous permet d’utiliser la pile de captures du groupe *name2* comme compteur pour effectuer le suivi des constructions imbriquées, telles que des parenthèses ou des crochets ouvrants et fermants.  
  
 La définition de groupe d'équilibrage utilise *name2* comme pile. Le caractère initial de chaque construction imbriquée est placé dans le groupe et dans sa collection <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> . Quand le caractère fermant est mis en correspondance, le caractère ouvrant correspondant est supprimé du groupe, et la collection <xref:System.Text.RegularExpressions.Group.Captures%2A> est diminuée d'une unité. Une fois que les caractères ouvrant et fermant de toutes les constructions imbriquées ont été mis en correspondance, *name2* est vide.  
  
> [!NOTE]
> Une fois que vous avez modifié l'expression régulière dans l'exemple suivant pour utiliser les caractères ouvrant et fermant appropriés d'une construction imbriquée, vous pouvez l'utiliser pour gérer la plupart des constructions imbriquées, telles que les expressions mathématiques ou les lignes de code de programme qui comprennent plusieurs appels de méthode imbriqués.  
  
 L'exemple suivant utilise une définition de groupe d'équilibrage pour mettre en correspondance les chevrons gauche et droit (<>) dans une chaîne d'entrée. L'exemple définit deux groupes nommés, `Open` et `Close`, qui sont utilisés comme une pile pour effectuer le suivi des paires de chevrons correspondantes. Chaque chevron gauche capturé est placé dans la collection de captures du groupe `Open` , tandis que chaque chevron droit capturé est placé dans la collection de captures du groupe `Close` . La définition de groupe d'équilibrage s'assure qu'à chaque chevron gauche correspond un chevron droit. Si tel n'est pas le cas, le sous-modèle final, `(?(Open)(?!))`, n'est évalué que si le groupe `Open` n'est pas vide (signe que toutes les constructions imbriquées n'ont pas été fermées). Si le sous-modèle final est évalué, la recherche de correspondance échoue, car le sous-modèle `(?!)` est une assertion de préanalyse négative de largeur nulle qui échoue systématiquement.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Le modèle d'expression régulière est le suivant :  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 L'expression régulière est interprétée comme suit :  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commencer au début de la chaîne.|  
|`[^<>]*`|Mettre en correspondance zéro caractère, ou plus, à l'exception des chevrons gauches ou droits.|  
|`(?'Open'<)`|Mettre en correspondance un chevron gauche et l'affecter à un groupe nommé `Open`.|  
|`[^<>]*`|Mettre en correspondance zéro caractère, ou plus, à l'exception des chevrons gauches ou droits.|  
|`((?'Open'<)[^<>]*)+`|Mettre en correspondance une ou plusieurs occurrences d'un chevron gauche suivies de zéro caractère, ou plus, à l'exception des chevrons gauches ou droits. Il s'agit du deuxième groupe de capture.|  
|`(?'Close-Open'>)`|Mettre en correspondance un chevron droit, affecter la sous-chaîne entre le groupe `Open` et le groupe actuel au groupe `Close` , puis supprimer la définition du groupe `Open` .|  
|`[^<>]*`|Mettre en correspondance zéro occurrence, ou plus, d'un caractère à l'exception d'un chevron gauche ou droit.|  
|`((?'Close-Open'>)[^<>]*)+`|Mettre en correspondance une occurrence, ou plus, d'un chevron droit, suivies de zéro occurrence, ou plus, d'un caractère à l'exception d'un chevron gauche ou droit. Durant la mise en correspondance du chevron droit, affecter la sous-chaîne entre le groupe `Open` et le groupe actuel au groupe `Close` , puis supprimer la définition du groupe `Open` . Il s'agit du troisième groupe de capture.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Mettre en correspondance zéro occurrence, ou plus, du modèle suivant : une ou plusieurs occurrences d'un chevron gauche, suivies de zéro caractère, ou plus, autre qu'un chevron, suivis d'une ou plusieurs occurrences d'un chevron droit, suivies de zéro caractère, ou plus, autre qu'un chevron. Durant la mise en correspondance du chevron droit, supprimer la définition du groupe `Open` et affecter la sous-chaîne entre le groupe `Open` et le groupe actuel au groupe `Close` . Il s'agit du premier groupe de capture.|  
|`(?(Open)(?!))`|Si le groupe `Open` existe, abandonner la recherche de correspondance si une chaîne vide peut être mise en correspondance, mais ne pas avancer la position du moteur d'expression régulière dans la chaîne. Il s'agit d'une assertion de préanalyse négative de largeur nulle. Comme une chaîne vide est toujours implicitement présente dans une chaîne d'entrée, cette recherche de correspondance échoue systématiquement. L'échec de cette recherche de correspondance indique que les chevrons ne sont pas équilibrés.|  
|`$`|Mettre en correspondance la fin de la chaîne d'entrée.|  
  
 La sous-expression finale, `(?(Open)(?!))`, indique si les constructions d'imbrication dans la chaîne d'entrée sont correctement équilibrées (par exemple, si à chaque chevron gauche correspond un chevron droit). Elle utilise une mise en correspondance conditionnelle basée sur un groupe capturé valide ; pour plus d'informations, voir [Alternation Constructs](alternation-constructs-in-regular-expressions.md). Si le groupe `Open` est défini, le moteur d'expression régulière essaie de mettre en correspondance la sous-expression `(?!)` dans la chaîne d'entrée. Le groupe `Open` ne doit être défini que si les constructions d'imbrication ne sont pas équilibrées. Le modèle à mettre en correspondance dans la chaîne d'entrée doit donc être un modèle qui entraîne systématiquement l'échec de la recherche de correspondance. Dans ce cas, `(?!)` est une assertion de préanalyse négative de largeur nulle qui échoue systématiquement, car une chaîne vide est toujours implicitement présente à la position suivante dans la chaîne d'entrée.  
  
 Dans l’exemple, le moteur d’expression régulière évalue la chaîne d’entrée « \<abc><mno\<xyz>> » comme indiqué dans le tableau suivant.  
  
|Étape|Modèle|Résultat|  
|----------|-------------|------------|  
|1|`^`|Commence la correspondance au début de la chaîne d'entrée.|  
|2|`[^<>]*`|Recherche des caractères autres que des chevrons avant le chevron gauche ; ne trouve aucune correspondance.|  
|3|`(((?'Open'<)`|Met en correspondance le chevron gauche dans « \<abc> » et l’affecte au groupe `Open`.|  
|4|`[^<>]*`|Met en correspondance « abc ».|  
|5|`)+`|« <abc » est la valeur du deuxième groupe capturé.<br /><br /> Le caractère suivant dans la chaîne d'entrée n'étant pas un chevron gauche, le moteur d'expression régulière ne repasse pas par le sous-modèle `(?'Open'<)[^<>]*)` .|  
|6|`((?'Close-Open'>)`|Met en correspondance le chevron droit dans « \<abc> », affecte « abc », qui est la sous-chaîne entre le groupe `Open` et le chevron droit, au groupe `Close`, puis supprime la valeur actuelle (« < ») du groupe `Open`, qui se trouve alors vide.|  
|7|`[^<>]*`|Recherche des caractères autres que des chevrons après le chevron droit ; ne trouve aucune correspondance.|  
|8|`)+`|La valeur du troisième groupe capturé est « > ».<br /><br /> Le caractère suivant dans la chaîne d'entrée n'étant pas un chevron droit, le moteur d'expression régulière ne repasse pas par le sous-modèle `((?'Close-Open'>)[^<>]*)` .|  
|9|`)*`|La valeur du premier groupe capturé est « \<abc> ».<br /><br /> Le caractère suivant dans la chaîne d'entrée étant un chevron gauche, le moteur d'expression régulière repasse par le sous-modèle `(((?'Open'<)` .|  
|10|`(((?'Open'<)`|Correspond au chevron gauche dans « \<mno" and assigns it to the `Open` group. Its <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> la collection a désormais une seule valeur, «< ».|  
|11|`[^<>]*`|Met en correspondance « mno ».|  
|12|`)+`|« <mno » est la valeur du deuxième groupe capturé.<br /><br /> Le caractère suivant dans la chaîne d'entrée étant un chevron gauche, le moteur d'expression régulière repasse par le sous-modèle `(?'Open'<)[^<>]*)` .|  
|13|`(((?'Open'<)`|Met en correspondance le chevron gauche dans « \<xyz> » et l’affecte au groupe `Open`. La <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection du `Open` groupe comprend maintenant deux captures : le Chevron gauche de « \<mno", and the left angle bracket from "\<xyz> ».|  
|14|`[^<>]*`|Met en correspondance « xyz ».|  
|15|`)+`|« <xyz » est la valeur du deuxième groupe capturé.<br /><br /> Le caractère suivant dans la chaîne d'entrée n'étant pas un chevron gauche, le moteur d'expression régulière ne repasse pas par le sous-modèle `(?'Open'<)[^<>]*)` .|  
|16|`((?'Close-Open'>)`|Met en correspondance le chevron droit dans « \<xyz> », "xyz" affecte la sous-chaîne entre le groupe `Open` et le chevron droit au groupe `Close` , puis supprime la valeur actuelle du groupe `Open` . La valeur de la capture précédente (le Chevron gauche dans « \<mno") becomes the current value of the `Open` group. The <xref:System.Text.RegularExpressions.Group.Captures%2A> collection du `Open` groupe comprend maintenant une seule capture, le Chevron gauche de « \<xyz> ».|  
|17|`[^<>]*`|Recherche des caractères autres que des chevrons ; ne trouve aucune correspondance.|  
|18|`)+`|La valeur du troisième groupe capturé est « > ».<br /><br /> Le caractère suivant dans la chaîne d'entrée étant un chevron droit, le moteur d'expression régulière repasse par le sous-modèle `((?'Close-Open'>)[^<>]*)` .|  
|19|`((?'Close-Open'>)`|Met en correspondance le chevron droit final dans « xyz>> », affecte « mno\<xyz> » (la sous-chaîne entre le groupe `Open` et le chevron droit) au groupe `Close`, puis supprime la valeur actuelle du groupe `Open`. Le groupe `Open` est maintenant vide.|  
|20|`[^<>]*`|Recherche des caractères autres que des chevrons ; ne trouve aucune correspondance.|  
|21|`)+`|La valeur du troisième groupe capturé est « > ».<br /><br /> Le caractère suivant dans la chaîne d'entrée n'étant pas un chevron droit, le moteur d'expression régulière ne repasse pas par le sous-modèle `((?'Close-Open'>)[^<>]*)` .|  
|22|`)*`|La valeur du premier groupe capturé est « <mno\<xyz>> ».<br /><br /> Le caractère suivant dans la chaîne d'entrée n'étant pas un chevron gauche, le moteur d'expression régulière ne repasse pas par le sous-modèle `(((?'Open'<)` .|  
|23|`(?(Open)(?!))`|Le groupe `Open` n'étant pas défini, aucune recherche de correspondance n'est effectuée.|  
|24|`$`|Met en correspondance la fin de la chaîne d'entrée.|  
  
<a name="noncapturing_group"></a>
## <a name="noncapturing-groups"></a>Groupes sans capture  
 La construction de regroupement suivante ne capture pas la sous-chaîne mise en correspondance par une sous-expression :  
  
`(?:subexpression)`
  
 où *subexpression* représente un modèle d'expression régulière valide. En règle générale, la construction de groupe sans capture est utilisée quand un quantificateur est appliqué à un groupe, mais que les sous-chaînes capturées par celui-ci ne présentent aucun intérêt.  
  
> [!NOTE]
> Si une expression régulière comprend des constructions de regroupement imbriquées, une construction de groupe sans capture externe ne s'applique pas aux constructions de groupe imbriquées internes.  
  
 L'exemple suivant illustre une expression régulière qui comprend des groupes sans capture. Notez que la sortie ne comprend aucun groupe capturé.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 L'expression régulière `(?:\b(?:\w+)\W*)+\.` met en correspondance une phrase terminée par un point. Comme l'expression régulière porte sur des phrases et non sur des mots spécifiques, les constructions de regroupement sont exclusivement utilisées en tant que quantificateurs. Le modèle d'expression régulière est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(?:\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Ne pas affecter le texte mis en correspondance à un groupe capturé.|  
|`\W*`|Mettre en correspondance zéro ou plusieurs caractères non alphabétiques.|  
|`(?:\b(?:\w+)\W*)+`|Mettre en correspondance le modèle d'un ou plusieurs caractères alphabétiques en commençant à la limite d'un mot, suivi de zéro caractère non alphabétique, ou plus, une ou plusieurs fois. Ne pas affecter le texte mis en correspondance à un groupe capturé.|  
|`\.`|Mettre en correspondance un point.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Options de groupe  
 La construction de regroupement suivante applique ou désactive les options spécifiées dans une sous-expression :  
  
 `(?imnsx-imnsx:`sous- *expression*`)`  
  
 où *subexpression* représente un modèle d'expression régulière valide. Par exemple, `(?i-s:)` désactive la prise en compte des majuscules et des minuscules, ainsi que le mode à ligne simple. Pour plus d’informations sur les options inline que vous pouvez spécifier, consultez [Options des expressions régulières](regular-expression-options.md).  
  
> [!NOTE]
> Vous pouvez spécifier des options qui s'appliquent à une expression régulière entière plutôt qu'à une sous-expression en utilisant un constructeur de classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> ou une méthode statique. Vous pouvez également spécifier des options inline qui s'appliquent après un point spécifique dans une expression régulière en utilisant la construction de langage `(?imnsx-imnsx)`.  
  
 La construction des options de groupe n'est pas un groupe de capture. En d'autres termes, bien qu'une partie d'une chaîne capturée par *sous-expression* soit incluse dans la correspondance, elle n'est pas placée dans un groupe capturé, ni utilisée pour remplir l'objet <xref:System.Text.RegularExpressions.GroupCollection> .  
  
 Dans l’exemple suivant, l’expression régulière `\b(?ix: d \w+)\s` utilise des options inline dans une construction de regroupement pour désactiver le respect de la casse et ignorer l’espace blanc du modèle durant l’identification de tous les mots commençant par la lettre « d ». L'expression régulière est définie comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(?ix: d \w+)`|Sans prendre en compte les majuscules et les minuscules et en ignorant l'espace blanc dans ce modèle, mettre en correspondance un caractère « d » suivi d'un ou plusieurs caractères alphabétiques.|  
|`\s`|Mettre en correspondance un espace blanc.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Assertions de préanalyse positive de largeur nulle  
 La construction de regroupement suivante définit une assertion de préanalyse positive de largeur nulle :  
  
 `(?=`sous- *expression*`)`  
  
 où *sous-expression* représente un modèle d'expression régulière. Pour qu'une recherche de correspondance réussisse, la chaîne d'entrée doit correspondre au modèle d'expression régulière dans *sous-expression* , bien que la sous-chaîne mise en correspondance ne soit pas incluse dans le résultat de la recherche de correspondance. Une assertion de préanalyse positive de largeur nulle n'est pas rétroactive.  
  
 En règle générale, une assertion de préanalyse positive de largeur nulle est trouvée à la fin d'un modèle d'expression régulière. Elle définit une sous-chaîne qui doit être trouvée à la fin d'une chaîne pour qu'une mise en correspondance se produise, mais qui ne doit pas être incluse dans la correspondance. En outre, elle est utile pour empêcher une rétroactivité excessive. Vous pouvez utiliser une assertion de préanalyse positive de largeur nulle indiquant qu'un groupe capturé particulier doit commencer par un texte qui correspond à une partie du modèle défini pour ce groupe. Par exemple, si un groupe de capture met en correspondance des caractères alphabétiques consécutifs, vous pouvez utiliser une assertion de préanalyse positive de largeur nulle pour imposer que le premier caractère soit un caractère majuscule alphabétique.  
  
 L'exemple suivant utilise une assertion de préanalyse positive de largeur nulle pour mettre en correspondance le mot qui précède le verbe « is » dans la chaîne d'entrée.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 L'expression régulière `\b\w+(?=\sis\b)` est interprétée comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|`(?=\sis\b)`|Détermine si les caractères alphabétiques sont suivis d'un espace blanc et de la chaîne « is », qui se termine à la limite d'un mot. Si tel est le cas, la recherche de correspondance réussit.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Assertions de préanalyse négative de largeur nulle  
 La construction de regroupement suivante définit une assertion de préanalyse négative de largeur nulle :  
  
 `(?!`sous- *expression*`)`  
  
 où *sous-expression* représente un modèle d'expression régulière. Pour que la recherche de correspondance réussisse, la chaîne d'entrée ne doit pas correspondre au modèle d'expression régulière dans *sous-expression* , bien que la chaîne mise en correspondance ne soit pas incluse dans le résultat de la recherche de correspondance.  
  
 En règle générale, une assertion de préanalyse négative de largeur nulle est utilisée au début ou à la fin d'une expression régulière. Au début d'une expression régulière, elle peut définir un modèle spécifique qui ne doit pas être mis en correspondance quand le début de l'expression régulière définit un modèle de recherche de correspondance similaire, mais plus général. Dans ce cas, elle est souvent utilisée pour limiter la rétroactivité. À la fin d'une expression régulière, elle peut définir une sous-expression qui ne peut pas apparaître à la fin d'une correspondance.  
  
 L'exemple suivant définit une expression régulière qui utilise une assertion de préanalyse de largeur nulle au début de l'expression régulière pour mettre en correspondance les mots qui ne commencent pas par « un ».  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 L'expression régulière `\b(?!un)\w+\b` est interprétée comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(?!un)`|Déterminer si les deux caractères suivants sont « un ». Si tel n'est pas le cas, une correspondance est possible.|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 L'exemple suivant définit une expression régulière qui utilise une assertion de préanalyse de largeur nulle à la fin de l'expression régulière pour mettre en correspondance les mots qui ne se terminent pas par un caractère de ponctuation.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 L'expression régulière `\b\w+\b(?!\p{P})` est interprétée comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
|`\p{P})`|Si le caractère suivant n'est pas un symbole de ponctuation (tel qu'un point ou une virgule), la recherche de correspondance réussit.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Assertions de postanalyse positive de largeur nulle  
 La construction de regroupement suivante définit une assertion de postanalyse positive de largeur nulle :  
  
 `(?<=`sous- *expression*`)`  
  
 où *sous-expression* représente un modèle d'expression régulière. Pour qu'une recherche de correspondance réussisse, *sous-expression* doit se trouver dans la chaîne d'entrée à gauche de la position actuelle, bien que la sous-expression ( `subexpression` ) ne soit pas incluse dans le résultat de la recherche de correspondance. Une assertion de postanalyse positive de largeur nulle n'est pas rétroactive.  
  
 Les assertions de postanalyse positive de largeur nulle sont généralement utilisées au début des expressions régulières. Le modèle qu'elles définissent est une condition préalable pour une correspondance, bien qu'il ne fasse pas partie du résultat de la recherche de correspondance.  
  
 L'exemple suivant met en correspondance les deux derniers chiffres des années appartenant au vingt et unième siècle (en d'autres termes, les chiffres « 20 » doivent précéder la chaîne mise en correspondance).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Le modèle d'expression régulière `(?<=\b20)\d{2}\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\d{2}`|Mettre en correspondance deux chiffres décimaux.|  
|`(?<=\b20)`|Continuer la mise en correspondance si les deux chiffres décimaux sont précédés des chiffres décimaux « 20 » à la limite d'un mot.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 Les assertions de postanalyse positive de largeur nulle permettent également de limiter la rétroactivité quand le ou les derniers caractères d'un groupe capturé doivent être une partie des caractères qui correspondent au modèle d'expression régulière de ce groupe. Par exemple, si un groupe capture tous les caractères alphabétiques consécutifs, vous pouvez utiliser une assertion de postanalyse positive de largeur nulle pour imposer que le dernier caractère soit un caractère alphabétique.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Assertions de postanalyse négative de largeur nulle  
 La construction de regroupement suivante définit une assertion de postanalyse négative de largeur nulle :  
  
 `(?<!`sous- *expression*`)`  
  
 où *sous-expression* représente un modèle d'expression régulière. Pour qu’une recherche de correspondance réussisse, *sous-expression* ne doit pas se trouver dans la chaîne d’entrée à gauche de la position actuelle. Toutefois, toute sous-chaîne qui ne correspond pas à `subexpression` est exclue du résultat de la recherche de correspondance.  
  
 Les assertions de postanalyse négative de largeur nulle sont généralement utilisées au début des expressions régulières. Le modèle qu'elles définissent exclut une mise en correspondance dans la chaîne qui suit. Elles permettent également de limiter la rétroactivité quand le ou les derniers caractères d'un groupe capturé ne doivent pas être un ou plusieurs des caractères qui correspondent au modèle d'expression régulière de ce groupe. Par exemple, si un groupe capture tous les caractères alphabétiques consécutifs, vous pouvez utiliser une assertion de postanalyse positive de largeur zéro pour exiger que le dernier caractère ne soit pas un trait de soulignement (\_).  
  
 L'exemple suivant met en correspondance la date de n'importe quel jour de la semaine ne tombant pas pendant le week-end (c'est-à-dire, tous les jours sauf le samedi et le dimanche).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Le modèle d'expression régulière `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques suivis d'un espace blanc.|  
|`\d{1,2},`|Mettre en correspondance un ou deux chiffres décimaux suivis d'un espace blanc et d'une virgule.|  
|`\d{4}\b`|Mettre en correspondance quatre chiffres décimaux, puis terminer la correspondance à la limite d'un mot.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Si la correspondance est précédée d'une chaîne autre que « Saturday » ou « Sunday » suivie d'un espace, la mise en correspondance réussit.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Groupes atomiques  
 La construction de regroupement suivante représente un groupe atomique (connu dans certains autres moteurs d’expressions régulières comme une sous-expression non rétroactive, une sous-expression atomique ou une sous-expression unique) :
  
 `(?>`sous- *expression*`)`  
  
 où *sous-expression* représente un modèle d'expression régulière.  
  
 D'ordinaire, si une expression régulière comprend un modèle de mise en correspondance facultatif ou de substitution et qu'aucune mise en correspondance ne réussit, le moteur d'expression régulière peut explorer plusieurs directions pour mettre en correspondance une chaîne d'entrée avec un modèle. Si aucune correspondance n'est trouvée au niveau de la première branche, le moteur d'expression régulière peut revenir au point d'exécution de la première mise en correspondance et renouveler l'opération au niveau de la deuxième branche. Ce processus peut se poursuivre jusqu'à ce que toutes les branches aient été essayées.  
  
 La construction de langage sous- `(?>` *expression* `)` désactive la rétroaction. Le moteur d'expression régulière met en correspondance tous les caractères possibles de la chaîne d'entrée. Quand aucune mise en correspondance supplémentaire n'est possible, il n'essaie pas d'effectuer une mise en correspondance de modèle de substitution de manière rétroactive. (En d'autres termes, la sous-expression ne met en correspondance que les chaînes qu'elle seule peut mettre en correspondance ; elle n'essaie pas de mettre en correspondance une chaîne avec le concours de sous-expressions qui la suivent éventuellement.)  
  
 Cette option est recommandée si vous savez que la rétroactivité est vouée à l'échec. Empêcher le moteur d'expression régulière d'effectuer des recherches superflues améliore les performances.  
  
 L’exemple suivant montre comment un groupe atomique modifie les résultats d’une correspondance de modèle. Contrairement à l'expression régulière non rétroactive, l'expression régulière rétroactive met en correspondance une série de caractères répétés suivis d'une occurrence supplémentaire du même caractère à la limite d'un mot.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 L'expression régulière non rétroactive `(?>(\w)\1+).\b` est définie comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`(\w)`|Mettre en correspondance un seul caractère alphabétique et l'affecter au premier groupe de capture.|  
|`\1+`|Mettre en correspondance la valeur de la première sous-chaîne capturée une ou plusieurs fois.|  
|`.`|Mettre en correspondance n'importe quel caractère.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
|`(?>(\w)\1+)`|Mettre en correspondance une ou plusieurs occurrences d'un caractère alphabétique en double, mais ne pas effectuer rétroactivement une mise en correspondance du dernier caractère à la limite d'un mot.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Constructions de regroupement et objets d'expression régulière  
 Les sous-chaînes mises en correspondance par un groupe de capture d'expression régulière sont représentées par des objets <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> , qui peuvent être récupérés de l'objet <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . L'objet <xref:System.Text.RegularExpressions.GroupCollection> est rempli comme suit :  
  
- Le premier objet <xref:System.Text.RegularExpressions.Group> de la collection (l'objet d'index zéro) représente la correspondance entière.  
  
- L'ensemble d'objets <xref:System.Text.RegularExpressions.Group> suivant représente des groupes de capture sans nom (numérotés). Ils apparaissent dans l'ordre dans lequel ils sont définis dans l'expression régulière, de la gauche vers la droite. Les valeurs d'index de ces groupes vont de 1 au nombre de groupes de capture sans nom dans la collection. (L'index d'un groupe particulier est équivalent à sa référence arrière numérotée. Pour plus d'informations sur les références arrière, voir [Backreference Constructs](backreference-constructs-in-regular-expressions.md).)  
  
- Le dernier ensemble d'objets <xref:System.Text.RegularExpressions.Group> représente des groupes de capture nommés. Ils apparaissent dans l'ordre dans lequel ils sont définis dans l'expression régulière, de la gauche vers la droite. La valeur d'index du premier groupe de capture nommé est égale à l'index du dernier groupe de capture sans nom, plus une unité. En l'absence de groupe de capture sans nom dans l'expression régulière, la valeur d'index du premier groupe de capture nommé est égale à un (1).  
  
 Si vous appliquez un quantificateur à un groupe de capture, les propriétés <xref:System.Text.RegularExpressions.Group> , <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>et <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>de l'objet <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> correspondant reflètent la dernière sous-chaîne capturée par un groupe de capture. Vous pouvez récupérer de l'objet <xref:System.Text.RegularExpressions.CaptureCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> un ensemble complet de sous-chaînes capturées par des groupes possédant des quantificateurs.  
  
 L'exemple suivant clarifie la relation entre les objets <xref:System.Text.RegularExpressions.Group> et <xref:System.Text.RegularExpressions.Capture> .  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Le modèle d'expression régulière `(\b(\w+)\W+)+` extrait des mots spécifiques d'une chaîne. Il est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Ensemble, ces caractères forment un mot. Il s'agit du deuxième groupe de capture.|  
|`\W+`|Mettre en correspondance un ou plusieurs caractères non alphabétiques.|  
|`(\b(\w+)\W+)`|Mettre en correspondance le modèle d'un ou plusieurs caractères alphabétiques, suivis d'un ou plusieurs caractères non alphabétiques, une ou plusieurs fois. Il s'agit du premier groupe de capture.|  
  
 Le second groupe de capture met en correspondance chaque mot de la phrase. Le premier groupe de capture met en correspondance chaque mot, ainsi que la ponctuation et l’espace qui suivent le mot. L'objet <xref:System.Text.RegularExpressions.Group> dont l'index a pour valeur 2 fournit des informations sur le texte mis en correspondance par le second groupe de capture. Tous les mots capturés par le groupe de capture sont récupérables de l'objet <xref:System.Text.RegularExpressions.CaptureCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
- [Rétroaction](backtracking-in-regular-expressions.md)
