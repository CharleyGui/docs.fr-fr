---
title: 'Comment : déterminer si deux objets sont identiques'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348596"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Comment : déterminer si deux objets sont identiques (Visual Basic)
Dans Visual Basic, deux références de variables sont considérées comme identiques si leurs pointeurs sont identiques, autrement dit, si les deux variables pointent vers la même instance de classe en mémoire. Par exemple, dans une application Windows Forms, vous souhaiterez peut-être effectuer une comparaison pour déterminer si l’instance actuelle (`Me`) est identique à une instance particulière, telle que `Form2`.  
  
 Visual Basic fournit deux opérateurs pour comparer des pointeurs. L' [opérateur is](../../../../visual-basic/language-reference/operators/is-operator.md) retourne `True` si les objets sont identiques, et l' [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retourne `True` s’ils ne le sont pas.  
  
## <a name="determining-if-two-objects-are-identical"></a>Déterminer si deux objets sont identiques  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Pour déterminer si deux objets sont identiques  
  
1. Configurez une expression `Boolean` pour tester les deux objets.  
  
2. Dans votre expression de test, utilisez l’opérateur `Is` avec les deux objets en tant qu’opérandes.  
  
     `Is` retourne `True` si les objets pointent vers la même instance de classe.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Déterminer si deux objets ne sont pas identiques  
 Parfois, vous souhaitez effectuer une action si les deux objets ne sont pas identiques, et il peut être difficile de combiner des `Not` et des `Is`, par exemple `If Not obj1 Is obj2`. Dans ce cas, vous pouvez utiliser l’opérateur `IsNot`.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Pour déterminer si deux objets ne sont pas identiques  
  
1. Configurez une expression `Boolean` pour tester les deux objets.  
  
2. Dans votre expression de test, utilisez l’opérateur `IsNot` avec les deux objets en tant qu’opérandes.  
  
     `IsNot` retourne `True` si les objets ne pointent pas vers la même instance de classe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant teste des paires de variables de `Object` pour voir si elles pointent vers la même instance de classe.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 L’exemple précédent affiche la sortie suivante.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Voir aussi

- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is (opérateur)](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Guide pratique : déterminer si deux objets sont liés](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
