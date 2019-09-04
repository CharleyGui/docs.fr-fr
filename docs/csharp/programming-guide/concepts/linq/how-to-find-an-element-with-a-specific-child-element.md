---
title: 'Procédure : Rechercher un élément avec un élément enfant spécifique (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: f007bddcbecc1cb938d05c7d444d29b6047749e8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253742"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="2e017-102">Procédure : Rechercher un élément avec un élément enfant spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="2e017-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="2e017-103">Cette rubrique montre comment rechercher un élément particulier qui a un élément enfant avec une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="2e017-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e017-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="2e017-104">Example</span></span>  
 <span data-ttu-id="2e017-105">L'exemple recherche l'élément `Test` qui a un élément enfant `CommandLine` avec la valeur « Examp2.EXE ».</span><span class="sxs-lookup"><span data-stu-id="2e017-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="2e017-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration de test (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e017-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="2e017-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2e017-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="2e017-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e017-108">Example</span></span>  
 <span data-ttu-id="2e017-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2e017-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="2e017-110">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e017-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2e017-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration de test dans un espace de noms](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="2e017-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="2e017-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2e017-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e017-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e017-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="2e017-114">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="2e017-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="2e017-115">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="2e017-115">Projection Operations (C#)</span></span>](./projection-operations.md)
