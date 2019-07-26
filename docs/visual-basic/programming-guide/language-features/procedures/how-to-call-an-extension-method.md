---
title: 'Procédure : Appeler une méthode d’extension (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512670"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Procédure : Appeler une méthode d’extension (Visual Basic)

Les méthodes d’extension vous permettent d’ajouter des méthodes à une classe existante. Une fois qu’une méthode d’extension a été déclarée et placée dans la portée, vous pouvez l’appeler comme une méthode d’instance du type qu’elle étend. Pour plus d’informations sur la façon d’écrire une méthode d' [extension, consultez Procédure: Écrire une méthode](./how-to-write-an-extension-method.md)d’extension.

 Les instructions suivantes font référence à la `PrintAndPunctuate`méthode d’extension, qui affiche l’instance de chaîne qui l’appelle, suivie de la valeur envoyée dans pour le deuxième paramètre `punc`,.

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

La méthode doit être dans la portée quand elle est appelée.

### <a name="to-call-an-extension-method"></a>Pour appeler une méthode d’extension

1. Déclarez une variable qui a le type de données du premier paramètre de la méthode d’extension. Pour `PrintAndPunctuate`, vous avez besoin <xref:System.String> d’une variable:

    ```vb
    Dim example = "Ready"
    ```

2. Cette variable appellera la méthode d’extension et sa valeur est liée au premier paramètre, `aString`. L’instruction appelante suivante s' `Ready?`affiche.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Notez que l’appel à cette méthode d’extension se présente comme un appel à l’une des <xref:System.String> méthodes d’instance qui requièrent un paramètre:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Déclarez une autre variable de chaîne et rappelez la méthode pour voir qu’elle fonctionne avec n’importe quelle chaîne.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Le résultat est le suivant: `or not!!!`.

## <a name="example"></a>Exemple
 Le code suivant est un exemple complet de la création et de l’utilisation d’une méthode d’extension simple.

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a>Voir aussi

- [Guide pratique : Écrire une méthode d’extension](./how-to-write-an-extension-method.md)
- [Méthodes d’extension](./extension-methods.md)
- [Étendue dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
