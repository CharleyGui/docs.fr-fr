---
title: Comment récupérer la valeur d’un LINQ to XML d’attributs
description: Récupérez la valeur d’un attribut. Vous pouvez convertir un XAttribute en type souhaité ou utiliser la propriété XAttribute. Value.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553652"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a><span data-ttu-id="4f262-104">Comment récupérer la valeur d’un attribut (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4f262-104">How to retrieve the value of an attribute (LINQ to XML)</span></span>

<span data-ttu-id="4f262-105">Cet article explique comment obtenir la valeur des attributs.</span><span class="sxs-lookup"><span data-stu-id="4f262-105">This article shows how to obtain the value of attributes.</span></span> <span data-ttu-id="4f262-106">Vous pouvez procéder de deux manières : tout d'abord, vous pouvez convertir un objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité ; l'opérateur de conversion. explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="4f262-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="4f262-107">En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f262-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="4f262-108">Toutefois, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="4f262-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="4f262-109">Si vous effectuez un cast de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un attribut qui peut ou non exister.</span><span class="sxs-lookup"><span data-stu-id="4f262-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="4f262-110">Pour obtenir des exemples de cette technique, consultez [Comment récupérer la valeur d’un élément](retrieve-value-element.md).</span><span class="sxs-lookup"><span data-stu-id="4f262-110">For examples of this technique, see [How to retrieve the value of an element](retrieve-value-element.md).</span></span>

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a><span data-ttu-id="4f262-111">Exemple : utiliser un cast pour récupérer la valeur d’un attribut</span><span class="sxs-lookup"><span data-stu-id="4f262-111">Example: Use a cast to retrieve the value of an attribute</span></span>

<span data-ttu-id="4f262-112">Pour récupérer la valeur d’un attribut en C#, vous effectuez un cast de l' <xref:System.Xml.Linq.XAttribute> objet vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="4f262-112">To retrieve the value of an attribute in C#, you cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span> <span data-ttu-id="4f262-113">Dans Visual Basic, vous pouvez utiliser la propriété d’attribut intégrée pour récupérer la valeur.</span><span class="sxs-lookup"><span data-stu-id="4f262-113">In Visual Basic, you can use the integrated attribute property to retrieve the value.</span></span>

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

<span data-ttu-id="4f262-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4f262-114">This example produces the following output:</span></span>

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="4f262-115">Exemple : utiliser un cast pour extraire du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="4f262-115">Example: Use a cast to retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="4f262-116">L’exemple suivant montre comment récupérer la valeur d’un attribut si l’attribut se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4f262-116">The following example shows how to retrieve the value of an attribute if the attribute is in a namespace.</span></span> <span data-ttu-id="4f262-117">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4f262-117">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>
        Dim str As String = root.@aw:Attr
        Console.WriteLine(str)
    End Sub
End Module
```

<span data-ttu-id="4f262-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4f262-118">This example produces the following output:</span></span>

```output
abcde
```

## <a name="see-also"></a><span data-ttu-id="4f262-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f262-119">See also</span></span>

- [<span data-ttu-id="4f262-120">Vue d’ensemble des axes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="4f262-120">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
