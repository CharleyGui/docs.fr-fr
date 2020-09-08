---
title: Programmation à l’aide de nœuds-LINQ to XML
description: Découvrez comment coder au niveau du nœud d’une arborescence XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8f9d5c8656a06a9b40a3833aaf7e190b9ba3f0a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553284"
---
# <a name="programming-with-nodes-linq-to-xml"></a><span data-ttu-id="d9b42-103">Programmation avec des nœuds (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d9b42-103">Programming with nodes (LINQ to XML)</span></span>

<span data-ttu-id="d9b42-104">LINQ to XML les développeurs qui ont besoin d’écrire des programmes tels qu’un éditeur XML, un système de transformation ou un générateur de rapports ont souvent besoin de code qui fonctionne à un niveau de granularité plus élevé que les éléments et les attributs.</span><span class="sxs-lookup"><span data-stu-id="d9b42-104">LINQ to XML developers who need to write programs such as an XML editor, a transform system, or a report writer often need code that works at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="d9b42-105">Ils doivent souvent travailler au niveau du nœud, manipuler des nœuds de texte, traiter des instructions et traiter des commentaires.</span><span class="sxs-lookup"><span data-stu-id="d9b42-105">They often need to work at the node level, manipulating text nodes, processing instructions, and processing comments.</span></span> <span data-ttu-id="d9b42-106">Cet article fournit des informations sur la programmation au niveau du nœud.</span><span class="sxs-lookup"><span data-stu-id="d9b42-106">This article provides information about programming at the node level.</span></span>

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a><span data-ttu-id="d9b42-107">Exemple : les `Parent` valeurs de propriété des nœuds enfants de XDocument sont définies sur `null`</span><span class="sxs-lookup"><span data-stu-id="d9b42-107">Example: The `Parent` property values of the child nodes of XDocument are set to `null`</span></span>

<span data-ttu-id="d9b42-108">La propriété <xref:System.Xml.Linq.XObject.Parent%2A> contient le <xref:System.Xml.Linq.XElement> parent, et non le nœud parent.</span><span class="sxs-lookup"><span data-stu-id="d9b42-108">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="d9b42-109">Les nœuds enfants de <xref:System.Xml.Linq.XDocument> n'ont aucun <xref:System.Xml.Linq.XElement> parent.</span><span class="sxs-lookup"><span data-stu-id="d9b42-109">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="d9b42-110">Leur parent étant le document, la <xref:System.Xml.Linq.XObject.Parent%2A> propriété de ces nœuds a la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="d9b42-110">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to `null`.</span></span>

<span data-ttu-id="d9b42-111">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d9b42-111">The following example demonstrates this:</span></span>

```csharp
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);
Console.WriteLine(doc.Root.Parent == null);
```

```vb
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)
Console.WriteLine(doc.Root.Parent Is Nothing)
```

<span data-ttu-id="d9b42-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-112">This example produces the following output:</span></span>

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a><span data-ttu-id="d9b42-113">Exemple : l’ajout de texte peut ou ne peut pas créer un nouveau nœud de texte</span><span class="sxs-lookup"><span data-stu-id="d9b42-113">Example: Adding text may or may not create a new text node</span></span>

<span data-ttu-id="d9b42-114">Dans un certain nombre de modèles de programmation XML, les nœuds de texte adjacents sont toujours fusionnés.</span><span class="sxs-lookup"><span data-stu-id="d9b42-114">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="d9b42-115">On appelle parfois cela la normalisation des nœuds de texte.</span><span class="sxs-lookup"><span data-stu-id="d9b42-115">This is sometimes called normalization of text nodes.</span></span> <span data-ttu-id="d9b42-116">LINQ to XML ne normalise pas les nœuds de texte.</span><span class="sxs-lookup"><span data-stu-id="d9b42-116">LINQ to XML doesn't normalize text nodes.</span></span> <span data-ttu-id="d9b42-117">L'ajout de deux nœuds de texte au même élément entraîne l'existence de nœuds de texte adjacents.</span><span class="sxs-lookup"><span data-stu-id="d9b42-117">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="d9b42-118">Toutefois, si vous ajoutez du contenu spécifié en tant que chaîne plutôt qu’en tant que <xref:System.Xml.Linq.XText> nœud, LINQ to XML pouvez fusionner la chaîne avec un nœud de texte adjacent.</span><span class="sxs-lookup"><span data-stu-id="d9b42-118">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, LINQ to XML might merge the string with an adjacent text node.</span></span> <span data-ttu-id="d9b42-119">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="d9b42-119">The following example demonstrates this.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");

Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this doesn't add a new text node
xmlTree.Add("new content");
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this does add a new, adjacent text node
xmlTree.Add(new XText("more text"));
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

