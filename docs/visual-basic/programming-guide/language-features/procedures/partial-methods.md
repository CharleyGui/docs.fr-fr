---
title: Méthodes partielles
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
ms.openlocfilehash: 61a1398ba7de8dab005fa1e9efa13dc2ba18cc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364121"
---
# <a name="partial-methods-visual-basic"></a>Méthodes partielles (Visual Basic)
Les méthodes partielles permettent aux développeurs d’insérer une logique personnalisée dans le code. En règle générale, le code fait partie d’une classe générée par le concepteur. Les méthodes partielles sont définies dans une classe partielle créée par un générateur de code, et elles sont généralement utilisées pour fournir une notification indiquant qu’un événement a été modifié. Ils permettent au développeur de spécifier un comportement personnalisé en réponse à la modification.  
  
 Le concepteur du générateur de code définit uniquement la signature de la méthode et un ou plusieurs appels à la méthode. Les développeurs peuvent ensuite fournir des implémentations pour la méthode s’ils souhaitent personnaliser le comportement du code généré. Quand aucune implémentation n’est fournie, les appels à la méthode sont supprimés par le compilateur, ce qui entraîne une surcharge de performance supplémentaire.  
  
## <a name="declaration"></a>Déclaration  
 Le code généré marque la définition d’une méthode partielle en plaçant le mot clé `Partial` au début de la ligne de signature.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 La définition doit respecter les conditions suivantes :  
  
- La méthode doit être un `Sub` , et non un `Function` .  
  
- Le corps de la méthode doit être laissé vide.  
  
- Le modificateur d’accès doit être `Private` .  
  
## <a name="implementation"></a>Implémentation  
 L’implémentation consiste principalement à remplir le corps de la méthode partielle. L’implémentation est généralement dans une classe partielle distincte de la définition, et est écrite par un développeur qui souhaite étendre le code généré.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 L’exemple précédent duplique exactement la signature dans la déclaration, mais les variations sont possibles. En particulier, d’autres modificateurs peuvent être ajoutés, tels que `Overloads` ou `Overrides` . Un seul `Overrides` modificateur est autorisé. Pour plus d’informations sur les modificateurs de méthode, consultez [instruction Sub](../../../language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Utilisation  
 Vous appelez une méthode partielle comme vous le feriez pour toute autre `Sub` procédure. Si la méthode a été implémentée, les arguments sont évalués et le corps de la méthode est exécuté. Toutefois, n’oubliez pas que l’implémentation d’une méthode partielle est facultative. Si la méthode n’est pas implémentée, un appel à celle-ci n’a aucun effet, et les expressions passées comme arguments à la méthode ne sont pas évaluées.  
  
## <a name="example"></a>Exemple  
 Dans un fichier nommé Product. Designer. vb, définissez une `Product` classe qui a une `Quantity` propriété.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 Dans un fichier nommé Product. vb, fournissez une implémentation pour `QuantityChanged` .  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Enfin, dans la méthode main d’un projet, déclarez une `Product` instance et fournissez une valeur initiale pour sa `Quantity` propriété.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Une boîte de message s’affiche pour afficher le message suivant :  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Voir aussi

- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [Sub, procédures](./sub-procedures.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Partial](../../../language-reference/modifiers/partial.md)
- [Génération de code dans LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Ajout d’une logique métier à l’aide de méthodes partielles](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
