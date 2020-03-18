---
title: Requêtes compilées statiquement (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253030"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="d14e8-102">Requêtes compilées statiquement (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d14e8-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d14e8-103">L'un des principaux avantages de LINQ to XML en terme de performance, par rapport à <xref:System.Xml.XmlDocument>, est que les requêtes dans LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétées lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d14e8-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="d14e8-104">Cette fonctionnalité étant intégrée dans LINQ to XML, vous n'avez pas à effectuer d'étapes supplémentaires pour en bénéficier, mais il est utile de comprendre cette distinction pour pouvoir choisir entre ces deux technologies.</span><span class="sxs-lookup"><span data-stu-id="d14e8-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="d14e8-105">Cette rubrique explique en quoi consiste la différence.</span><span class="sxs-lookup"><span data-stu-id="d14e8-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="d14e8-106">Requêtes compilées statiquement et Xpath</span><span class="sxs-lookup"><span data-stu-id="d14e8-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="d14e8-107">L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d14e8-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="d14e8-108">Ce qui suit est l’expression équivalente XPath:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="d14e8-108">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d14e8-109">L'expression de requête contenue dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="d14e8-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="d14e8-110">L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="d14e8-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d14e8-111">La méthode <xref:System.Linq.Enumerable.Where%2A> est une méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="d14e8-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="d14e8-112">Pour plus d’informations, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d14e8-112">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d14e8-113"><xref:System.Linq.Enumerable.Where%2A> étant une méthode d'extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="d14e8-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d14e8-114">Cet exemple produit exactement les mêmes résultats que les deux exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="d14e8-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="d14e8-115">Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement.</span><span class="sxs-lookup"><span data-stu-id="d14e8-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="d14e8-116">Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance.</span><span class="sxs-lookup"><span data-stu-id="d14e8-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="d14e8-117">Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [Exécution et évaluation différées dans LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d14e8-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d14e8-118">Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="d14e8-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="d14e8-119">L'implémentation réelle peut différer légèrement de ces exemples, mais la performance sera identique ou similaire à celle de ces exemples.</span><span class="sxs-lookup"><span data-stu-id="d14e8-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="d14e8-120">Exécution d’expressions XPath avec XmlDocument</span><span class="sxs-lookup"><span data-stu-id="d14e8-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="d14e8-121">L'exemple suivant utilise <xref:System.Xml.XmlDocument> pour produire les mêmes résultats que les exemples précédents :</span><span class="sxs-lookup"><span data-stu-id="d14e8-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="d14e8-122">Cette requête retourne le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le XML imprimé, tandis que ce n'est pas le cas pour <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="d14e8-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="d14e8-123">Toutefois, l'approche <xref:System.Xml.XmlDocument> fournit généralement une performance inférieure à LINQ to XML, car la méthode <xref:System.Xml.XmlNode.SelectNodes%2A> doit effectuer les opérations suivantes au niveau interne chaque fois qu'elle est appelée :</span><span class="sxs-lookup"><span data-stu-id="d14e8-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="d14e8-124">Elle analyse la chaîne qui contient l'expression XPath, en scindant la chaîne en jetons.</span><span class="sxs-lookup"><span data-stu-id="d14e8-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="d14e8-125">Elle valide les jetons pour s'assurer que l'expression XPath est valide.</span><span class="sxs-lookup"><span data-stu-id="d14e8-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="d14e8-126">Elle traduit l'expression en arborescence d'expression interne.</span><span class="sxs-lookup"><span data-stu-id="d14e8-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="d14e8-127">Elle effectue l'itération sur les nœuds, en sélectionnant de façon appropriée les nœuds pour le jeu de résultats basé sur l'évaluation de l'expression.</span><span class="sxs-lookup"><span data-stu-id="d14e8-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="d14e8-128">Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant.</span><span class="sxs-lookup"><span data-stu-id="d14e8-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="d14e8-129">La différence de performance spécifique varie selon les différents types de requête, mais en général les requêtes LINQ to XML effectuent moins de tâches et fournissent donc une meilleure performance que l'évaluation des expressions XPath à l'aide de <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="d14e8-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