' This doesn't add a new text node.
xmlTree.Add("new content")
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

'// This does add a new, adjacent text node.
xmlTree.Add(New XText("more text"))
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())
```

 <span data-ttu-id="d9b42-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-120">This example produces the following output:</span></span>

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a><span data-ttu-id="d9b42-121">Exemple : la définition d’une valeur de nœud de texte sur la chaîne vide ne supprime pas le nœud</span><span class="sxs-lookup"><span data-stu-id="d9b42-121">Example: Setting a text node value to the empty string doesn't delete the node</span></span>

<span data-ttu-id="d9b42-122">Dans certains modèles de programmation XML, les nœuds de texte sont assurés de ne pas contenir la chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="d9b42-122">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="d9b42-123">Le raisonnement est qu'un tel nœud de texte n'a aucun impact sur la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="d9b42-123">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="d9b42-124">Toutefois, pour la même raison que les nœuds de texte adjacents sont possibles, si vous supprimez le texte d’un nœud de texte en définissant sa valeur sur la chaîne vide, le nœud de texte lui-même ne sera pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="d9b42-124">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself won't be deleted.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");
XText textNode = xmlTree.Nodes().OfType<XText>().First();

// the following line doesn't cause the removal of the text node.
textNode.Value = "";

XText textNode2 = xmlTree.Nodes().OfType<XText>().First();
Console.WriteLine(">>{0}<<", textNode2);
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()

' The following line doesn't cause the removal of the text node.
textNode.Value = ""

Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()
Console.WriteLine(">>{0}<<", textNode2)
```

<span data-ttu-id="d9b42-125">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-125">This example produces the following output:</span></span>

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a><span data-ttu-id="d9b42-126">Exemple : un élément avec un nœud de texte vide est sérialisé différemment d’un élément sans nœud de texte</span><span class="sxs-lookup"><span data-stu-id="d9b42-126">Example: An element with one empty text node is serialized differently from one with no text node</span></span>

<span data-ttu-id="d9b42-127">Si un élément contient uniquement un nœud de texte enfant vide, il est sérialisé avec la syntaxe de balise longue : `<Child></Child>` .</span><span class="sxs-lookup"><span data-stu-id="d9b42-127">If an element contains only a child text node that's empty, it's serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="d9b42-128">Si un élément ne contient aucun nœud enfant, il est sérialisé avec la syntaxe de balise abrégée : `<Child />` .</span><span class="sxs-lookup"><span data-stu-id="d9b42-128">If an element contains no child nodes whatsoever, it's serialized with the short tag syntax: `<Child />`.</span></span>

```csharp
XElement child1 = new XElement("Child1",
    new XText("")
);
XElement child2 = new XElement("Child2");
Console.WriteLine(child1);
Console.WriteLine(child2);
```

```vb
Dim child1 As XElement = New XElement("Child1", _
    New XText("") _
)
Dim child2 As XElement = New XElement("Child2")
Console.WriteLine(child1)
Console.WriteLine(child2)
```

<span data-ttu-id="d9b42-129">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-129">This example produces the following output:</span></span>

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="d9b42-130">Exemple : les espaces de noms sont des attributs dans l’arborescence LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="d9b42-130">Example: Namespaces are attributes in the LINQ to XML tree</span></span>

