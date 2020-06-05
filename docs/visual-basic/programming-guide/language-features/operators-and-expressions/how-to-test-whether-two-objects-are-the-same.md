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
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403419"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Comment : déterminer si deux objets sont identiques (Visual Basic)
Si vous avez deux variables qui font référence à des objets, vous pouvez utiliser `Is` l' `IsNot` opérateur ou, ou les deux, pour déterminer s’ils font référence à la même instance.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Pour tester si deux objets sont identiques  
  
- Utilisez l' [opérateur is](../../../language-reference/operators/is-operator.md) ou l' [opérateur IsNot](../../../language-reference/operators/isnot-operator.md) avec les deux variables comme opérandes.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Vous souhaiterez peut-être effectuer une certaine action selon que deux objets font référence à la même instance. L’exemple précédent compare `c` le contrôle par rapport au contrôle actif sur le formulaire `f` . S’il n’y a aucun contrôle actif, ou s’il en existe un mais qu’il ne s’agit pas de la même instance de contrôle que `c` , l' `If` instruction échoue et la procédure est retournée sans traitement supplémentaire.  
  
 Que vous utilisiez ou que vous soyez `Is` `IsNot` une question de commodité personnelle. Il peut être plus facile à lire que l’autre dans une expression donnée.  
  
## <a name="see-also"></a>Voir aussi

- [Comparison Operators in Visual Basic](comparison-operators.md)
