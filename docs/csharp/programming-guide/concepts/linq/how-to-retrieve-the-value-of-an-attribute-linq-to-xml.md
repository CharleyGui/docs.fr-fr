---
title: Comment récupérer la valeur d’un attribut (LINQ to XML) (C#)
description: Découvrez comment obtenir la valeur d’un attribut. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301552"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="0c929-104">Comment récupérer la valeur d’un attribut (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0c929-104">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0c929-105">Cette rubrique montre comment obtenir la valeur d'attributs.</span><span class="sxs-lookup"><span data-stu-id="0c929-105">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="0c929-106">Vous pouvez procéder de deux manières : tout d'abord, vous pouvez convertir un objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité ; l'opérateur de conversion. explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="0c929-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="0c929-107">En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c929-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="0c929-108">Toutefois, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="0c929-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="0c929-109">Si vous effectuez un cast de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un attribut qui peut ou non exister.</span><span class="sxs-lookup"><span data-stu-id="0c929-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="0c929-110">Pour obtenir des exemples de cette technique, consultez [Comment récupérer la valeur d’un élément (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0c929-110">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c929-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c929-111">Example</span></span>  
 <span data-ttu-id="0c929-112">Pour récupérer la valeur d'un attribut, il vous suffit de convertir l'objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="0c929-112">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0c929-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0c929-113">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0c929-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c929-114">Example</span></span>  
 <span data-ttu-id="0c929-115">L'exemple suivant montre comment récupérer la valeur d'un attribut lorsque celui-ci se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0c929-115">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="0c929-116">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0c929-116">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0c929-117">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0c929-117">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c929-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c929-118">See also</span></span>

- [<span data-ttu-id="0c929-119">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0c929-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
