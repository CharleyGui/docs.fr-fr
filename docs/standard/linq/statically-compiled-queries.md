---
title: Requêtes compilées statiquement-LINQ to XML
description: Découvrez comment les requêtes LINQ to XML tirent un avantage en termes de performances par rapport à XMLDocument en étant compilées statiquement.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553415"
---
# <a name="statically-compiled-queries-linq-to-xml"></a><span data-ttu-id="0c6e3-103">Requêtes compilées statiquement (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0c6e3-103">Statically compiled queries (LINQ to XML)</span></span>

<span data-ttu-id="0c6e3-104">L’un des avantages les plus importants en matière de performances de LINQ to XML, par rapport à <xref:System.Xml.XmlDocument> , est que les requêtes dans les LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétées au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-104">One of the most important performance advantages of LINQ to XML, as compared to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="0c6e3-105">Cette fonctionnalité étant intégrée à LINQ to XML, il n’est pas nécessaire d’effectuer des étapes supplémentaires pour en tirer parti, mais il est utile de comprendre la distinction lors du choix entre les deux technologies.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-105">This feature is built into LINQ to XML, so you don't have to perform extra steps to take advantage of it, but it's helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="0c6e3-106">Cet article explique la différence.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-106">This article explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="0c6e3-107">Requêtes compilées statiquement et XPath</span><span class="sxs-lookup"><span data-stu-id="0c6e3-107">Statically compiled queries vs. XPath</span></span>

<span data-ttu-id="0c6e3-108">L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span> <span data-ttu-id="0c6e3-109">L’expression XPath équivalente est `//Address[@Type='Shipping']` .</span><span class="sxs-lookup"><span data-stu-id="0c6e3-109">The equivalent XPath expression is `//Address[@Type='Shipping']`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="0c6e3-110">L’expression de requête dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-110">The query expression in this example is rewritten by the compiler to method-based query syntax.</span></span> <span data-ttu-id="0c6e3-111">L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="0c6e3-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="0c6e3-112">La méthode <xref:System.Linq.Enumerable.Where%2A> est une méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="0c6e3-113">Pour plus d’informations, consultez [méthodes d’extension (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0c6e3-113">For more information, see [Extension Methods (C# Programming Guide)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="0c6e3-114"><xref:System.Linq.Enumerable.Where%2A> étant une méthode d'extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="0c6e3-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="0c6e3-115">Cet exemple produit exactement les mêmes résultats que les deux exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="0c6e3-116">Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="0c6e3-117">Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="0c6e3-118">Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [exécution différée et évaluation](deferred-execution-lazy-evaluation.md)différée.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-118">For more information about the deferred execution semantics of iterators, see [Deferred execution and lazy evaluation](deferred-execution-lazy-evaluation.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0c6e3-119">Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="0c6e3-120">L’implémentation réelle peut différer légèrement de ces exemples, mais les performances sont les mêmes que, ou similaires à, ces exemples.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-120">The actual implementation might differ slightly from these examples, but the performance will be the same as, or similar to, these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="0c6e3-121">Exécution d’expressions XPath avec XmlDocument</span><span class="sxs-lookup"><span data-stu-id="0c6e3-121">Executing XPath expressions with XmlDocument</span></span>

<span data-ttu-id="0c6e3-122">L'exemple suivant utilise <xref:System.Xml.XmlDocument> pour produire les mêmes résultats que les exemples précédents :</span><span class="sxs-lookup"><span data-stu-id="0c6e3-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

<span data-ttu-id="0c6e3-123">Cette requête retourne le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le code XML imprimé, contrairement à <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="0c6e3-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> doesn't.</span></span>

<span data-ttu-id="0c6e3-124">Toutefois, l' <xref:System.Xml.XmlDocument> approche ne fonctionne généralement pas aussi bien que LINQ to XML, car la <xref:System.Xml.XmlNode.SelectNodes%2A> méthode doit effectuer les opérations suivantes chaque fois qu’elle est appelée :</span><span class="sxs-lookup"><span data-stu-id="0c6e3-124">However, the <xref:System.Xml.XmlDocument> approach generally doesn't perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following every time it's called:</span></span>

- <span data-ttu-id="0c6e3-125">Analyser la chaîne qui contient l’expression XPath, en scindant la chaîne en jetons.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-125">Parse the string that contains the XPath expression, breaking the string into tokens.</span></span>
- <span data-ttu-id="0c6e3-126">Validez les jetons pour vous assurer que l’expression XPath est valide.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-126">Validate the tokens to make sure that the XPath expression is valid.</span></span>
- <span data-ttu-id="0c6e3-127">Traduisez l’expression en une arborescence d’expression interne.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-127">Translate the expression into an internal expression tree.</span></span>
- <span data-ttu-id="0c6e3-128">Itérez au sein des nœuds, en sélectionnant de manière appropriée les nœuds du jeu de résultats en fonction de l’évaluation de l’expression.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-128">Iterate through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="0c6e3-129">Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="0c6e3-130">La différence de performance spécifique varie selon les différents types de requête, mais en général les requêtes LINQ to XML effectuent moins de tâches et fournissent donc une meilleure performance que l'évaluation des expressions XPath à l'aide de <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>
