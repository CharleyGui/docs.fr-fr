---
title: Comment exécuter des arborescences d’expressions (C#)
description: Découvrez comment exécuter une arborescence de l’expression pour retourner une valeur ou effectuer une action comme appeler une méthode.
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 19c3e639d64a44d180c75964261569dc0d6c2d89
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154013"
---
# <a name="how-to-execute-expression-trees-c"></a>Comment exécuter des arborescences d’expressions (C#)

Cette rubrique montre comment exécuter une arborescence d’expressions. L’exécution d’une arborescence d’expressions peut retourner une valeur, ou elle peut simplement effectuer une action telle que l’appel d’une méthode.  
  
 Seules les arborescences d’expressions qui représentent des expressions lambda peuvent être exécutées. Les arborescences d’expressions qui représentent des expressions lambda peuvent être de type <xref:System.Linq.Expressions.LambdaExpression> ou <xref:System.Linq.Expressions.Expression%601>. Pour exécuter ces arborescences d’expressions, appelez la méthode <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> pour créer un délégué exécutable, puis appelez le délégué.  
  
> [!NOTE]
> Si le type du délégué n’est pas connu, autrement dit si l’expression lambda est de type <xref:System.Linq.Expressions.LambdaExpression> et non <xref:System.Linq.Expressions.Expression%601>, vous devez appeler la méthode <xref:System.Delegate.DynamicInvoke%2A> sur le délégué au lieu de l’appeler directement.  
  
 Si une arborescence d’expressions ne représente pas une expression lambda, vous pouvez créer une expression lambda ayant l’arborescence d’expressions d’origine comme corps, en appelant la méthode <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>. Ensuite, vous pouvez exécuter l’expression lambda comme décrit plus haut dans cette section.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant montre comment exécuter une arborescence d’expressions qui représente l’élévation d’un nombre à une puissance en créant une expression lambda et en l’exécutant. Le résultat, qui représente le nombre élevé à la puissance, est affiché.  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Incluez l’espace de noms System.Linq.Expressions.  
  
## <a name="see-also"></a>Voir aussi

- [Arborescences d’expressions (C#)](./index.md)
- [Comment modifier les arborescences d’expressions (C#)](./how-to-modify-expression-trees.md)
