---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351594"
---
# <a name="byval-visual-basic"></a>Byval (Visual Basic)
Spécifie qu’un argument est passé [par valeur](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de sorte que la procédure ou propriété appelée ne peut pas modifier la valeur d’une variable sous-jacente à l’argument dans le code appelant. Si aucun modificateur n’est spécifié, ByVal est la valeur par défaut.

> [!NOTE]
> Étant donné qu’il s’agit de la valeur par défaut, il n’est pas nécessaire de spécifier explicitement le mot clé `ByVal` dans les signatures de méthode. Il a tendance à produire du code bruyant et entraîne souvent un surexamen du mot clé `ByRef` non défini par défaut.

## <a name="remarks"></a>Notes
 Le modificateur `ByVal` peut être utilisé dans les contextes suivants :

 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Exemple
 L’exemple suivant illustre l’utilisation du mécanisme de passage de paramètre `ByVal` avec un argument de type référence. Dans l’exemple, l’argument est `c1`, une instance de la classe `Class1`. `ByVal` empêche le code des procédures de modifier la valeur sous-jacente de l’argument de référence, `c1`, mais ne protège pas les champs et les propriétés accessibles de `c1`.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Voir aussi

- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Passage d’un argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
