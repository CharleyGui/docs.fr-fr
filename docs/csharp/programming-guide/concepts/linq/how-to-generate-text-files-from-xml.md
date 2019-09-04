---
title: 'Procédure : Générer des fichiers texte à partir de données XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 76fcca69236ef97374855ebbb19259aa5e119ea0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253595"
---
# <a name="how-to-generate-text-files-from-xml-c"></a><span data-ttu-id="2abbb-102">Procédure : Générer des fichiers texte à partir de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2abbb-102">How to: Generate Text Files from XML (C#)</span></span>
<span data-ttu-id="2abbb-103">Cet exemple montre comment générer un fichier de valeurs séparées par des virgules (CSV) à partir d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="2abbb-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2abbb-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="2abbb-104">Example</span></span>  
 <span data-ttu-id="2abbb-105">La version C# de cet exemple utilise la syntaxe de méthode et l'opérateur `Aggregate` pour générer un fichier CSV à partir d'un document XML dans une expression simple.</span><span class="sxs-lookup"><span data-stu-id="2abbb-105">The C# version of this example uses method syntax and the `Aggregate` operator to generate a CSV file from an XML document in a single expression.</span></span> <span data-ttu-id="2abbb-106">Pour plus d’informations, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2abbb-106">For more information, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="2abbb-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="2abbb-107">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 <span data-ttu-id="2abbb-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2abbb-108">This code produces the following output:</span></span>  
  
```output  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="2abbb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2abbb-109">See also</span></span>

- [<span data-ttu-id="2abbb-110">Projections et transformations (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2abbb-110">Projections and Transformations (LINQ to XML) (C#)</span></span>](./projections-and-transformations-linq-to-xml.md)
