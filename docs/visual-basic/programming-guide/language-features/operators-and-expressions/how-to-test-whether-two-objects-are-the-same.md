---
title: 'Comment : déterminer si deux objets sont identiques'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343617"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Comment : déterminer si deux objets sont identiques (Visual Basic)
Si vous avez deux variables qui font référence à des objets, vous pouvez utiliser l’opérateur `Is` ou `IsNot`, ou les deux, pour déterminer s’ils font référence à la même instance.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Pour tester si deux objets sont identiques  
  
- Utilisez l' [opérateur is](../../../../visual-basic/language-reference/operators/is-operator.md) ou l' [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) avec les deux variables comme opérandes.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Vous souhaiterez peut-être effectuer une certaine action selon que deux objets font référence à la même instance. L’exemple précédent compare les `c` de contrôle par rapport au contrôle actif sur le `f`de formulaire. S’il n’y a aucun contrôle actif, ou s’il en existe un mais qu’il ne s’agit pas de la même instance de contrôle que `c`, l’instruction `If` échoue et la procédure est retournée sans traitement supplémentaire.  
  
 Que vous utilisiez `Is` ou `IsNot` est une question de commodité personnelle. Il peut être plus facile à lire que l’autre dans une expression donnée.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs de comparaison dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
