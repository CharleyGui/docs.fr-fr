---
title: 'Procédure : Récupérer une collection d’attributs (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: b1721de5ac396faab010dab691bfd88991bad638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253433"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="3910b-102">Procédure : Récupérer une collection d’attributs (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3910b-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3910b-103">Cette rubrique présente la méthode <xref:System.Xml.Linq.XElement.Attributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="3910b-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="3910b-104">Cette méthode récupère les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="3910b-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3910b-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="3910b-105">Example</span></span>  
 <span data-ttu-id="3910b-106">L’exemple suivant montre comment itérer au sein de la collection d’attributs d’un élément.</span><span class="sxs-lookup"><span data-stu-id="3910b-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="3910b-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3910b-107">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="3910b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3910b-108">See also</span></span>

- [<span data-ttu-id="3910b-109">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3910b-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
