---
title: Requêtes compilées statiquement (LINQ to XML) (C#)
description: En savoir plus sur les requêtes compilées statiquement dans LINQ to XML en C# et sur leur différence par rapport aux requêtes XPath, qui doivent être interprétées lors de l’exécution.
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: cd2e6a6507311d5fc17215a22c70bd0449292b6f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302306"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="e5bb1-103">Requêtes compilées statiquement (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5bb1-103">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="e5bb1-104">L'un des principaux avantages de LINQ to XML en terme de performance, par rapport à <xref:System.Xml.XmlDocument>, est que les requêtes dans LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétées lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-104">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="e5bb1-105">Cette fonctionnalité étant intégrée dans LINQ to XML, vous n'avez pas à effectuer d'étapes supplémentaires pour en bénéficier, mais il est utile de comprendre cette distinction pour pouvoir choisir entre ces deux technologies.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-105">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="e5bb1-106">Cette rubrique explique en quoi consiste la différence.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-106">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="e5bb1-107">Requêtes compilées statiquement et Xpath</span><span class="sxs-lookup"><span data-stu-id="e5bb1-107">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="e5bb1-108">L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="e5bb1-109">L’expression XPath équivalente est la suivante :`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="e5bb1-109">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5bb1-110">L'expression de requête contenue dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-110">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="e5bb1-111">L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="e5bb1-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5bb1-112">La méthode <xref:System.Linq.Enumerable.Where%2A> est une méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="e5bb1-113">Pour plus d’informations, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e5bb1-113">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="e5bb1-114"><xref:System.Linq.Enumerable.Where%2A> étant une méthode d'extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="e5bb1-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5bb1-115">Cet exemple produit exactement les mêmes résultats que les deux exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="e5bb1-116">Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="e5bb1-117">Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="e5bb1-118">Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [Exécution et évaluation différées dans LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e5bb1-118">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5bb1-119">Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="e5bb1-120">L'implémentation réelle peut différer légèrement de ces exemples, mais la performance sera identique ou similaire à celle de ces exemples.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-120">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="e5bb1-121">Exécution d’expressions XPath avec XmlDocument</span><span class="sxs-lookup"><span data-stu-id="e5bb1-121">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="e5bb1-122">L'exemple suivant utilise <xref:System.Xml.XmlDocument> pour produire les mêmes résultats que les exemples précédents :</span><span class="sxs-lookup"><span data-stu-id="e5bb1-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="e5bb1-123">Cette requête retourne le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le XML imprimé, tandis que ce n'est pas le cas pour <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="e5bb1-124">Toutefois, l'approche <xref:System.Xml.XmlDocument> fournit généralement une performance inférieure à LINQ to XML, car la méthode <xref:System.Xml.XmlNode.SelectNodes%2A> doit effectuer les opérations suivantes au niveau interne chaque fois qu'elle est appelée :</span><span class="sxs-lookup"><span data-stu-id="e5bb1-124">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="e5bb1-125">Elle analyse la chaîne qui contient l'expression XPath, en scindant la chaîne en jetons.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-125">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="e5bb1-126">Elle valide les jetons pour s'assurer que l'expression XPath est valide.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-126">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="e5bb1-127">Elle traduit l'expression en arborescence d'expression interne.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-127">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="e5bb1-128">Elle effectue l'itération sur les nœuds, en sélectionnant de façon appropriée les nœuds pour le jeu de résultats basé sur l'évaluation de l'expression.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-128">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="e5bb1-129">Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="e5bb1-130">La différence de performance spécifique varie selon les différents types de requête, mais en général les requêtes LINQ to XML effectuent moins de tâches et fournissent donc une meilleure performance que l'évaluation des expressions XPath à l'aide de <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
