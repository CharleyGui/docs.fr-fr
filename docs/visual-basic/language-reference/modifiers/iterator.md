---
title: Itérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351523"
---
# <a name="iterator-visual-basic"></a>Itérateur (Visual Basic)
Spécifie qu’une fonction ou un accesseur `Get` est un itérateur.  
  
## <a name="remarks"></a>Notes  
 Un *itérateur* exécute une itération personnalisée sur une collection. Un itérateur utilise l’instruction [yield](../../../visual-basic/language-reference/statements/yield-statement.md) pour retourner chaque élément de la collection un par un. Quand une instruction `Yield` est atteinte, l’emplacement actuel dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Un itérateur peut être implémenté en tant que fonction ou en tant qu’accesseur `Get` d’une définition de propriété. Le modificateur `Iterator` apparaît dans la déclaration de la fonction d’itérateur ou de l’accesseur `Get`.  
  
 Vous appelez un itérateur à partir du code client à l’aide [d’un for each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Le type de retour d’une fonction d’itérateur ou d’un accesseur `Get` peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Un itérateur ne peut pas avoir de paramètres de `ByRef`.  
  
 Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Un itérateur peut être une fonction anonyme. Pour plus d’informations, consultez [Itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `Iterator` peut être utilisé dans les contextes suivants :  
  
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une fonction d’itérateur. La fonction Iterator a une instruction `Yield` qui se trouve à l’intérieur d’une instruction [for... Next](../../../visual-basic/language-reference/statements/for-next-statement.md) . Chaque itération de [pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corps d’instruction dans `Main` crée un appel à la fonction d’itérateur `Power`. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre un accesseur `Get` qui est un itérateur. Le modificateur `Iterator` se trouve dans la déclaration de la propriété.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Pour obtenir des exemples supplémentaires, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Itérateurs](../../programming-guide/concepts/iterators.md)
- [Yield (instruction)](../../../visual-basic/language-reference/statements/yield-statement.md)
