---
title: Expression Trees
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266415"
---
# <a name="expression-trees-visual-basic"></a>Arborescences d’expressions (Visual Basic)
Les arborescences d'expressions représentent du code dans une structure de données arborescente, où chaque nœud est une expression, par exemple un appel de méthode ou une opération binaire comme `x < y`.  
  
 Vous pouvez compiler et exécuter du code représenté par des arborescences d'expressions. Ceci permet la modification dynamique du code exécutable, l'exécution de requêtes LINQ dans différentes bases de données et la création de requêtes dynamiques. Pour plus d’informations sur les arborescences d’expressions dans LINQ, consultez [Guide pratique pour utiliser des arborescences d’expressions pour générer des requêtes dynamiques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Les arborescences d’expressions sont également utilisées dans l’environnement d’exécution de langage dynamique (DLR, Dynamic Language Runtime) pour fournir une interopérabilité entre les langages dynamiques et .NET Framework, ainsi que pour permettre aux writers de compilateur d’émettre des arborescences d’expressions au lieu d’utiliser le langage intermédiaire MSIL (Microsoft Intermediate Language). Pour plus d’informations sur le DLR, consultez [Vue d’ensemble du Dynamic Language Runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Le compilateur C# ou Visual Basic peut créer pour vous une arborescence d'expressions basée sur une expression lambda anonyme. Vous pouvez aussi créer manuellement des arborescences d'expressions en utilisant l'espace de noms <xref:System.Linq.Expressions>.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Création d’arborescences d’expressions à partir d’expressions lambda  
 Quand une expression lambda est affectée à une variable de type <xref:System.Linq.Expressions.Expression%601>, le compilateur produit du code pour générer une arborescence d'expressions qui représente l'expression lambda.  
  
 Le compilateur Visual Basic peut générer des arborescences d’expressions seulement à partir d’expressions lambda (ou de lambdas sur une seule ligne). Ils ne peuvent pas analyser des lambdas d'instruction (ou lambdas multilignes). Pour plus d’informations sur les expressions lambda en Visual Basic, consultez [Expressions lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Les exemples de code suivants montrent comment le compilateur Visual Basic crée une arborescence d’expressions qui représente l’expression lambda `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Création d’arborescences d’expressions à l’aide de l’API  
 Pour créer des arborescences d'expressions à l'aide de l'API, utilisez la classe <xref:System.Linq.Expressions.Expression>. Cette classe contient des méthodes de fabrique statiques qui créent des nœuds d'arborescence d'expressions de types spécifiques, par exemple <xref:System.Linq.Expressions.ParameterExpression>, qui représente une variable ou un paramètre, ou <xref:System.Linq.Expressions.MethodCallExpression>, qui représente un appel de méthode. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> et les autres types spécifiques à une expression sont également définis dans l'espace de noms <xref:System.Linq.Expressions>. Ces types dérivent du type abstrait <xref:System.Linq.Expressions.Expression>.  
  
 L’exemple de code suivant montre comment créer une arborescence d’expressions qui représente l’expression lambda `Function(num) num < 5` à l’aide de l’API.  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 Dans le .NET Framework 4 ou ultérieur, l’API des arborescences d’expressions prend également en charge les affectations et les expressions de flux de contrôle, comme les boucles, les blocs conditionnels et les blocs `try-catch`. À l’aide de l’API, vous pouvez créer des arborescences d’expressions qui sont plus complexes que celles qui peuvent être créées à partir d’expressions lambda par le compilateur Visual Basic. L’exemple suivant montre comment créer une arborescence d’expressions qui calcule la factorielle d’un nombre.  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

Pour plus d’informations, consultez [Génération de méthodes dynamiques avec des arborescences d’expressions dans Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/) (ou version ultérieure).
  
## <a name="parsing-expression-trees"></a>Analyse des arborescences d’expressions  
 L’exemple de code suivant montre comment l’arborescence d’expressions qui représente l’expression lambda `Function(num) num < 5` peut être décomposée selon ses différentes parties.  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a>Immuabilité des arborescences d’expressions  
 Les arborescences d'expressions doivent être immuables. Cela signifie que si vous voulez modifier une arborescence d'expressions, vous devez construire une nouvelle arborescence d'expressions en copiant l'arborescence existante et en y remplaçant les nœuds. Vous pouvez utiliser un visiteur d’arborescence d’expressions pour parcourir l’arborescence d’expressions existante. Pour plus d’informations, consultez [Guide pratique pour modifier des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Compilation des arborescences d’expressions  
 Le type <xref:System.Linq.Expressions.Expression%601> fournit la méthode <xref:System.Linq.Expressions.Expression%601.Compile%2A> qui compile le code représenté par une arborescence d'expressions en un délégué exécutable.  
  
 L’exemple de code suivant montre comment compiler une arborescence d’expressions et exécuter le code résultant.  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 Pour plus d’informations, consultez [Guide pratique pour exécuter des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Expressions>
- [Guide pratique pour exécuter des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Guide pratique pour modifier des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Expressions lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Aperçu dynamique du temps d’exécution du langage](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Concepts de programmation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
