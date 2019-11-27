---
title: 'Comment : créer une expression lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: bb0bdb3c10a7df2ca954fbdb9382a25bf805068d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349740"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Comment : créer une expression lambda (Visual Basic)
Une *expression lambda* est une fonction ou une sous-routine qui n’a pas de nom. Une expression lambda peut être utilisée partout où un type délégué est valide.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Pour créer une fonction d’expression lambda sur une seule ligne  
  
1. Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Function`, comme dans l’exemple suivant :  
  
     `Dim add1 =`   `Function`  
  
2. Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction. Notez que vous ne spécifiez pas de nom après `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. À la suite de la liste de paramètres, tapez une seule expression en tant que corps de la fonction. La valeur évaluée par l’expression est la valeur retournée par la fonction. Vous n’utilisez pas de clause `As` pour spécifier le type de retour.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Vous appelez l’expression lambda en passant un argument entier.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. En guise d’alternative, le même résultat est obtenu par l’exemple suivant :  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Pour créer une sous-routine d’expression lambda sur une seule ligne  
  
1. Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Sub`, comme indiqué dans l’exemple suivant.  
  
     `Dim add1 =`   `Sub`  
  
2. Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine. Notez que vous ne spécifiez pas de nom après `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. À la suite de la liste de paramètres, tapez une seule instruction en tant que corps de la sous-routine.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Vous appelez l’expression lambda en passant un argument de chaîne.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Pour créer une fonction d’expression lambda multiligne  
  
1. Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Function`, comme indiqué dans l’exemple suivant.  
  
     `Dim add1 =`   `Function`  
  
2. Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction. Notez que vous ne spécifiez pas de nom après `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Appuyez sur ENTRÉE. L’instruction `End Function` est automatiquement ajoutée.  
  
4. Dans le corps de la fonction, ajoutez le code suivant pour créer une expression et retourner la valeur. Vous n’utilisez pas de clause `As` pour spécifier le type de retour.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Vous appelez l’expression lambda en passant un argument entier.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Pour créer une sous-routine d’expression lambda multiligne  
  
1. Dans les cas où un type délégué pourrait être utilisé, tapez le mot clé `Sub`, comme indiqué dans l’exemple suivant :  
  
     `Dim add1 =`   `Sub`  
  
2. Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine. Notez que vous ne spécifiez pas de nom après `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Appuyez sur ENTRÉE. L’instruction `End Sub` est automatiquement ajoutée.  
  
4. Dans le corps de la fonction, ajoutez le code suivant à exécuter lorsque la sous-routine est appelée.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Vous appelez l’expression lambda en passant un argument de chaîne.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Exemple  
 Les expressions lambda sont généralement utilisées pour définir une fonction qui peut être passée comme argument pour un paramètre dont le type est `Delegate`. Dans l’exemple suivant, la méthode <xref:System.Diagnostics.Process.GetProcesses%2A> retourne un tableau des processus en cours d’exécution sur l’ordinateur local. La méthode <xref:System.Linq.Enumerable.Where%2A> de la classe <xref:System.Linq.Enumerable> requiert un délégué `Boolean` comme argument. L’expression lambda dans l’exemple est utilisée à cette fin. Il retourne `True` pour chaque processus qui n’a qu’un seul thread, et ceux-ci sont sélectionnés dans `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 L’exemple précédent est équivalent au code suivant, qui est écrit en [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxe :  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Enumerable>
- [Expressions lambda](./lambda-expressions.md)
- [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Guide pratique : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate (instruction)](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
