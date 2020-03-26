---
title: Expressions lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249667"
---
# <a name="lambda-expressions-visual-basic"></a>Expressions lambda (Visual Basic)

Une *expression lambda* est une fonction ou une sous-route sans nom qui peut être utilisé partout où un délégué est valide. Les expressions Lambda peuvent être des fonctions ou des sous-roues et peuvent être unifamiliales ou multi-lignes. Vous pouvez passer des valeurs de la portée actuelle à une expression lambda.

> [!NOTE]
> La `RemoveHandler` déclaration est une exception. Vous ne pouvez pas passer une expression `RemoveHandler`lambda pour le paramètre délégué de .

Vous créez des expressions `Function` lambda en utilisant le ou `Sub` le mot clé, tout comme vous créez une fonction standard ou une sous-mesure. Cependant, les expressions lambda sont incluses dans une déclaration.

L’exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur. L’exemple montre à la fois la syntaxe d’expression lambda à une seule ligne et multi-lignes pour une fonction.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

L’exemple suivant est une expression lambda qui écrit une valeur à la console. L’exemple montre à la fois la syntaxe d’expression lambda à une seule ligne et multi-lignes pour une sous-route.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Notez que dans les exemples précédents les expressions lambda sont attribuées à un nom variable. Chaque fois que vous vous référez à la variable, vous invoquez l’expression lambda. Vous pouvez également déclarer et invoquer une expression lambda en même temps, comme le montre l’exemple suivant.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Une expression lambda peut être retournée comme valeur d’un appel de fonction (comme le montre l’exemple dans la section [Contexte](#context) plus tard dans ce sujet), ou transmise comme argument à un paramètre qui prend un type de délégué, comme le montre l’exemple suivant.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda

La syntaxe d’une expression lambda ressemble à celle d’une fonction standard ou d’une sous-mesure. Les différences sont les suivantes :

- Une expression lambda n’a pas de nom.

- Les expressions Lambda ne peuvent `Overloads` `Overrides`pas avoir de modificateurs, tels que ou .

- Les fonctions lambda à une `As` seule ligne n’utilisent pas de clause pour désigner le type de retour. Au lieu de cela, le type est déduit de la valeur que le corps de l’expression lambda évalue à. Par exemple, si le corps de `cust.City = "London"`l’expression `Boolean`lambda est , son type de retour est .

- Dans les fonctions lambda multi-lignes, vous pouvez `As` soit spécifier `As` un type de retour en utilisant une clause, soit omettre la clause de sorte que le type de retour soit déduit. Lorsque `As` la clause est omise pour une fonction lambda multi-lignes, le type de `Return` retour est déduit pour être le type dominant de toutes les déclarations dans la fonction lambda multi-lignes. Le *type dominant* est un type unique que tous les autres types peuvent élargir. Si ce type unique ne peut pas être déterminé, le type dominant est le type unique que tous les autres types dans le tableau peut se rétrécir. Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`. Dans ce cas, `Option Strict` si `On`elle est réglée, une erreur de compilateur se produit.

     Par exemple, si les `Return` expressions fournies à `Integer` `Long`l’instruction contiennent des valeurs de type, , et `Double`, le tableau résultant est de type `Double`. À `Integer` `Long` la `Double` fois `Double`et élargir à et seulement . Par conséquent, `Double` est le type dominant. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Le corps d’une fonction à une seule ligne doit être une expression qui renvoie une valeur, et non une déclaration. Il n’y a pas `Return` de déclaration pour les fonctions à une seule ligne. La valeur retournée par la fonction à une seule ligne est la valeur de l’expression dans le corps de la fonction.

- Le corps d’une sous-ligne d’une seule ligne doit être une déclaration à une seule ligne.

- Les fonctions et les sous-roues à `End Function` `End Sub` une seule ligne n’incluent pas une ou une déclaration.

- Vous pouvez spécifier le type de `As` données d’un paramètre d’expression lambda en utilisant le mot clé, ou le type de données du paramètre peut être déduit. Tous les paramètres doivent avoir des types de données spécifiés ou tous doivent être déduits.

- `Optional`et `Paramarray` les paramètres ne sont pas autorisés.

- Les paramètres génériques ne sont pas autorisés.

## <a name="async-lambdas"></a>Lambdas asynchrones

Vous pouvez facilement créer des expressions lambda et des déclarations qui intègrent un traitement asynchrone en utilisant les mots clés [Async](../../../../visual-basic/language-reference/modifiers/async.md) et [Await Operator.](../../../../visual-basic/language-reference/operators/await-operator.md) Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Vous pouvez ajouter le même gestionnaire d’événement en utilisant un lambda async dans une [déclaration AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Pour ajouter ce gestionnaire, ajoutez un modificateur `Async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Pour plus d’informations sur la façon de créer et d’utiliser des méthodes async, voir [Programmation asynchrone avec Async et Await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Context

Une expression lambda partage son contexte avec la portée dans laquelle elle est définie. Il a les mêmes droits d’accès que n’importe quel code écrit dans la portée contenant. Cela comprend l’accès aux variables, `Me`fonctions et sous-marins des membres, ainsi qu’aux paramètres et aux variables locales dans la portée de confinement.

L’accès aux variables et aux paramètres locaux dans la portée de confinement peut s’étendre au-delà de la durée de vie de cette portée. Tant qu’un délégué se référant à une expression lambda n’est pas disponible pour la collecte des ordures, l’accès aux variables dans l’environnement d’origine est conservé. Dans l’exemple `target` suivant, `makeTheGame`variable est locale à , `playTheGame` la méthode dans laquelle l’expression lambda est définie. Notez que l’expression lambda `Main`retournée, assignée à `target` `takeAGuess` , a toujours accès à la variable locale .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

L’exemple suivant montre le large éventail de droits d’accès de l’expression lambda imbriquée. Lorsque l’expression lambda retournée `Main` `aDel`est exécutée à partir de , il accède à ces éléments:

- Un domaine de la classe dans lequel il est défini:`aField`

- Une propriété de la classe dans laquelle elle est définie :`aProp`

- Un paramètre `functionWithNestedLambda`de méthode , dans lequel il est défini:`level1`

- Une variable `functionWithNestedLambda`locale de :`localVar`

- Un paramètre de l’expression lambda dans lequel il est imbriqué:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Conversion à un type de délégué

Une expression lambda peut être implicitement convertie en un type de délégué compatible. Pour plus d’informations sur les exigences générales de compatibilité, voir [Conversion déléguée détendue](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Par exemple, l’exemple de code suivant montre une `Func(Of Integer, Boolean)` expression lambda qui se convertit implicitement à ou une signature de délégué correspondant.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

L’exemple de code suivant montre une expression `Sub(Of Double, String, Double)` lambda qui se convertit implicitement à ou une signature de délégué correspondant.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Lorsque vous attribuez des expressions lambda aux délégués ou les transmettez comme arguments aux procédures, vous pouvez spécifier les noms de paramètres, mais omettre leurs types de données, en laissant les types être prélevés sur le délégué.

## <a name="examples"></a>Exemples

- L’exemple suivant définit une expression `True` lambda qui renvoie si l’argument de type valeur nulle a une valeur assignée, et `False` si sa valeur est `Nothing`.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- L’exemple suivant définit une expression lambda qui renvoie l’index du dernier élément dans un tableau.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Types de valeur nuls](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Comment : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Comment : créer une expression lambda](./how-to-create-a-lambda-expression.md)
- [Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
