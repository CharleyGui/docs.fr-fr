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
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406701"
---
# <a name="lambda-expressions-visual-basic"></a>Expressions lambda (Visual Basic)

Une *expression lambda* est une fonction ou une sous-routine sans nom qui peut être utilisée partout où un délégué est valide. Les expressions lambda peuvent être des fonctions ou des sous-routines et peuvent être sur une ou plusieurs lignes. Vous pouvez passer des valeurs de la portée actuelle à une expression lambda.

> [!NOTE]
> L' `RemoveHandler` instruction est une exception. Vous ne pouvez pas passer une expression lambda dans pour le paramètre de délégué de `RemoveHandler` .

Vous créez des expressions lambda à l’aide du `Function` `Sub` mot clé ou, de la même façon que vous créez une fonction ou une sous-routine standard. Toutefois, les expressions lambda sont incluses dans une instruction.

L’exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur. L’exemple montre la syntaxe d’expression lambda sur une seule ligne et sur plusieurs lignes pour une fonction.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

L’exemple suivant est une expression lambda qui écrit une valeur dans la console. L’exemple montre la syntaxe de l’expression lambda sur une seule ligne et sur plusieurs lignes pour une sous-routine.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Notez que dans les exemples précédents, les expressions lambda sont assignées à un nom de variable. Chaque fois que vous faites référence à la variable, vous appelez l’expression lambda. Vous pouvez également déclarer et appeler une expression lambda en même temps, comme illustré dans l’exemple suivant.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Une expression lambda peut être retournée en tant que valeur d’un appel de fonction (comme indiqué dans l’exemple de la section [Context](#context) plus loin dans cette rubrique) ou passée comme argument à un paramètre qui accepte un type délégué, comme indiqué dans l’exemple suivant.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda

La syntaxe d’une expression lambda ressemble à celle d’une fonction ou d’une sous-routine standard. Les différences sont les suivantes :

- Une expression lambda n’a pas de nom.

- Les expressions lambda ne peuvent pas avoir de modificateurs, tels que `Overloads` ou `Overrides` .

- Les fonctions lambda sur une seule ligne n’utilisent pas `As` de clause pour désigner le type de retour. Au lieu de cela, le type est déduit de la valeur à laquelle le corps de l’expression lambda correspond. Par exemple, si le corps de l’expression lambda est `cust.City = "London"` , son type de retour est `Boolean` .

- Dans les fonctions lambda sur plusieurs lignes, vous pouvez spécifier un type de retour à l’aide d’une `As` clause, ou omettre la `As` clause afin que le type de retour soit déduit. Lorsque la `As` clause est omise pour une fonction lambda multiligne, le type de retour est déduit comme étant le type dominant de toutes les `Return` instructions dans la fonction lambda multiligne. Le *type dominant* est un type unique auquel tous les autres types peuvent s’étendre. Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types du tableau peuvent se limiter. Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`. Dans ce cas, si `Option Strict` a la valeur `On` , une erreur de compilateur se produit.

     Par exemple, si les expressions fournies à l' `Return` instruction contiennent des valeurs de type `Integer` , `Long` et `Double` , le tableau résultant est de type `Double` . `Integer`Et `Long` s’étendent à `Double` et à uniquement `Double` . Par conséquent, `Double` est le type dominant. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).

- Le corps d’une fonction sur une seule ligne doit être une expression qui retourne une valeur, et non une instruction. Il n’existe aucune `Return` instruction pour les fonctions à ligne unique. La valeur retournée par la fonction sur une seule ligne est la valeur de l’expression dans le corps de la fonction.

- Le corps d’une sous-routine sur une seule ligne doit être une instruction sur une seule ligne.

- Les fonctions et sous-routines sur une seule ligne n’incluent pas d' `End Function` `End Sub` instruction ou.

- Vous pouvez spécifier le type de données d’un paramètre d’expression lambda à l’aide du `As` mot clé, ou le type de données du paramètre peut être déduit. Tous les paramètres doivent avoir des types de données spécifiés ou tous doivent être déduits.

- `Optional`les `Paramarray` paramètres et ne sont pas autorisés.

- Les paramètres génériques ne sont pas autorisés.

## <a name="async-lambdas"></a>Lambdas asynchrones

Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l’aide des mots clés [Async](../../../language-reference/modifiers/async.md) et await de l' [opérateur](../../../language-reference/operators/await-operator.md) . Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.

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

Vous pouvez ajouter le même gestionnaire d’événements en utilisant une expression lambda asynchrone dans une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md). Pour ajouter ce gestionnaire, ajoutez un modificateur `Async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.

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

Pour plus d’informations sur la création et l’utilisation des méthodes Async, consultez [programmation asynchrone avec Async et await](../../concepts/async/index.md).

## <a name="context"></a>Context

Une expression lambda partage son contexte avec la portée dans laquelle elle est définie. Il possède les mêmes droits d’accès que tout code écrit dans l’étendue contenante. Cela comprend l’accès aux variables membres, aux fonctions, aux Subs, `Me` , et aux paramètres et variables locales dans l’étendue contenante.

L’accès aux variables locales et aux paramètres dans l’étendue contenante peut s’étendre au-delà de la durée de vie de cette étendue. Tant qu’un délégué qui fait référence à une expression lambda n’est pas disponible pour garbage collection, l’accès aux variables dans l’environnement d’origine est conservé. Dans l’exemple suivant, la variable `target` est locale à `makeTheGame` , la méthode dans laquelle l’expression lambda `playTheGame` est définie. Notez que l’expression lambda retournée, assignée à `takeAGuess` dans `Main` , a toujours accès à la variable locale `target` .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

L’exemple suivant illustre la large gamme de droits d’accès de l’expression lambda imbriquée. Lorsque l’expression lambda retournée est exécutée à partir de `Main` sous `aDel` , elle accède à ces éléments :

- Champ de la classe dans laquelle il est défini :`aField`

- Une propriété de la classe dans laquelle elle est définie :`aProp`

- Paramètre de la méthode `functionWithNestedLambda` , dans lequel elle est définie :`level1`

- Une variable locale `functionWithNestedLambda` :`localVar`

- Paramètre de l’expression lambda dans laquelle il est imbriqué :`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Convertir en un type délégué

Une expression lambda peut être implicitement convertie en un type délégué compatible. Pour plus d’informations sur les exigences générales en matière de compatibilité, consultez la section [conversion souple des délégués](../delegates/relaxed-delegate-conversion.md). Par exemple, l’exemple de code suivant montre une expression lambda qui convertit implicitement en `Func(Of Integer, Boolean)` ou une signature de délégué correspondante.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

L’exemple de code suivant montre une expression lambda qui convertit implicitement en `Sub(Of Double, String, Double)` ou une signature de délégué correspondante.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Quand vous assignez des expressions lambda à des délégués ou les passez comme arguments à des procédures, vous pouvez spécifier les noms des paramètres, mais omettre leurs types de données, ce qui permet aux types d’être extraits du délégué.

## <a name="examples"></a>Exemples

- L’exemple suivant définit une expression lambda qui retourne `True` si l’argument de type valeur Nullable a une valeur assignée, et `False` si sa valeur est `Nothing` .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- L’exemple suivant définit une expression lambda qui retourne l’index du dernier élément d’un tableau.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Introduction à LINQ en Visual Basic](../linq/introduction-to-linq.md)
- [Délégués](../delegates/index.md)
- [Function (instruction)](../../../language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [Types valeur Nullable](../data-types/nullable-value-types.md)
- [Comment : passer des procédures à une autre procédure en Visual Basic](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Comment : créer une expression lambda](./how-to-create-a-lambda-expression.md)
- [Conversion simplifiée des délégués](../delegates/relaxed-delegate-conversion.md)
