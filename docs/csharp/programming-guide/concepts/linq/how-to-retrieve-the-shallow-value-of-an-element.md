---
title: Comment récupérer la valeur superficielle d’un élément (C)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347446"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="7cd3c-102">Comment récupérer la valeur superficielle d’un élément (C)</span><span class="sxs-lookup"><span data-stu-id="7cd3c-102">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="7cd3c-103">Cette rubrique montre comment obtenir la valeur superficielle d'un élément.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="7cd3c-104">La valeur superficielle est la valeur de l’élément spécifique uniquement, par opposition à la valeur profonde, qui inclut les valeurs de tous les éléments descendants concaténés dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="7cd3c-105">Lorsque vous extrayez la valeur d'un élément par le biais d'une conversion ou en utilisant la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>, vous extrayez une valeur profonde.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="7cd3c-106">Pour extraire la valeur superficielle, vous pouvez utiliser la méthode d'extension `ShallowValue`, comme dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="7cd3c-107">L'extraction de la valeur superficielle est utile lorsque vous voulez sélectionner des éléments en fonction de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="7cd3c-108">L'exemple suivant déclare une méthode d'extension qui extrait la valeur superficielle d'un élément.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="7cd3c-109">Il utilise ensuite la méthode d’extension dans une requête pour répertorier tous les éléments qui contiennent une valeur calculée.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cd3c-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7cd3c-110">Example</span></span>  
 <span data-ttu-id="7cd3c-111">Le fichier texte suivant, Report.xml, est la source pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="7cd3c-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7cd3c-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7cd3c-112">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="7cd3c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cd3c-113">See also</span></span>

- [<span data-ttu-id="7cd3c-114">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7cd3c-114">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
