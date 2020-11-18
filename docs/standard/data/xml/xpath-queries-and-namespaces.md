---
title: Requêtes et espaces de noms XPath
description: En savoir plus sur les requêtes XPath & les espaces de noms. Les requêtes XPath connaissent les espaces de noms dans un document XML & peuvent utiliser des préfixes d’espaces de noms pour qualifier des noms d’attributs d’élément &.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: a97ff5afef23c361b1f675d2f07f43b3bc5df299
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818386"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="10139-104">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="10139-104">XPath Queries and Namespaces</span></span>
<span data-ttu-id="10139-105">Les requêtes XPath reconnaissent les espaces de noms d’un document XML et peuvent utiliser les préfixes d’espace de noms pour qualifier des noms d’éléments et d’attributs.</span><span class="sxs-lookup"><span data-stu-id="10139-105">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="10139-106">Le fait de qualifier des noms d’éléments et d’attributs avec un préfixe d’espace de noms permet de limiter les nœuds retournés par une requête XPath aux nœuds qui appartiennent à un espace de noms spécifique.</span><span class="sxs-lookup"><span data-stu-id="10139-106">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="10139-107">Par exemple, si le préfixe `books` correspond à l’espace de noms `http://www.contoso.com/books`, la requête XPath suivante `/books:books/books:book` sélectionne uniquement les éléments `book` se trouvant dans l’espace de noms `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="10139-107">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="10139-108">La classe XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="10139-108">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="10139-109">Pour qu'il soit possible d'utiliser des espaces de noms dans une requête XPath, un objet dérivé de l'interface <xref:System.Xml.IXmlNamespaceResolver> comme la classe <xref:System.Xml.XmlNamespaceManager> est construit avec l'URI d'espace de noms et le préfixe à utiliser dans la requête XPath.</span><span class="sxs-lookup"><span data-stu-id="10139-109">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="10139-110">L'objet <xref:System.Xml.XmlNamespaceManager> peut être utilisé dans la requête de chacune des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="10139-110">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="10139-111">L'objet <xref:System.Xml.XmlNamespaceManager> est associé à un objet <xref:System.Xml.XPath.XPathExpression> existant en utilisant la méthode <xref:System.Xml.XPath.XPathExpression.SetContext%2A> de l'objet <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="10139-111">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="10139-112">Vous pouvez aussi compiler un nouvel objet <xref:System.Xml.XPath.XPathExpression> à l'aide de la méthode <xref:System.Xml.XPath.XPathExpression.Compile%2A> statique, qui prend comme paramètres une chaîne représentant l'expression XPath ainsi qu'un objet <xref:System.Xml.XmlNamespaceManager> et retourne un nouvel objet <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="10139-112">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="10139-113">L’objet <xref:System.Xml.XmlNamespaceManager> lui-même est passé en paramètre à une méthode réceptrice de la classe <xref:System.Xml.XPath.XPathNavigator> en même temps qu’une chaîne représentant l’expression XPath.</span><span class="sxs-lookup"><span data-stu-id="10139-113">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="10139-114">Voici les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> qui acceptent comme paramètre un objet dérivé de l'interface <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="10139-114">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="10139-115">L'espace de noms par défaut</span><span class="sxs-lookup"><span data-stu-id="10139-115">The Default Namespace</span></span>  
 <span data-ttu-id="10139-116">Dans le document XML suivant, l'espace de noms par défaut, avec un préfixe vide, est utilisé pour déclarer l'espace de noms `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="10139-116">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="10139-117">XPath traite le préfixe vide comme l’espace de noms `null`.</span><span class="sxs-lookup"><span data-stu-id="10139-117">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="10139-118">Autrement dit, seuls les préfixes mappés à des espaces de noms peuvent être utilisés dans des requêtes XPath.</span><span class="sxs-lookup"><span data-stu-id="10139-118">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="10139-119">Cela signifie que si vous voulez appliquer une requête à un espace de noms d'un document XML, vous devez définir un préfixe pour cet espace de noms, même si c'est l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="10139-119">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="10139-120">Par exemple, si aucun préfixe n’est défini pour le document XML ci-dessus, la requête XPath `/books/book` ne retournera aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="10139-120">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="10139-121">Un préfixe doit être lié afin d'éviter toute ambiguïté lors de l'interrogation de documents où certains nœuds ne sont pas dans un espace de noms et certains se trouvent dans un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="10139-121">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="10139-122">Le code suivant définit un préfixe pour l'espace de noms par défaut et sélectionne tous les éléments `book` de l'espace de noms `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="10139-122">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a><span data-ttu-id="10139-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10139-123">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="10139-124">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="10139-124">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="10139-125">Sélection de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="10139-125">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="10139-126">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="10139-126">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="10139-127">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="10139-127">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="10139-128">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="10139-128">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="10139-129">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="10139-129">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
