---
title: Guide pratique pour rechercher des éléments enfants en fonction de leur position (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher des éléments enfants en fonction de leur position à l’aide d’une expression XPath. Passez en revue un exemple de code qui utilise un exemple de fichier XML.
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 2603d3ac94ace645bde1ce85a43a43af7321014e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301669"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="22813-104">Guide pratique pour rechercher des éléments enfants en fonction de leur position (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="22813-104">How to find child elements based on position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="22813-105">Parfois, vous souhaitez rechercher des éléments en fonction de leur position.</span><span class="sxs-lookup"><span data-stu-id="22813-105">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="22813-106">Vous pourriez souhaiter rechercher le deuxième élément, ou les troisième, quatrième et cinquième éléments.</span><span class="sxs-lookup"><span data-stu-id="22813-106">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="22813-107">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="22813-107">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="22813-108">Il existe deux approches pour l'écriture de cette requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] d'une manière différée.</span><span class="sxs-lookup"><span data-stu-id="22813-108">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="22813-109">Vous pouvez utiliser les opérateurs <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Take%2A>, ou vous pouvez utiliser la surcharge <xref:System.Linq.Enumerable.Where%2A> qui prend un index.</span><span class="sxs-lookup"><span data-stu-id="22813-109">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="22813-110">Lorsque vous utilisez la surcharge <xref:System.Linq.Enumerable.Where%2A>, vous utilisez une expression lambda qui prend deux arguments.</span><span class="sxs-lookup"><span data-stu-id="22813-110">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="22813-111">L'exemple suivant illustre les deux méthodes de sélection basée sur la position.</span><span class="sxs-lookup"><span data-stu-id="22813-111">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22813-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="22813-112">Example</span></span>  
 <span data-ttu-id="22813-113">Cet exemple recherche les deuxième, troisième et quatrième éléments `Test`.</span><span class="sxs-lookup"><span data-stu-id="22813-113">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="22813-114">Le résultat est une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="22813-114">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="22813-115">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration test (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22813-115">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="22813-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="22813-116">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
