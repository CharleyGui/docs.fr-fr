---
title: Sous-expression (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701335"
---
# <a name="sub-expression-visual-basic"></a>Sous-expression (Visual Basic)
Déclare les paramètres et le code qui définissent une expression lambda de sous-routine.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`parameterlist`|facultatif. Liste des noms de variables locales qui représentent les paramètres de la procédure. Les parenthèses doivent être présentes même lorsque la liste est vide. Pour plus d'informations, consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Obligatoire. Instruction unique.|  
|`statements`|Obligatoire. Liste d’instructions.|  
  
## <a name="remarks"></a>Notes  
 Une *expression lambda* est une sous-routine qui n’a pas de nom et qui exécute une ou plusieurs instructions. Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument pour `RemoveHandler`. Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec des délégués, consultez [instruction de délégué](../../../visual-basic/language-reference/statements/delegate-statement.md) et [conversion simplifiée](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)des délégués.  
  
## <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda  
 La syntaxe d’une expression lambda ressemble à celle d’une sous-routine standard. Les différences sont les suivantes :  
  
- Une expression lambda n’a pas de nom.  
  
- Une expression lambda ne peut pas avoir de modificateur, tel que `Overloads` ou `Overrides`.  
  
- Le corps d’une expression lambda sur une seule ligne doit être une instruction, et non une expression. Le corps peut se composer d’un appel à une procédure Sub, mais pas d’un appel à une procédure Function.  
  
- Dans une expression lambda, tous les paramètres doivent avoir des types de données spécifiés ou tous les paramètres doivent être déduits.  
  
- Les paramètres facultatifs et `ParamArray` ne sont pas autorisés dans les expressions lambda.  
  
- Les paramètres génériques ne sont pas autorisés dans les expressions lambda.  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’expression lambda qui écrit une valeur dans la console. L’exemple montre la syntaxe d’expression lambda à ligne unique et multiligne pour une sous-routine. Pour obtenir plus d’exemples, consultez [expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
- [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
