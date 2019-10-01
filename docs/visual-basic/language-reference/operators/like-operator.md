---
title: Like (opérateur Visual Basic)
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
ms.openlocfilehash: 795ecc2e80d57af29ccd50c50d2dd209c6425e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701136"
---
# <a name="like-operator-visual-basic"></a>Like (opérateur Visual Basic)
Compare une chaîne à un modèle.  

> [!IMPORTANT]
> L’opérateur `Like` n’est actuellement pas pris en charge dans les projets .NET Core et .NET Standard.

## <a name="syntax"></a>Syntaxe  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Toute variable `Boolean`. Le résultat est une valeur `Boolean` indiquant si la `string` satisfait ou non au `pattern`.  
  
 `string`  
 Obligatoire. Toute expression `String` .  
  
 `pattern`  
 Obligatoire. Toute expression `String` conforme aux conventions de critères spéciaux décrites dans « remarques ».  
  
## <a name="remarks"></a>Notes  
 Si la valeur de `string` est conforme au modèle contenu dans `pattern`, `result` est `True`. Si la chaîne n’est pas conforme au modèle, `result` est `False`. Si les `string` et `pattern` sont des chaînes vides, le résultat est `True`.  
  
## <a name="comparison-method"></a>Méthode de comparaison  
 Le comportement de l’opérateur `Like` dépend de l' [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md). La méthode de comparaison de chaînes par défaut pour chaque fichier source est `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Options de modèle  
 Les critères spéciaux intégrés fournissent un outil polyvalent pour les comparaisons de chaînes. Les fonctionnalités de critères spéciaux vous permettent de faire correspondre chaque caractère de `string` à un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères. Le tableau suivant indique les caractères autorisés dans `pattern` et ce qu’ils correspondent.  
  
|Caractères en `pattern`|Correspond à `string`|  
|-----------------------------|-------------------------|  
|`?`|Tout caractère unique|  
|`*`|Zéro, un ou plusieurs caractères|  
|`#`|Tout chiffre (0 à 9)|  
|`[charlist]`|Tout caractère unique dans `charlist`|  
|`[!charlist]`|Tout caractère qui n’est pas dans `charlist`|  
  
## <a name="character-lists"></a>Listes de caractères  
 Un groupe d’un ou plusieurs caractères (`charlist`) entre crochets (`[ ]`) peut être utilisé pour mettre en correspondance n’importe quel caractère unique dans `string` et peut inclure presque n’importe quel code de caractère, y compris des chiffres.  
  
 Un point d’exclamation (`!`) au début de `charlist` signifie qu’une correspondance est établie si un caractère quelconque à l’exception des caractères de `charlist` est trouvé dans `string`. Lorsqu’il est utilisé en dehors des crochets, le point d’exclamation correspond à lui-même.  
  
## <a name="special-characters"></a>Caractères spéciaux  
 Pour mettre en correspondance les caractères spéciaux crochet gauche (`[`), point d’interrogation (`?`), signe dièse (`#`) et astérisque (`*`), placez-les entre crochets. Le crochet droit (`]`) ne peut pas être utilisé dans un groupe pour se mettre en correspondance, mais il peut être utilisé en dehors d’un groupe comme un caractère individuel.  
  
 La séquence de caractères `[]` est considérée comme une chaîne de longueur nulle (`""`). Toutefois, il ne peut pas faire partie d’une liste de caractères placée entre crochets. Si vous souhaitez vérifier si une position dans `string` contient un groupe de caractères ou aucun caractère, vous pouvez utiliser `Like` à deux reprises. Pour voir un exemple, consultez [Comment : Faire correspondre une chaîne à un modèle @ no__t-0.  
  
## <a name="character-ranges"></a>Plages de caractères  
 En utilisant un trait d’Union (`–`) pour séparer les limites inférieure et supérieure de la plage, `charlist` peut spécifier une plage de caractères. Par exemple, `[A–Z]` donne une correspondance si la position de caractère correspondante dans `string` contient un caractère dans la plage `A` – `Z`, et `[!H–L]` aboutit à une correspondance si la position de caractère correspondante contient un caractère en dehors de plage `H` – `L`.  
  
 Lorsque vous spécifiez une plage de caractères, ceux-ci doivent apparaître dans l’ordre de tri croissant, c’est-à-dire de la plus petite à la plus élevée. Ainsi, `[A–Z]` est un modèle valide, mais `[Z–A]` ne l’est pas.  
  
### <a name="multiple-character-ranges"></a>Plusieurs plages de caractères  
 Pour spécifier plusieurs plages pour la même position de caractère, placez-les entre les crochets sans délimiteurs. Par exemple, `[A–CX–Z]` donne une correspondance si la position de caractère correspondante dans `string` contient un caractère dans la plage `A` – `C` ou la plage `X` – `Z`.  
  
### <a name="usage-of-the-hyphen"></a>Utilisation du trait d’Union  
 Un trait d’Union (`–`) peut apparaître au début (après un point d’exclamation, le cas échéant) ou à la fin de `charlist` pour correspondre à lui-même. Dans tout autre emplacement, le trait d’Union identifie une plage de caractères délimitée par les caractères situés de part et d’autre du trait d’Union.  
  
## <a name="collating-sequence"></a>Séquence de classement  
 La signification d’une plage spécifiée dépend de l’ordre des caractères au moment de l’exécution, comme déterminé par `Option Compare` et les paramètres régionaux du système sur lequel le code s’exécute. Avec `Option Compare Binary`, la plage `[A–E]` correspond à `A`, `B`, `C`, `D` et `E`. Avec `Option Compare Text`, `[A–E]` correspond à `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, 0, 1, 2 et 3. La plage ne correspond pas à `Ê` ou à `ê`, car les caractères accentués sont triés après les caractères non accentués dans l’ordre de tri.  
  
## <a name="digraph-characters"></a>Caractères digrammes  
 Dans certains langages, des caractères alphabétiques représentent deux caractères distincts. Par exemple, plusieurs langues utilisent le caractère `æ` pour représenter les caractères `a` et `e` lorsqu’ils apparaissent ensemble. L’opérateur `Like` reconnaît que le caractère digramme unique et les deux caractères individuels sont équivalents.  
  
 Quand une langue qui utilise un caractère digramme est spécifiée dans les paramètres régionaux du système, une occurrence du caractère digramme unique dans `pattern` ou `string` correspond à la séquence de deux caractères équivalente dans l’autre chaîne. De même, un caractère digramme dans `pattern` placé entre crochets (seul, dans une liste ou dans une plage) correspond à la séquence de deux caractères équivalente dans `string`.  
  
## <a name="overloading"></a>Surcharge  
 L’opérateur `Like` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’opérateur `Like` pour comparer des chaînes à différents modèles. Les résultats sont placés dans une variable `Boolean` indiquant si chaque chaîne est conforme au modèle.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Guide pratique pour Faire correspondre une chaîne à un modèle @ no__t-0
