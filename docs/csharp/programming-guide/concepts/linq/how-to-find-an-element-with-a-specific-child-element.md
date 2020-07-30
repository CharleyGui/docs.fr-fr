---
title: Comment rechercher un élément avec un élément enfant spécifique (C#)
description: Découvrez comment rechercher un élément qui a un élément enfant spécifique. Consultez des exemples de code et des ressources supplémentaires.
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301708"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="dd0bd-104">Comment rechercher un élément avec un élément enfant spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="dd0bd-104">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="dd0bd-105">Cette rubrique montre comment rechercher un élément particulier qui a un élément enfant avec une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-105">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd0bd-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd0bd-106">Example</span></span>  
 <span data-ttu-id="dd0bd-107">L'exemple recherche l'élément `Test` qui a un élément enfant `CommandLine` avec la valeur « Examp2.EXE ».</span><span class="sxs-lookup"><span data-stu-id="dd0bd-107">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="dd0bd-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration test (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd0bd-108">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="dd0bd-109">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="dd0bd-109">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="dd0bd-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd0bd-110">Example</span></span>  
 <span data-ttu-id="dd0bd-111">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="dd0bd-112">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd0bd-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="dd0bd-113">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration test dans un espace de noms](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="dd0bd-113">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="dd0bd-114">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="dd0bd-114">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd0bd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd0bd-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="dd0bd-116">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="dd0bd-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="dd0bd-117">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="dd0bd-117">Projection Operations (C#)</span></span>](./projection-operations.md)