<span data-ttu-id="d9b42-131">Bien que les déclarations d’espaces de noms aient une syntaxe identique aux attributs, dans certaines interfaces de programmation, telles que XSLT et XPath, les déclarations d’espaces de noms ne sont pas considérées comme des attributs.</span><span class="sxs-lookup"><span data-stu-id="d9b42-131">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations aren't considered to be attributes.</span></span> <span data-ttu-id="d9b42-132">Toutefois, dans LINQ to XML, les espaces de noms sont stockés en tant qu' <xref:System.Xml.Linq.XAttribute> objets dans l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="d9b42-132">However, in LINQ to XML, namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="d9b42-133">Si vous itérez au sein des attributs d’un élément qui contient une déclaration d’espace de noms, la déclaration d’espace de noms est l’un des éléments de la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="d9b42-133">If you iterate through the attributes of an element that contains a namespace declaration, the namespace declaration is one of the items in the returned collection.</span></span> <span data-ttu-id="d9b42-134">La propriété <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indique si un attribut est une déclaration d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d9b42-134">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>");
foreach (XAttribute att in root.Attributes())
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);
```

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

<span data-ttu-id="d9b42-135">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-135">This example produces the following output:</span></span>

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a><span data-ttu-id="d9b42-136">Exemple : les méthodes d’axe XPath ne retournent pas les nœuds de texte enfants de XDocument</span><span class="sxs-lookup"><span data-stu-id="d9b42-136">Example: XPath axis methods don't return the child text nodes of XDocument</span></span>

<span data-ttu-id="d9b42-137">LINQ to XML autorise les nœuds de texte enfants d’un <xref:System.Xml.Linq.XDocument> , à condition que les nœuds de texte contiennent uniquement des espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="d9b42-137">LINQ to XML allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="d9b42-138">Toutefois, le modèle objet XPath n’inclut pas d’espace blanc comme nœuds enfants d’un document. par conséquent, lorsque vous itérez au sein des enfants d’un objet <xref:System.Xml.Linq.XDocument> à l’aide de l' <xref:System.Xml.Linq.XContainer.Nodes%2A> axe, des nœuds de texte d’espace blanc sont retournés.</span><span class="sxs-lookup"><span data-stu-id="d9b42-138">However, the XPath object model doesn't include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="d9b42-139">Toutefois, lorsque vous itérez au sein des enfants d’un <xref:System.Xml.Linq.XDocument> à l’aide des méthodes d’axe XPath, les nœuds de texte avec espaces blancs ne sont pas retournés.</span><span class="sxs-lookup"><span data-stu-id="d9b42-139">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes won't be returned.</span></span>

```csharp
// Create a document with some white space child nodes of the document.
XDocument root = XDocument.Parse(
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<Root/>

<!--a comment-->
", LoadOptions.PreserveWhitespace);

// count the white space child nodes using LINQ to XML
Console.WriteLine(root.Nodes().OfType<XText>().Count());

// count the white space child nodes using XPathEvaluate
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```

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

<span data-ttu-id="d9b42-140">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-140">This example produces the following output:</span></span>

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a><span data-ttu-id="d9b42-141">Le nœud de déclaration XML d’un XDocument est une propriété, et non un nœud enfant</span><span class="sxs-lookup"><span data-stu-id="d9b42-141">The XML declaration node of an XDocument is a property, not a child node</span></span>

<span data-ttu-id="d9b42-142">Lorsque vous itérez au sein des nœuds enfants d’un <xref:System.Xml.Linq.XDocument> , vous ne voyez pas l’objet de déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="d9b42-142">When you iterate through the child nodes of an <xref:System.Xml.Linq.XDocument>, you won't see the XML declaration object.</span></span> <span data-ttu-id="d9b42-143">Il s’agit d’une propriété du document, et non d’un nœud enfant de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d9b42-143">It's a property of the document, not a child node of it.</span></span>

```csharp
XDocument doc = new XDocument(
    new XDeclaration("1.0", "utf-8", "yes"),
    new XElement("Root")
);
doc.Save("Temp.xml");
Console.WriteLine(File.ReadAllText("Temp.xml"));

// this shows that there is only one child node of the document
Console.WriteLine(doc.Nodes().Count());
```

```vb
Dim doc As XDocument = _
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<Root/>

doc.Save("Temp.xml")
Console.WriteLine(File.ReadAllText("Temp.xml"))

' This shows that there is only one child node of the document.
Console.WriteLine(doc.Nodes().Count())
```

<span data-ttu-id="d9b42-144">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d9b42-144">This example produces the following output:</span></span>

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
