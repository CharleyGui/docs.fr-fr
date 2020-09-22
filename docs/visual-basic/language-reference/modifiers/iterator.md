---
title: Itérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 0b459a16317b8ba55886e52ecadb227ddf2fee83
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875432"
---
# <a name="iterator-visual-basic"></a>Itérateur (Visual Basic)

Spécifie qu’une fonction ou un `Get` accesseur est un itérateur.  
  
## <a name="remarks"></a>Notes  

 Un *itérateur* exécute une itération personnalisée sur une collection. Un itérateur utilise l’instruction [yield](../statements/yield-statement.md) pour retourner chaque élément de la collection un par un. Quand une `Yield` instruction est atteinte, l’emplacement actuel dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Un itérateur peut être implémenté en tant que fonction ou en tant qu' `Get` accesseur d’une définition de propriété. Le `Iterator` modificateur apparaît dans la déclaration de la fonction d’itérateur ou de l' `Get` accesseur.  
  
 Vous appelez un itérateur à partir du code client à l’aide [d’un for each... Instruction suivante](../statements/for-each-next-statement.md).  
  
 Le type de retour d’une fonction ou d’un `Get` accesseur d’itérateur peut être <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> .  
  
 Un itérateur ne peut pas avoir de `ByRef` paramètres.  
  
 Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Un itérateur peut être une fonction anonyme. Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Usage  

 Le modificateur `Iterator` peut être utilisé dans les contextes suivants :  
  
- [Function (instruction)](../statements/function-statement.md)  
  
- [Property Statement](../statements/property-statement.md)  
  
## <a name="example"></a>Exemple  

 L’exemple suivant illustre une fonction d’itérateur. La fonction Iterator a une `Yield` instruction qui se trouve à l’intérieur d’une instruction [for... Next](../statements/for-next-statement.md) . Chaque itération de [pour chaque](../statements/for-each-next-statement.md) corps d’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant illustre un accesseur `Get` qui est un itérateur. Le `Iterator` modificateur est dans la déclaration de propriété.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Pour obtenir des exemples supplémentaires, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iterators](../../programming-guide/concepts/iterators.md)
- [Yield (instruction)](../statements/yield-statement.md)
