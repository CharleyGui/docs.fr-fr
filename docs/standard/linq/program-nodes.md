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
# <a name="programming-with-nodes-linq-to-xml"></a>Programmation avec des nœuds (LINQ to XML)

LINQ to XML les développeurs qui ont besoin d’écrire des programmes tels qu’un éditeur XML, un système de transformation ou un générateur de rapports ont souvent besoin de code qui fonctionne à un niveau de granularité plus élevé que les éléments et les attributs. Ils doivent souvent travailler au niveau du nœud, manipuler des nœuds de texte, traiter des instructions et traiter des commentaires. Cet article fournit des informations sur la programmation au niveau du nœud.

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a>Exemple : les `Parent` valeurs de propriété des nœuds enfants de XDocument sont définies sur `null`

La propriété <xref:System.Xml.Linq.XObject.Parent%2A> contient le <xref:System.Xml.Linq.XElement> parent, et non le nœud parent. Les nœuds enfants de <xref:System.Xml.Linq.XDocument> n'ont aucun <xref:System.Xml.Linq.XElement> parent. Leur parent étant le document, la <xref:System.Xml.Linq.XObject.Parent%2A> propriété de ces nœuds a la valeur `null` .

Cela est illustré par l'exemple suivant :

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

Cet exemple produit la sortie suivante :

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a>Exemple : l’ajout de texte peut ou ne peut pas créer un nouveau nœud de texte

Dans un certain nombre de modèles de programmation XML, les nœuds de texte adjacents sont toujours fusionnés. On appelle parfois cela la normalisation des nœuds de texte. LINQ to XML ne normalise pas les nœuds de texte. L'ajout de deux nœuds de texte au même élément entraîne l'existence de nœuds de texte adjacents. Toutefois, si vous ajoutez du contenu spécifié en tant que chaîne plutôt qu’en tant que <xref:System.Xml.Linq.XText> nœud, LINQ to XML pouvez fusionner la chaîne avec un nœud de texte adjacent. l’exemple ci-dessous illustre ce cas de figure.

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

 Cet exemple produit la sortie suivante :

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a>Exemple : la définition d’une valeur de nœud de texte sur la chaîne vide ne supprime pas le nœud

Dans certains modèles de programmation XML, les nœuds de texte sont assurés de ne pas contenir la chaîne vide. Le raisonnement est qu'un tel nœud de texte n'a aucun impact sur la sérialisation du code XML. Toutefois, pour la même raison que les nœuds de texte adjacents sont possibles, si vous supprimez le texte d’un nœud de texte en définissant sa valeur sur la chaîne vide, le nœud de texte lui-même ne sera pas supprimé.

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

Cet exemple produit la sortie suivante :

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a>Exemple : un élément avec un nœud de texte vide est sérialisé différemment d’un élément sans nœud de texte

Si un élément contient uniquement un nœud de texte enfant vide, il est sérialisé avec la syntaxe de balise longue : `<Child></Child>` . Si un élément ne contient aucun nœud enfant, il est sérialisé avec la syntaxe de balise abrégée : `<Child />` .

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

Cet exemple produit la sortie suivante :

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Exemple : les espaces de noms sont des attributs dans l’arborescence LINQ to XML

Bien que les déclarations d’espaces de noms aient une syntaxe identique aux attributs, dans certaines interfaces de programmation, telles que XSLT et XPath, les déclarations d’espaces de noms ne sont pas considérées comme des attributs. Toutefois, dans LINQ to XML, les espaces de noms sont stockés en tant qu' <xref:System.Xml.Linq.XAttribute> objets dans l’arborescence XML. Si vous itérez au sein des attributs d’un élément qui contient une déclaration d’espace de noms, la déclaration d’espace de noms est l’un des éléments de la collection retournée. La propriété <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indique si un attribut est une déclaration d'espace de noms.

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

Cet exemple produit la sortie suivante :

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a>Exemple : les méthodes d’axe XPath ne retournent pas les nœuds de texte enfants de XDocument

LINQ to XML autorise les nœuds de texte enfants d’un <xref:System.Xml.Linq.XDocument> , à condition que les nœuds de texte contiennent uniquement des espaces blancs. Toutefois, le modèle objet XPath n’inclut pas d’espace blanc comme nœuds enfants d’un document. par conséquent, lorsque vous itérez au sein des enfants d’un objet <xref:System.Xml.Linq.XDocument> à l’aide de l' <xref:System.Xml.Linq.XContainer.Nodes%2A> axe, des nœuds de texte d’espace blanc sont retournés. Toutefois, lorsque vous itérez au sein des enfants d’un <xref:System.Xml.Linq.XDocument> à l’aide des méthodes d’axe XPath, les nœuds de texte avec espaces blancs ne sont pas retournés.

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

Cet exemple produit la sortie suivante :

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a>Le nœud de déclaration XML d’un XDocument est une propriété, et non un nœud enfant

Lorsque vous itérez au sein des nœuds enfants d’un <xref:System.Xml.Linq.XDocument> , vous ne voyez pas l’objet de déclaration XML. Il s’agit d’une propriété du document, et non d’un nœud enfant de celui-ci.

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

Cet exemple produit la sortie suivante :

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
