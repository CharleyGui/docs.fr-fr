---
title: Expressions XPath compilées
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: b4675765849299050eb6cddeaaa497bc6cdc620a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711101"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="f38ed-102">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="f38ed-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="f38ed-103">Un objet <xref:System.Xml.XPath.XPathExpression> représente une requête XPath compilée retournée depuis la méthode statique <xref:System.Xml.XPath.XPathExpression.Compile%2A> de la classe <xref:System.Xml.XPath.XPathExpression> ou depuis la méthode <xref:System.Xml.XPath.XPathNavigator.Compile%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f38ed-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="f38ed-104">La classe XPathExpression</span><span class="sxs-lookup"><span data-stu-id="f38ed-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="f38ed-105">Une requête XPath compilée représentée par un objet <xref:System.Xml.XPath.XPathExpression> est utile si la même requête XPath doit être utilisée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="f38ed-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="f38ed-106">Par exemple, lorsque la méthode <xref:System.Xml.XPath.XPathNavigator.Select%2A> doit être appelée plusieurs fois, au lieu d'utiliser chaque fois une chaîne représentant la requête XPath, utilisez la méthode <xref:System.Xml.XPath.XPathExpression.Compile%2A> de la classe <xref:System.Xml.XPath.XPathExpression> ou la méthode <xref:System.Xml.XPath.XPathNavigator.Compile%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> pour compiler et mettre en cache la requête XPath dans un objet <xref:System.Xml.XPath.XPathExpression> afin de pouvoir la réutiliser et d'améliorer ainsi les performances.</span><span class="sxs-lookup"><span data-stu-id="f38ed-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="f38ed-107">Une fois compilé, l’objet <xref:System.Xml.XPath.XPathExpression> peut être utilisé comme entrée des méthodes suivantes de la classe <xref:System.Xml.XPath.XPathNavigator> selon le type retourné par la requête XPath.</span><span class="sxs-lookup"><span data-stu-id="f38ed-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="f38ed-108">Le tableau suivant décrit chacun des types de retours XPath W3C, leurs équivalents Microsoft .NET Framework et les méthodes avec lesquelles l'objet <xref:System.Xml.XPath.XPathExpression> peut être utilisé selon le type de retour.</span><span class="sxs-lookup"><span data-stu-id="f38ed-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="f38ed-109">Type de retour XPath W3C</span><span class="sxs-lookup"><span data-stu-id="f38ed-109">W3C XPath Return Type</span></span>|<span data-ttu-id="f38ed-110">Type .NET Framework équivalent</span><span class="sxs-lookup"><span data-stu-id="f38ed-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="f38ed-111">Description</span><span class="sxs-lookup"><span data-stu-id="f38ed-111">Description</span></span>|<span data-ttu-id="f38ed-112">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f38ed-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="f38ed-113">Une collection non triée des nœuds sans doublons créés dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="f38ed-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="f38ed-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> ou <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="f38ed-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="f38ed-115">Une valeur `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="f38ed-115">A `true` or `false` value.</span></span>|<span data-ttu-id="f38ed-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ou</span><span class="sxs-lookup"><span data-stu-id="f38ed-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="f38ed-117">Nombre à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="f38ed-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="f38ed-118">Séquence de caractères UCS.</span><span class="sxs-lookup"><span data-stu-id="f38ed-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="f38ed-119">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> accepte une expression XPath comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="f38ed-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="f38ed-120">La méthode <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> retourne un objet <xref:System.Xml.XPath.XPathNavigator>, pas un des types de retours XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="f38ed-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="f38ed-121">La propriété ReturnType</span><span class="sxs-lookup"><span data-stu-id="f38ed-121">The ReturnType Property</span></span>  
 <span data-ttu-id="f38ed-122">Une fois qu'une requête XPath a été compilée dans un objet <xref:System.Xml.XPath.XPathExpression>, vous pouvez utiliser la propriété <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> de l'objet <xref:System.Xml.XPath.XPathExpression> pour déterminer ce que retourne la requête XPath.</span><span class="sxs-lookup"><span data-stu-id="f38ed-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="f38ed-123">La propriété <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> retourne une des valeurs d'énumération <xref:System.Xml.XPath.XPathResultType> suivantes, représentant les types de retours XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="f38ed-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="f38ed-124">L'exemple suivant utilise l'objet <xref:System.Xml.XPath.XPathExpression> pour retourner un nombre et une collection de nœuds à partir du fichier `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="f38ed-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="f38ed-125">La propriété <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> de chaque objet <xref:System.Xml.XPath.XPathExpression> ainsi que les résultats des méthodes <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> et <xref:System.Xml.XPath.XPathNavigator.Select%2A> sont écrits à la console.</span><span class="sxs-lookup"><span data-stu-id="f38ed-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="f38ed-126">L'exemple prend le fichier `books.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="f38ed-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="f38ed-127">Expressions XPath plus performantes</span><span class="sxs-lookup"><span data-stu-id="f38ed-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="f38ed-128">Pour obtenir des performances optimales, utilisez l'expression XPath la plus spécifique possible dans vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="f38ed-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="f38ed-129">Par exemple, si le nœud `book` est un enfant du noeud `bookstore` et si le nœud `bookstore` est l'élément de niveau supérieur dans un document XML, il est plus rapide d'utiliser l'expression XPath `/bookstore/book` que `//book`.</span><span class="sxs-lookup"><span data-stu-id="f38ed-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="f38ed-130">L’expression XPath `//book` analysera en effet chaque nœud de l’arborescence XML en vue d’identifier les nœuds qui correspondent.</span><span class="sxs-lookup"><span data-stu-id="f38ed-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="f38ed-131">De plus, l'utilisation des méthodes de navigation dans les nœuds fournies par la classe <xref:System.Xml.XPath.XPathNavigator> peut améliorer les performances par rapport aux méthodes de sélection fournies par la classe <xref:System.Xml.XPath.XPathNavigator> lorsque les critères de sélection sont simples.</span><span class="sxs-lookup"><span data-stu-id="f38ed-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="f38ed-132">Par exemple, si vous devez sélectionner le premier enfant du nœud actuel, il est plus rapide d’utiliser la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> que d’utiliser l’expression XPath `child::*[1]` et la méthode <xref:System.Xml.XPath.XPathNavigator.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="f38ed-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="f38ed-133">Pour plus d'informations sur les méthodes de navigation dans les nœuds fournies par la classe <xref:System.Xml.XPath.XPathNavigator>, consultez [Navigation dans la collection de nœuds à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="f38ed-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38ed-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f38ed-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f38ed-135">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="f38ed-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f38ed-136">Sélection de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f38ed-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f38ed-137">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f38ed-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="f38ed-138">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f38ed-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="f38ed-139">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="f38ed-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="f38ed-140">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="f38ed-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
