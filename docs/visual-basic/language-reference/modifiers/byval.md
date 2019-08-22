---
title: Byval (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666860"
---
# <a name="byval-visual-basic"></a>Byval (Visual Basic)
Spécifie qu’un argument est passé [par valeur](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de sorte que la procédure ou propriété appelée ne peut pas modifier la valeur d’une variable sous-jacente à l’argument dans le code appelant. Si aucun modificateur n’est spécifié, ByVal est la valeur par défaut.

> [!NOTE]
> Étant donné qu’il s’agit de la valeur par défaut, il n' `ByVal` est pas nécessaire de spécifier explicitement le mot clé dans les signatures de méthode. Il a tendance à produire du code bruyant et entraîne souvent un surexamen `ByRef` du mot clé non défini par défaut.

## <a name="remarks"></a>Notes
 Le modificateur `ByVal` peut être utilisé dans les contextes suivants :

 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Exemples
 L’exemple suivant illustre l’utilisation du mécanisme `ByVal` de passage de paramètre avec un argument de type référence. Dans l’exemple, l’argument est `c1`, une instance de la `Class1`classe. `ByVal`empêche le code des procédures de modifier la valeur sous-jacente de l’argument de `c1`référence,, mais ne protège pas les champs et les `c1`propriétés accessibles de.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Voir aussi

- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Passage d’un argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
