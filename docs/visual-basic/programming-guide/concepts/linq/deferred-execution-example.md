---
title: Exemple d’exécution différée (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6d1f66cbe246b609f634989625688965dd4e5c93
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351800"
---
# <a name="deferred-execution-example-visual-basic"></a>Exemple d’exécution différée (Visual Basic)
Cette rubrique montre comment l'exécution et l'évaluation différées affectent l'exécution de vos requêtes LINQ to XML.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'ordre d'exécution lors de l'utilisation d'une méthode d'extension qui utilise l'exécution différée. L'exemple déclare un tableau de trois chaînes. Il itère ensuite au sein de la collection retournée par `ConvertCollectionToUpperCase`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```console  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Notez que lors de l'itération de la collection retournée par `ConvertCollectionToUpperCase`, chaque élément est récupéré du tableau de chaînes source et converti en majuscules avant que l'élément suivant ne soit récupéré du tableau de chaînes source.  
  
 Vous pouvez constater que l'intégralité du tableau de chaînes n'est pas convertie en majuscules avant que chaque élément de la collection retournée n'ait été traité dans la boucle `foreach` dans `Main`.  
  
## <a name="see-also"></a>Voir aussi

- [Tutoriel : Exécution différée (Visual Basic) ](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
