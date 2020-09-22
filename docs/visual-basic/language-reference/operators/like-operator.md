---
title: Like, opérateur
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 49dfe5cf5dbcf8dc6f79f569a92e36aa81806913
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866774"
---
# <a name="like-operator-visual-basic"></a>Like (opérateur Visual Basic)

Compare une chaîne à un modèle.  

> [!IMPORTANT]
> L' `Like` opérateur n’est actuellement pas pris en charge dans les projets .net Core et .NET standard.

## <a name="syntax"></a>Syntaxe  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Éléments  

 `result`  
 Obligatoire. Toute `Boolean` variable. Le résultat est une `Boolean` valeur indiquant si le répond à `string` `pattern` .  
  
 `string`  
 Obligatoire. Toute expression `String` .  
  
 `pattern`  
 Obligatoire. Toute `String` expression conforme aux conventions de critères spéciaux décrites dans « remarques ».  
  
## <a name="remarks"></a>Notes  

 Si la valeur de `string` est conforme au modèle contenu dans `pattern` , `result` est `True` . Si la chaîne n’est pas conforme au modèle, a la valeur `result` `False` . Si `string` et `pattern` sont des chaînes vides, le résultat est `True` .  
  
## <a name="comparison-method"></a>Méthode de comparaison  

 Le comportement de l' `Like` opérateur dépend de l' [instruction Option Compare](../statements/option-compare-statement.md). La méthode de comparaison de chaînes par défaut pour chaque fichier source est `Option Compare Binary` .  
  
## <a name="pattern-options"></a>Options de modèle  

 Les critères spéciaux intégrés fournissent un outil polyvalent pour les comparaisons de chaînes. Les fonctionnalités de critères spéciaux vous permettent de faire correspondre chaque caractère d' `string` un caractère spécifique, d’un caractère générique, d’une liste de caractères ou d’une plage de caractères. Le tableau suivant indique les caractères autorisés dans `pattern` et ce qu’ils correspondent.  
  
|Caractères dans `pattern`|Correspond à `string`|  
|-----------------------------|-------------------------|  
|`?`|Tout caractère unique|  
|`*`|Zéro, un ou plusieurs caractères|  
|`#`|Tout chiffre (0 à 9)|  
|`[charlist]`|N’importe quel caractère unique dans `charlist`|  
|`[!charlist]`|N’importe quel caractère ne figurant pas dans `charlist`|  
  
## <a name="character-lists"></a>Listes de caractères  

 Un groupe d’un ou plusieurs caractères ( `charlist` ) entre crochets ( `[ ]` ) peut être utilisé pour mettre en correspondance n’importe quel caractère unique dans `string` et peut inclure presque n’importe quel code de caractère, y compris des chiffres.  
  
 Un point d’exclamation ( `!` ) au début de `charlist` signifie qu’une correspondance est établie si un caractère quelconque à l’exception des caractères de `charlist` est trouvé dans `string` . Lorsqu’il est utilisé en dehors des crochets, le point d’exclamation correspond à lui-même.  
  
## <a name="special-characters"></a>Caractères spéciaux  

 Pour mettre en correspondance les caractères spéciaux ( `[` ), le point d’interrogation ( `?` ), le signe dièse ( `#` ) et l’astérisque ( `*` ), placez-les entre crochets. `]`Vous ne pouvez pas utiliser le crochet droit () dans un groupe pour qu’il corresponde à lui-même, mais il peut être utilisé en dehors d’un groupe comme un caractère individuel.  
  
 La séquence de caractères `[]` est considérée comme une chaîne de longueur nulle ( `""` ). Toutefois, il ne peut pas faire partie d’une liste de caractères placée entre crochets. Si vous souhaitez vérifier si une position dans `string` contient un groupe de caractères ou aucun caractère, vous pouvez utiliser `Like` deux fois. Pour obtenir un exemple, consultez [Comment : faire correspondre une chaîne à un modèle](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Plages de caractères  

 En utilisant un trait d’Union ( `–` ) pour séparer les limites inférieure et supérieure de la plage, `charlist` peut spécifier une plage de caractères. Par exemple, `[A–Z]` aboutit à une correspondance si la position de caractère correspondante dans `string` contient un caractère quelconque dans la plage `A` `Z` , et `[!H–L]` aboutit à une correspondance si la position de caractère correspondante contient un caractère en dehors de la plage `H` () `L` .  
  
 Lorsque vous spécifiez une plage de caractères, ceux-ci doivent apparaître dans l’ordre de tri croissant, c’est-à-dire de la plus petite à la plus élevée. Par conséquent, `[A–Z]` est un modèle valide, mais `[Z–A]` ne l’est pas.  
  
### <a name="multiple-character-ranges"></a>Plusieurs plages de caractères  

 Pour spécifier plusieurs plages pour la même position de caractère, placez-les entre les crochets sans délimiteurs. Par exemple, `[A–CX–Z]` aboutit à une correspondance si la position de caractère correspondante dans `string` contient un caractère quelconque dans la plage `A` ( `C` ou la plage `X` ) `Z` .  
  
### <a name="usage-of-the-hyphen"></a>Utilisation du trait d’Union  

 Un trait d’Union ( `–` ) peut apparaître au début (après un point d’exclamation, le cas échéant) ou à la fin de `charlist` pour se mettre en correspondance. Dans tout autre emplacement, le trait d’Union identifie une plage de caractères délimitée par les caractères situés de part et d’autre du trait d’Union.  
  
## <a name="collating-sequence"></a>Séquence de classement  

 La signification d’une plage spécifiée dépend de l’ordre des caractères au moment de l’exécution, tel que déterminé par `Option Compare` et des paramètres régionaux du système sur lequel le code s’exécute. Avec `Option Compare Binary` , la plage `[A–E]` correspond à,,, `A` `B` `C` `D` et `E` . Avec, correspond à,,,,,,,,,, `Option Compare Text` `[A–E]` `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` et `e` . La plage ne correspond pas `Ê` ou `ê` parce que les caractères accentués sont triés après les caractères non accentués dans l’ordre de tri.  
  
## <a name="digraph-characters"></a>Caractères digrammes  

 Dans certains langages, des caractères alphabétiques représentent deux caractères distincts. Par exemple, plusieurs langues utilisent le caractère `æ` pour représenter les caractères `a` et `e` lorsqu’ils apparaissent ensemble. L' `Like` opérateur reconnaît que le caractère digramme unique et les deux caractères individuels sont équivalents.  
  
 Quand une langue qui utilise un caractère digramme est spécifiée dans les paramètres régionaux du système, une occurrence du caractère digramme unique dans `pattern` ou `string` correspond à la séquence de deux caractères équivalente dans l’autre chaîne. De même, un caractère digramme `pattern` placé entre crochets (par lui-même, dans une liste ou dans une plage) correspond à la séquence de deux caractères équivalente dans `string` .  
  
## <a name="overloading"></a>Surcharge  

 L' `Like` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise l' `Like` opérateur pour comparer des chaînes à différents modèles. Les résultats sont placés dans une `Boolean` variable indiquant si chaque chaîne est conforme au modèle.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Opérateurs de comparaison](comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Option Compare, instruction](../statements/option-compare-statement.md)
- [Opérateurs et expressions](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Comment : faire correspondre une chaîne à un modèle](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
