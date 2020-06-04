---
title: Accès à des attributs à l'aide de la réflexion
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: c0da5c4ae00eb2bc80b10f63f4bfd39763445e55
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400756"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Accéder à des attributs à l’aide de la réflexion (Visual Basic)

La définition d’attributs personnalisés et leur ajout à votre code source présentent peu d’intérêt si vous ne pouvez pas ensuite récupérer et manipuler ces informations. La réflexion vous permet de récupérer les informations qui ont été définies à l’aide d’attributs personnalisés. La méthode clé est `GetCustomAttributes`. Elle retourne un tableau d’objets qui sont les équivalents des attributs du code source au moment de l’exécution. Cette méthode a plusieurs versions surchargées. Pour plus d’informations, consultez <xref:System.Attribute>.

Par exemple, cette spécification d’attribut :

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 est semblable à celle-ci d’un point de vue conceptuel :

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

Toutefois, le code n’est pas exécuté tant qu’une requête n’est pas effectuée sur `SampleClass` pour obtenir les attributs. L’appel de `GetCustomAttributes` sur `SampleClass` entraîne la construction et l’initialisation d’un objet `Author` comme illustré ci-dessus. Si la classe a d’autres attributs, les autres objets attribut sont construits de la même façon. `GetCustomAttributes` retourne ensuite l’objet `Author` et les autres objets attribut dans un tableau. Vous pouvez ensuite itérer sur ce tableau, déterminer quels attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations des objets attribut.

## <a name="example"></a>Exemple

Voici un exemple complet. Un attribut personnalisé est défini, appliqué à plusieurs entités, puis récupéré par réflexion.

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Guide de programmation Visual Basic](../../index.md)
- [Récupération des informations stockées dans les attributs](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Réflexion (Visual Basic)](../reflection.md)
- [Attributs (Visual Basic)](../../../language-reference/attributes.md)
- [Créer des attributs personnalisés (Visual Basic)](creating-custom-attributes.md)
