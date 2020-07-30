---
title: Comment trier des éléments (C#)
description: Découvrez comment trier les éléments. Consultez des exemples d’écriture d’une requête qui trie ses résultats dans un document XML.
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 669d9cf583e6ab70c93be39ad271eaf104f88718
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301435"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="1bd21-104">Comment trier des éléments (C#)</span><span class="sxs-lookup"><span data-stu-id="1bd21-104">How to sort elements (C#)</span></span>
<span data-ttu-id="1bd21-105">Cet exemple montre comment écrire une requête qui trie ses résultats.</span><span class="sxs-lookup"><span data-stu-id="1bd21-105">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bd21-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="1bd21-106">Example</span></span>  
 <span data-ttu-id="1bd21-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1bd21-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="1bd21-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1bd21-108">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="1bd21-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="1bd21-109">Example</span></span>  
 <span data-ttu-id="1bd21-110">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1bd21-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1bd21-111">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1bd21-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1bd21-112">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1bd21-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="1bd21-113">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1bd21-113">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bd21-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bd21-114">See also</span></span>

- [<span data-ttu-id="1bd21-115">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="1bd21-115">Sorting Data (C#)</span></span>](./sorting-data.md)
