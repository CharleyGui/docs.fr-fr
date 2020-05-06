---
title: Programmation à l'aide de nœuds
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 9c64c348f5d26172f26593b927e6bc24baf365bf
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794401"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="011db-102">Programmation avec des nœuds (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="011db-102">Programming with Nodes (Visual Basic)</span></span>
<span data-ttu-id="011db-103">Les développeurs [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] qui doivent écrire des programmes tels qu'un éditeur XML, un système de transformation ou un générateur de rapports doivent souvent écrire des programmes qui fonctionnent à un niveau de granularité plus élevé que les éléments et attributs.</span><span class="sxs-lookup"><span data-stu-id="011db-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="011db-104">Ils doivent souvent travailler au niveau des nœuds, manipuler des nœuds de texte et traiter des instructions et des commentaires.</span><span class="sxs-lookup"><span data-stu-id="011db-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="011db-105">Cette rubrique fournit quelques détails sur la programmation au niveau nœud.</span><span class="sxs-lookup"><span data-stu-id="011db-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="011db-106">Détails concernant les nœuds</span><span class="sxs-lookup"><span data-stu-id="011db-106">Node Details</span></span>  
 <span data-ttu-id="011db-107">Un programmeur travaillant au niveau nœud doit connaître certains détails de programmation.</span><span class="sxs-lookup"><span data-stu-id="011db-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="011db-108">La propriété parente des nœuds enfants de XDocument a la valeur Null</span><span class="sxs-lookup"><span data-stu-id="011db-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="011db-109">La propriété <xref:System.Xml.Linq.XObject.Parent%2A> contient le <xref:System.Xml.Linq.XElement> parent, et non le nœud parent.</span><span class="sxs-lookup"><span data-stu-id="011db-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="011db-110">Les nœuds enfants de <xref:System.Xml.Linq.XDocument> n'ont aucun <xref:System.Xml.Linq.XElement> parent.</span><span class="sxs-lookup"><span data-stu-id="011db-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="011db-111">Leur parent étant le document, la propriété <xref:System.Xml.Linq.XObject.Parent%2A> de ces nœuds a la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="011db-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="011db-112">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="011db-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="011db-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-113">This example produces the following output:</span></span>  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="011db-114">Des nœuds de texte adjacents sont possibles</span><span class="sxs-lookup"><span data-stu-id="011db-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="011db-115">Dans un certain nombre de modèles de programmation XML, les nœuds de texte adjacents sont toujours fusionnés.</span><span class="sxs-lookup"><span data-stu-id="011db-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="011db-116">On appelle parfois cela la normalisation des nœuds de texte.</span><span class="sxs-lookup"><span data-stu-id="011db-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="011db-117">ne normalise pas les nœuds de texte.</span><span class="sxs-lookup"><span data-stu-id="011db-117">does not normalize text nodes.</span></span> <span data-ttu-id="011db-118">L'ajout de deux nœuds de texte au même élément entraîne l'existence de nœuds de texte adjacents.</span><span class="sxs-lookup"><span data-stu-id="011db-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="011db-119">Toutefois, si vous ajoutez du contenu spécifié comme chaîne plutôt que comme nœud <xref:System.Xml.Linq.XText>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] peut fusionner la chaîne avec un nœud de texte adjacent.</span><span class="sxs-lookup"><span data-stu-id="011db-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="011db-120">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="011db-120">The following example demonstrates this:</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="011db-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-121">This example produces the following output:</span></span>  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="011db-122">Des nœuds de texte vides sont possibles</span><span class="sxs-lookup"><span data-stu-id="011db-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="011db-123">Dans certains modèles de programmation XML, les nœuds de texte sont assurés de ne pas contenir la chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="011db-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="011db-124">Le raisonnement est qu'un tel nœud de texte n'a aucun impact sur la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="011db-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="011db-125">Toutefois, pour la même raison que les nœuds de texte adjacents sont possibles, si vous supprimez le texte d'un nœud de texte en lui affectant comme valeur la chaîne vide, le nœud de texte lui-même ne sera pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="011db-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="011db-126">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-126">This example produces the following output:</span></span>  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="011db-127">Un nœud de texte vide a un impact sur la sérialisation</span><span class="sxs-lookup"><span data-stu-id="011db-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="011db-128">Si un élément contient uniquement un nœud de texte enfant vide, il est sérialisé avec la syntaxe de balise longue : `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="011db-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="011db-129">Si un élément ne contient aucun nœud enfant, il est sérialisé avec la syntaxe de balise abrégée : `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="011db-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="011db-130">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="011db-131">Les espaces de noms sont des attributs dans l'arborescence LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="011db-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="011db-132">Bien que les déclarations d'espaces de noms aient une syntaxe identique aux attributs, dans certaines interfaces de programmation (telles que XSLT et XPath) les déclarations d'espaces de noms ne sont pas considérées comme des attributs.</span><span class="sxs-lookup"><span data-stu-id="011db-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="011db-133">Toutefois, dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], les espaces de noms sont stockés en tant qu'objets <xref:System.Xml.Linq.XAttribute> dans l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="011db-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="011db-134">Si vous itérez au sein des attributs à la recherche d'un élément qui contient une déclaration d'espace de noms, vous verrez la déclaration d'espace de noms comme l'un des éléments dans la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="011db-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="011db-135">La propriété <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indique si un attribut est une déclaration d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="011db-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```vb  
Dim root As XElement = _
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 <span data-ttu-id="011db-136">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-136">This example produces the following output:</span></span>  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="011db-137">Les méthodes d'axe XPath ne retournent pas les espaces blancs enfants de XDocument</span><span class="sxs-lookup"><span data-stu-id="011db-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="011db-138">autorise l'existence des nœuds de texte enfants d'un objet <xref:System.Xml.Linq.XDocument>, à condition que les nœuds de texte contiennent uniquement des espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="011db-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="011db-139">Toutefois, le modèle objet XPath n’inclut pas d’espace blanc comme nœuds enfants d’un document ; par conséquent, lorsque vous itérez au sein des enfants d’un objet <xref:System.Xml.Linq.XDocument> à l’aide de l’axe <xref:System.Xml.Linq.XContainer.Nodes%2A>, des nœuds de texte avec espaces blancs sont retournés.</span><span class="sxs-lookup"><span data-stu-id="011db-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="011db-140">Toutefois, lorsque vous itérez au sein des enfants d'un objet <xref:System.Xml.Linq.XDocument> à l'aide des méthodes d'axe XPath, aucun nœud de texte avec espaces blancs n'est retourné.</span><span class="sxs-lookup"><span data-stu-id="011db-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="011db-141">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-141">This example produces the following output:</span></span>  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="011db-142">Les objets XDeclaration ne sont pas des nœuds</span><span class="sxs-lookup"><span data-stu-id="011db-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="011db-143">Lorsque vous itérez au sein des enfants nœuds d'un objet <xref:System.Xml.Linq.XDocument>, vous ne voyez pas l'objet de déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="011db-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="011db-144">Il s'agit d'une propriété du document, et non d'un de ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="011db-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="011db-145">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="011db-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />
1
```  
  
## <a name="see-also"></a><span data-ttu-id="011db-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="011db-146">See also</span></span>

- [<span data-ttu-id="011db-147">Visual Basic (Advanced LINQ to XML Programming)</span><span class="sxs-lookup"><span data-stu-id="011db-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
