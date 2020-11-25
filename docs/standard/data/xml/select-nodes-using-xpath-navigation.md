---
title: Sélection de nœuds à l'aide de la navigation XPath
description: Apprenez à sélectionner des nœuds XML dans .NET. Utilisez des méthodes Document Object Model (DOM) qui vous permettent d’utiliser la navigation XPath (XML Path Language) pour interroger les informations DOM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: b6b68d9351431acc6d9ef20276f51ac4d667d325
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734684"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="153bf-104">Sélection de nœuds à l'aide de la navigation XPath</span><span class="sxs-lookup"><span data-stu-id="153bf-104">Select Nodes Using XPath Navigation</span></span>

<span data-ttu-id="153bf-105">Le DOM (Document Object Model) XML contient des méthodes permettant d’utiliser la navigation du langage XPath (XML Path) pour demander des informations dans le DOM.</span><span class="sxs-lookup"><span data-stu-id="153bf-105">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="153bf-106">Vous pouvez utiliser XPath pour rechercher un nœud simple spécifique ou tous les nœuds qui correspondent à certains critères.</span><span class="sxs-lookup"><span data-stu-id="153bf-106">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="153bf-107">Méthodes de sélection XPath</span><span class="sxs-lookup"><span data-stu-id="153bf-107">XPath Select Methods</span></span>  

 <span data-ttu-id="153bf-108">Les classes DOM offrent deux méthodes pour la sélection XPath : la méthode <xref:System.Xml.XmlNode.SelectSingleNode%2A> et la méthode <xref:System.Xml.XmlNode.SelectNodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="153bf-108">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="153bf-109">La méthode <xref:System.Xml.XmlNode.SelectSingleNode%2A> retourne le premier nœud qui correspond aux critères de sélection.</span><span class="sxs-lookup"><span data-stu-id="153bf-109">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="153bf-110">La méthode <xref:System.Xml.XmlNode.SelectNodes%2A> retourne un objet <xref:System.Xml.XmlNodeList> qui contient les nœuds correspondants.</span><span class="sxs-lookup"><span data-stu-id="153bf-110">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="153bf-111">L'exemple suivant utilise la méthode <xref:System.Xml.XmlNode.SelectSingleNode%2A> pour sélectionner le premier nœud `book` dans lequel le nom de l'auteur répond aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="153bf-111">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="153bf-112">Le fichier bookstore.xml (qui est fourni à la fin de cette rubrique) est utilisé comme fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="153bf-112">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="153bf-113">L'exemple suivant utilise la méthode <xref:System.Xml.XmlNode.SelectNodes%2A> pour sélectionner tous les nœuds book dont le prix est supérieur à un montant spécifié.</span><span class="sxs-lookup"><span data-stu-id="153bf-113">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="153bf-114">Puis le prix de chaque book dans la liste sélectionnée est réduit à l'aide d'un programme de dix pour cent.</span><span class="sxs-lookup"><span data-stu-id="153bf-114">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="153bf-115">Enfin, le fichier mis à jour est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="153bf-115">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="153bf-116">Le fichier bookstore.xml (qui est fourni à la fin de cette rubrique) est utilisé comme fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="153bf-116">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="153bf-117">Les exemples ci-dessus commencent la requête XPath à l’élément de document.</span><span class="sxs-lookup"><span data-stu-id="153bf-117">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="153bf-118">La définition du point de départ pour la requête XPath définit le nœud de contexte, qui constitue le point de départ de la requête XPath.</span><span class="sxs-lookup"><span data-stu-id="153bf-118">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="153bf-119">Si vous ne souhaitez pas commencer à l'élément de document, mais au premier enfant de l'élément de document, vous pouvez coder l'instruction de sélection illustrée comme suit :</span><span class="sxs-lookup"><span data-stu-id="153bf-119">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="153bf-120">Tous les objets <xref:System.Xml.XmlNodeList> sont synchronisés avec le document sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="153bf-120">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="153bf-121">Par conséquent, si vous itérez via la liste de nœuds et modifiez la valeur d'un nœud, celui-ci est également mis à jour dans le document dont il provient.</span><span class="sxs-lookup"><span data-stu-id="153bf-121">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="153bf-122">Notez que, dans l'exemple précédent, lorsqu'un nœud est modifié dans la classe <xref:System.Xml.XmlNodeList> sélectionnée, le document sous-jacent est également modifié.</span><span class="sxs-lookup"><span data-stu-id="153bf-122">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="153bf-123">En cas de modification du document sous-jacent, il est recommandé de réexécuter la sélection.</span><span class="sxs-lookup"><span data-stu-id="153bf-123">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="153bf-124">Si le nœud modifié fait partie de ceux qui peuvent entraîner l'ajout du nœud à la liste dans laquelle il ne figure pas encore ou sa suppression de la liste, il n'est pas garanti que la liste de nœuds est à jour.</span><span class="sxs-lookup"><span data-stu-id="153bf-124">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="153bf-125">Espaces de noms dans les expressions XPath</span><span class="sxs-lookup"><span data-stu-id="153bf-125">Namespaces in XPath Expressions</span></span>  

 <span data-ttu-id="153bf-126">Les expressions XPath peuvent inclure des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="153bf-126">XPath expressions can include namespaces.</span></span> <span data-ttu-id="153bf-127">La résolution d'espace de noms n'est pas prise en charge par l'objet <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="153bf-127">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="153bf-128">Si l'expression XPath comprend un préfixe, celui-ci et l'URI d'espace de noms doivent être ajoutés à l'objet <xref:System.Xml.XmlNamespaceManager> et l'objet <xref:System.Xml.XmlNamespaceManager> est transmis à la méthode <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> ou <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29>.</span><span class="sxs-lookup"><span data-stu-id="153bf-128">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="153bf-129">Remarquez que les exemples de code ci-dessus utilisent le <xref:System.Xml.XmlNamespaceManager> pour trouver l'espace de noms du document bookstore.xml.</span><span class="sxs-lookup"><span data-stu-id="153bf-129">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="153bf-130">Si l’expression XPath n’inclut pas de préfixe, l’URI (Uniform Resource Identifier) d’espace de noms est réputé être l’espace de noms vide.</span><span class="sxs-lookup"><span data-stu-id="153bf-130">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="153bf-131">Si votre code XML inclut un espace de noms par défaut, vous devez toujours ajouter un préfixe et un URI d'espace de noms à l'objet <xref:System.Xml.XmlNamespaceManager> ; sinon, aucun nœud n'est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="153bf-131">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="153bf-132">Fichier d'entrée</span><span class="sxs-lookup"><span data-stu-id="153bf-132">Input File</span></span>  

 <span data-ttu-id="153bf-133">Le fichier bookstore.xml suivant est utilisé comme fichier d'entrée dans les exemples de cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="153bf-133">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="153bf-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="153bf-134">See also</span></span>

- [<span data-ttu-id="153bf-135">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="153bf-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
