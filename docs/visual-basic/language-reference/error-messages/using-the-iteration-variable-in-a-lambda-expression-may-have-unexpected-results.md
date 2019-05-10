---
title: L’utilisation de la variable d’itération dans une expression lambda peut provoquer des résultats inattendus
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 3335da503b6fb9c33e44266997cc945214a3a365
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913073"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>L’utilisation de la variable d’itération dans une expression lambda peut provoquer des résultats inattendus
L’utilisation de la variable d’itération dans une expression lambda peut avoir des résultats inattendus. Au lieu de cela, créez une variable locale dans la boucle et affectez-lui la valeur de la variable d’itération.  
  
 Cet avertissement s’affiche lorsque vous utilisez une variable d’itération de boucle dans une expression lambda qui est déclarée à l’intérieur de la boucle. Par exemple, l’exemple suivant provoque l’avertissement apparaît.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 L’exemple suivant montre les résultats inattendus peuvent se produire.  
  
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
  
 Le `For` boucle crée un tableau d’expressions lambda, chacune d'entre elles retourne la valeur de la variable d’itération de boucle `i`. Lorsque les expressions lambda sont évaluées dans le `For Each` boucle, vous attendez peut-être à voir 0, 1, 2, 3 et 4 affichés, les valeurs consécutives de `i` dans le `For` boucle. Au lieu de cela, vous voyez la valeur finale de `i` affichée cinq fois :  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42324  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Affectez la valeur de la variable d’itération à une variable locale et utilisez la variable locale dans l’expression lambda.  
  
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

- [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
