---
title: L’utilisation de la variable d’itération dans une expression lambda peut provoquer des résultats inattendus
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: d0deea94084565ea91debe2b6db30def4cd9e00e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161489"
---
# <a name="bc42324-using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>BC42324 : l’utilisation de la variable d’itération dans une expression lambda peut avoir des résultats inattendus

L’utilisation de la variable d’itération dans une expression lambda peut avoir des résultats inattendus. Au lieu de cela, créez une variable locale dans la boucle et affectez-lui la valeur de la variable d’itération.

 Cet avertissement apparaît lorsque vous utilisez une variable d’itération de boucle dans une expression lambda qui est déclarée à l’intérieur de la boucle. Par exemple, l’exemple suivant provoque l’affichage de l’avertissement.

```vb
For i As Integer = 1 To 10
    ' The warning is given for the use of i.
    Dim exampleFunc As Func(Of Integer) = Function() i
Next
```

 L’exemple suivant montre les résultats inattendus qui peuvent se produire.

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            array1(i) = Function() i
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

 La `For` boucle crée un tableau d’expressions lambda, chacune d’elles retournant la valeur de la variable d’itération de la boucle `i` . Lorsque les expressions lambda sont évaluées dans la `For Each` boucle, vous pouvez vous attendre à ce que 0, 1, 2, 3 et 4 s’affichent, les valeurs successives de `i` dans la `For` boucle. Au lieu de cela, vous voyez la valeur finale de l' `i` affichage cinq fois :

 `5`

 `5`

 `5`

 `5`

 `5`

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC42324

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Assignez la valeur de la variable d’itération à une variable locale et utilisez la variable locale dans l’expression lambda.

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            Dim j = i
            array1(i) = Function() j
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

- [Expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
