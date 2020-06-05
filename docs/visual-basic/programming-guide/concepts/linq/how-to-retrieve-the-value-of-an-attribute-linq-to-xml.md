---
title: 'Procédure : récupérer la valeur d’un attribut (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 48ad3c0ab079012793fd9eea89d52fc3a7b1698f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397802"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="102c2-102">Comment : récupérer la valeur d’un attribut (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="102c2-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="102c2-103">Cette rubrique montre comment obtenir la valeur d'attributs.</span><span class="sxs-lookup"><span data-stu-id="102c2-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="102c2-104">Vous pouvez procéder de deux manières : tout d'abord, vous pouvez convertir un objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité ; l'opérateur de conversion. explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="102c2-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="102c2-105">En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="102c2-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="102c2-106">Toutefois, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="102c2-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="102c2-107">Si vous effectuez un cast de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un attribut qui peut ou non exister.</span><span class="sxs-lookup"><span data-stu-id="102c2-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="102c2-108">Pour obtenir des exemples de cette technique, consultez [Comment : récupérer la valeur d’un élément (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="102c2-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="102c2-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="102c2-109">Example</span></span>  
 <span data-ttu-id="102c2-110">En Visual Basic, vous pouvez utiliser la propriété d'attribut intégrée pour récupérer la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="102c2-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="102c2-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="102c2-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="102c2-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="102c2-112">Example</span></span>  
 <span data-ttu-id="102c2-113">En Visual Basic, vous pouvez utiliser la propriété d'attribut intégrée pour définir la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="102c2-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="102c2-114">En outre, si vous utilisez la propriété d'attribut intégrée pour définir la valeur d'un attribut qui n'existe pas, l'attribut sera créé.</span><span class="sxs-lookup"><span data-stu-id="102c2-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="102c2-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="102c2-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="102c2-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="102c2-116">Example</span></span>  
 <span data-ttu-id="102c2-117">L'exemple suivant montre comment récupérer la valeur d'un attribut lorsque celui-ci se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="102c2-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="102c2-118">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="102c2-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="102c2-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="102c2-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="102c2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="102c2-120">See also</span></span>

- [<span data-ttu-id="102c2-121">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="102c2-121">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
