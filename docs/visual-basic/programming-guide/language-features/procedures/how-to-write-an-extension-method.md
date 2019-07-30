---
title: 'Procédure : Écrire une méthode d’extension (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631032"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Procédure : Écrire une méthode d’extension (Visual Basic)
Les méthodes d’extension vous permettent d’ajouter des méthodes à une classe existante. La méthode d’extension peut être appelée comme s’il s’agissait d’une instance de cette classe.

### <a name="to-define-an-extension-method"></a>Pour définir une méthode d’extension

1. Ouvrez une application de Visual Basic nouvelle ou existante dans Visual Studio.

2. En haut du fichier dans lequel vous souhaitez définir une méthode d’extension, incluez l’instruction d’importation suivante:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. Dans un module de votre application nouvelle ou existante, commencez la définition de la méthode par l’attribut d’extension:

    ```vb
    <Extension()>
    ```

4. Déclarez votre méthode de manière ordinaire, sauf que le type du premier paramètre doit être le type de données que vous souhaitez étendre.

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Exemple
 L’exemple suivant déclare une méthode d’extension dans un `StringExtensions`module. Un deuxième module, `Module1`, importe `StringExtensions` et appelle la méthode. La méthode d’extension doit être dans la portée quand elle est appelée. La méthode `PrintAndPunctuate` d’extension <xref:System.String> étend la classe avec une méthode qui affiche l’instance de chaîne suivie d’une chaîne de symboles de ponctuation envoyée en tant que paramètre.
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 Notez que la méthode est définie avec deux paramètres et appelée avec un seul. Le premier paramètre, `aString`, dans la définition de méthode est lié `example`à, l’instance `String` de qui appelle la méthode. Voici la sortie de l’exemple :
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Méthodes d’extension](./extension-methods.md)
- [Module (instruction)](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Étendue dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
