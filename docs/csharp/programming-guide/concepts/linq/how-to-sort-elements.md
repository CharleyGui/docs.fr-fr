---
title: Comment trier les éléments (C)
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7fad9fcb43905072c88a5704c56672917bfc377c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347365"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="862ab-102">Comment trier les éléments (C)</span><span class="sxs-lookup"><span data-stu-id="862ab-102">How to sort elements (C#)</span></span>
<span data-ttu-id="862ab-103">Cet exemple montre comment écrire une requête qui trie ses résultats.</span><span class="sxs-lookup"><span data-stu-id="862ab-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="862ab-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="862ab-104">Example</span></span>  
 <span data-ttu-id="862ab-105">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="862ab-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="862ab-106">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="862ab-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="862ab-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="862ab-107">Example</span></span>  
 <span data-ttu-id="862ab-108">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="862ab-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="862ab-109">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="862ab-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="862ab-110">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="862ab-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="862ab-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="862ab-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="862ab-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="862ab-112">See also</span></span>

- [<span data-ttu-id="862ab-113">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="862ab-113">Sorting Data (C#)</span></span>](./sorting-data.md)
