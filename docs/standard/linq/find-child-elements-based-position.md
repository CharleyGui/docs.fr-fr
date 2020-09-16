---
title: Comment rechercher des éléments enfants en fonction de la position-LINQ to XML
description: 'Découvrez comment rechercher des éléments de recherche en fonction de la position de l’élément. Trois méthodes sont affichées : une qui utilise XPathEvaluate, deux qui utilisent LINQ to XML requête.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 889e3dbac3acf229fd49422285d650fc13792521
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557120"
---
# <a name="how-to-find-child-elements-based-on-position-linq-to-xml"></a><span data-ttu-id="17bba-104">Comment rechercher des éléments enfants en fonction de la position (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="17bba-104">How to find child elements based on position (LINQ to XML)</span></span>

<span data-ttu-id="17bba-105">Cet article montre comment utiliser <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour rechercher des éléments en fonction de la position de l’élément, par exemple pour rechercher le deuxième élément, ou le troisième au cinquième.</span><span class="sxs-lookup"><span data-stu-id="17bba-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find elements based on element position – for example, to find the second element, or the third through the fifth.</span></span> <span data-ttu-id="17bba-106">Il montre également deux façons d’utiliser LINQ to XML requête pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="17bba-106">It also shows two ways to use LINQ to XML query to do the same thing.</span></span>

<span data-ttu-id="17bba-107">Il existe deux approches pour l’écriture de cette LINQ to XML requête de manière différée.</span><span class="sxs-lookup"><span data-stu-id="17bba-107">There are two approaches to writing this LINQ to XML query in a lazy way.</span></span> <span data-ttu-id="17bba-108">Vous pouvez utiliser les opérateurs <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Take%2A>, ou vous pouvez utiliser la surcharge <xref:System.Linq.Enumerable.Where%2A> qui prend un index.</span><span class="sxs-lookup"><span data-stu-id="17bba-108">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="17bba-109">Lorsque vous utilisez la surcharge <xref:System.Linq.Enumerable.Where%2A>, vous utilisez une expression lambda qui prend deux arguments.</span><span class="sxs-lookup"><span data-stu-id="17bba-109">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="17bba-110">L'exemple suivant illustre les deux méthodes de sélection basée sur la position.</span><span class="sxs-lookup"><span data-stu-id="17bba-110">The following example shows both methods of selecting based on position.</span></span>

## <a name="example-find-the-second-through-the-fourth-test-elements"></a><span data-ttu-id="17bba-111">Exemple : Rechercher les deuxième et quatrième `Test` éléments</span><span class="sxs-lookup"><span data-stu-id="17bba-111">Example: Find the second through the fourth `Test` elements</span></span>

<span data-ttu-id="17bba-112">Cet exemple recherche le deuxième jusqu’au quatrième `Test` élément de l' [exemple de fichier XML : configuration de test](sample-xml-file-test-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="17bba-112">This example finds the second through the fourth `Test` element in the [Sample XML file: Test configuration](sample-xml-file-test-configuration.md).</span></span> <span data-ttu-id="17bba-113">Le résultat est une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="17bba-113">The result is a collection of elements.</span></span>

<span data-ttu-id="17bba-114">L'expression XPath est `Test[position() >= 2 and position() <= 4]`.</span><span class="sxs-lookup"><span data-stu-id="17bba-114">The XPath expression is `Test[position() >= 2 and position() <= 4]`.</span></span>

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

```vb
Dim testCfg As XElement = XElement.Load("TestConfig.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test").Skip(1).Take(3)

'LINQ to XML query
Dim list2 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test"). _
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)

' XPath expression
Dim list3 As IEnumerable(Of XElement) = _
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")

If list1.Count() = list2.Count() And _
       list1.Count() = list3.Count() And _
       list1.Intersect(list2).Count() = list1.Count() And _
       list1.Intersect(list3).Count() = list1.Count() Then

    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="17bba-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="17bba-115">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="17bba-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17bba-116">See also</span></span>

- [<span data-ttu-id="17bba-117">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17bba-117">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
