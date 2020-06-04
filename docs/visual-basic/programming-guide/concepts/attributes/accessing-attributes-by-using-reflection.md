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
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="805e0-102">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="805e0-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="805e0-103">La définition d’attributs personnalisés et leur ajout à votre code source présentent peu d’intérêt si vous ne pouvez pas ensuite récupérer et manipuler ces informations.</span><span class="sxs-lookup"><span data-stu-id="805e0-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="805e0-104">La réflexion vous permet de récupérer les informations qui ont été définies à l’aide d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="805e0-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="805e0-105">La méthode clé est `GetCustomAttributes`. Elle retourne un tableau d’objets qui sont les équivalents des attributs du code source au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="805e0-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="805e0-106">Cette méthode a plusieurs versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="805e0-106">This method has several overloaded versions.</span></span> <span data-ttu-id="805e0-107">Pour plus d’informations, consultez <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="805e0-107">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="805e0-108">Par exemple, cette spécification d’attribut :</span><span class="sxs-lookup"><span data-stu-id="805e0-108">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="805e0-109">est semblable à celle-ci d’un point de vue conceptuel :</span><span class="sxs-lookup"><span data-stu-id="805e0-109">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="805e0-110">Toutefois, le code n’est pas exécuté tant qu’une requête n’est pas effectuée sur `SampleClass` pour obtenir les attributs.</span><span class="sxs-lookup"><span data-stu-id="805e0-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="805e0-111">L’appel de `GetCustomAttributes` sur `SampleClass` entraîne la construction et l’initialisation d’un objet `Author` comme illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="805e0-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="805e0-112">Si la classe a d’autres attributs, les autres objets attribut sont construits de la même façon.</span><span class="sxs-lookup"><span data-stu-id="805e0-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="805e0-113">`GetCustomAttributes` retourne ensuite l’objet `Author` et les autres objets attribut dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="805e0-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="805e0-114">Vous pouvez ensuite itérer sur ce tableau, déterminer quels attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations des objets attribut.</span><span class="sxs-lookup"><span data-stu-id="805e0-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="805e0-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="805e0-115">Example</span></span>

<span data-ttu-id="805e0-116">Voici un exemple complet.</span><span class="sxs-lookup"><span data-stu-id="805e0-116">Here is a complete example.</span></span> <span data-ttu-id="805e0-117">Un attribut personnalisé est défini, appliqué à plusieurs entités, puis récupéré par réflexion.</span><span class="sxs-lookup"><span data-stu-id="805e0-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="805e0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="805e0-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="805e0-119">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="805e0-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="805e0-120">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="805e0-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="805e0-121">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="805e0-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="805e0-122">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="805e0-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="805e0-123">Créer des attributs personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="805e0-123">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
