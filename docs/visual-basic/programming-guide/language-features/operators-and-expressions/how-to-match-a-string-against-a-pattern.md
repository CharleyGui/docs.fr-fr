---
title: 'Comment : faire correspondre une chaîne à un modèle'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: d8a3c363d1a443db4a0b7633e380562af1913aca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403444"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Comment : faire correspondre une chaîne à un modèle (Visual Basic)

Si vous souhaitez savoir si une expression du [type de données String](../../../language-reference/data-types/string-data-type.md) est conforme à un modèle, vous pouvez utiliser l' [opérateur Like](../../../language-reference/operators/like-operator.md).

`Like`prend deux opérandes. L’opérande de gauche est une expression de chaîne et l’opérande de droite est une chaîne contenant le modèle à utiliser pour la mise en correspondance. `Like`retourne une `Boolean` valeur indiquant si l’expression de chaîne respecte le modèle.

Vous pouvez faire correspondre chaque caractère de l’expression de chaîne à un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères. Les positions des spécifications dans la chaîne de modèle correspondent aux positions des caractères à mettre en correspondance dans l’expression de chaîne.

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Pour faire correspondre un caractère de l’expression de chaîne à un caractère spécifique

Placez le caractère spécifique directement dans la chaîne du modèle. Certains caractères spéciaux doivent être placés entre crochets ( `[ ]` ). Pour plus d’informations, consultez [Like, opérateur](../../../language-reference/operators/like-operator.md).

L’exemple suivant teste si `myString` se compose exactement du caractère unique `H` .

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Pour faire correspondre un caractère de l’expression de chaîne à un caractère générique

Placez un point d’interrogation ( `?` ) dans la chaîne du modèle. Tout caractère valide dans cette position fait l’aboutissement d’une correspondance.

L’exemple suivant teste si `myString` se compose du caractère unique `W` suivi de deux caractères exactement de toutes les valeurs.

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Pour mettre en correspondance un caractère de l’expression de chaîne avec une liste de caractères

Placez les crochets ( `[ ]` ) dans la chaîne de modèle, et à l’intérieur des crochets, placez la liste des caractères. Ne séparez pas les caractères par des virgules ou tout autre séparateur. Tout caractère unique de la liste fait l’aboutissement d’une correspondance.

L’exemple suivant teste si `myString` se compose d’un caractère valide suivi de l’un des caractères `A` , `C` ou `E` .

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

Notez que cette correspondance respecte la casse.

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Pour faire correspondre un caractère de l’expression de chaîne à une plage de caractères

Placez les crochets ( `[ ]` ) dans la chaîne de modèle, et à l’intérieur des crochets, placez les caractères les plus bas et les plus hauts dans la plage, séparés par un trait d’Union ( `–` ). Tout caractère unique dans la plage fait l’aboutissement d’une correspondance.

L’exemple suivant teste si `myString` se compose des caractères `num` suivis de l’un des caractères,,,, `i` `j` `k` `l` `m` ou `n` .

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

Notez que cette correspondance respecte la casse.

## <a name="matching-empty-strings"></a>Correspondance de chaînes vides

`Like`traite la séquence `[]` comme une chaîne de longueur nulle ( `""` ). Vous pouvez utiliser `[]` pour tester si la totalité de l’expression de chaîne est vide, mais vous ne pouvez pas l’utiliser pour tester si une position particulière dans l’expression de chaîne est vide. Si une position vide est l’une des options dont vous avez besoin pour tester, vous pouvez utiliser `Like` plusieurs fois.

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Pour mettre en correspondance un caractère de l’expression de chaîne avec une liste de caractères ou aucun caractère

1. Appelez l' `Like` opérateur deux fois sur la même expression de chaîne et connectez les deux appels à l’aide de l' [opérateur or](../../../language-reference/operators/or-operator.md) ou de l' [opérateur OrElse](../../../language-reference/operators/orelse-operator.md).

2. Dans la chaîne de modèle de la première `Like` clause, incluez la liste de caractères entre crochets ( `[ ]` ).

3. Dans la chaîne de modèle de la deuxième `Like` clause, ne placez pas de caractère à la position en question.

    L’exemple suivant teste le numéro de téléphone à sept chiffres `phoneNum` pour exactement trois chiffres, suivis d’un espace, d’un trait d’Union ( `–` ), d’un point ( `.` ) ou d’aucun caractère, suivi de quatre chiffres exactement.

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>Voir aussi

- [Opérateurs de comparaison](../../../language-reference/operators/comparison-operators.md)
- [Opérateurs et expressions](index.md)
- [Like, opérateur](../../../language-reference/operators/like-operator.md)
- [String, type de données](../../../language-reference/data-types/string-data-type.md)
