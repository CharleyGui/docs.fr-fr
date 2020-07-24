---
title: Comment récupérer une collection d’attributs (LINQ to XML) (C#)
description: La méthode d’attributs en C# récupère les attributs d’un élément. Cet exemple LINQ to XML effectue une itération au sein de la collection d’attributs d’un élément.
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103382"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="2e44d-104">Comment récupérer une collection d’attributs (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2e44d-104">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2e44d-105">Cette rubrique présente la méthode <xref:System.Xml.Linq.XElement.Attributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e44d-105">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="2e44d-106">Cette méthode récupère les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="2e44d-106">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e44d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e44d-107">Example</span></span>  
 <span data-ttu-id="2e44d-108">L’exemple suivant montre comment itérer au sein de la collection d’attributs d’un élément.</span><span class="sxs-lookup"><span data-stu-id="2e44d-108">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="2e44d-109">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2e44d-109">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e44d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e44d-110">See also</span></span>

- [<span data-ttu-id="2e44d-111">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2e44d-111">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
