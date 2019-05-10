---
title: Méthodes partielles (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 50d7f24fd9f854d36bb2ed48c2e41a996c29dfe8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638883"
---
# <a name="partial-methods-visual-basic"></a>Méthodes partielles (Visual Basic)
Méthodes partielles permettent aux développeurs d’insérer une logique personnalisée dans du code. En règle générale, le code fait partie d’une classe généré par le concepteur. Les méthodes partielles sont définies dans une classe partielle qui est créée par un générateur de code, et ils sont couramment utilisés pour fournir une notification que quelque chose a été modifiée. Ils permettent au développeur de spécifier un comportement personnalisé en réponse à la modification.  
  
 Le concepteur du Générateur de code définit uniquement la signature de méthode et un ou plusieurs appels à la méthode. Les développeurs peuvent ensuite fournir des implémentations de la méthode s’ils souhaitent personnaliser le comportement du code généré. Lorsqu’aucune implémentation n’est fournie, les appels à la méthode sont supprimés par le compilateur, ce qui entraîne aucune surcharge de performances supplémentaires.  
  
## <a name="declaration"></a>Déclaration  
 Le code généré marque la définition d’une méthode partielle en plaçant le mot clé `Partial` au début de la ligne de signature.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 La définition doit remplir les conditions suivantes :  
  
- La méthode doit être un `Sub`, et non un `Function`.  
  
- Le corps de la méthode doit être laissé vide.  
  
- Le modificateur d’accès doit être `Private`.  
  
## <a name="implementation"></a>Implémentation  
 L’implémentation consiste principalement à remplir le corps de la méthode partielle. L’implémentation est généralement dans une classe partielle distincte de la définition et est écrite par un développeur qui souhaite étendre le code généré.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 L’exemple précédent reproduit la signature dans la déclaration exactement, mais des variations sont possibles. En particulier, autres modificateurs peuvent être ajoutés, tels que `Overloads` ou `Overrides`. Seul `Overrides` modificateur est autorisé. Pour plus d’informations sur les modificateurs de méthode, consultez [Sub, instruction](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Utilisez  
 Vous appelez une méthode partielle comme vous appelleriez n’importe quel autre `Sub` procédure. Si la méthode a été implémentée, les arguments sont évalués et le corps de la méthode est exécuté. Toutefois, n’oubliez pas que l’implémentation d’une méthode partielle est facultative. Si la méthode n’est pas implémentée, un appel à ce dernier n’a aucun effet, et les expressions passées comme arguments à la méthode ne sont pas évaluées.  
  
## <a name="example"></a>Exemple  
 Dans un fichier nommé Product.Designer.vb, définissez une `Product` classe a un `Quantity` propriété.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 Dans un fichier nommé Product.vb, fournir une implémentation pour `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Enfin, dans la méthode Main d’un projet, déclarez un `Product` de l’instance et de fournir une valeur initiale pour son `Quantity` propriété.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Une boîte de message doit apparaître qui affiche ce message :  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Voir aussi

- [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procédures Sub](./sub-procedures.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Génération de code dans LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Ajout d’une logique métier à l’aide de méthodes partielles](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
