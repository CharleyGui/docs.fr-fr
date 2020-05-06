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
# <a name="programming-with-nodes-visual-basic"></a>Programmation avec des nœuds (Visual Basic)
Les développeurs [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] qui doivent écrire des programmes tels qu'un éditeur XML, un système de transformation ou un générateur de rapports doivent souvent écrire des programmes qui fonctionnent à un niveau de granularité plus élevé que les éléments et attributs. Ils doivent souvent travailler au niveau des nœuds, manipuler des nœuds de texte et traiter des instructions et des commentaires. Cette rubrique fournit quelques détails sur la programmation au niveau nœud.  
  
## <a name="node-details"></a>Détails concernant les nœuds  
 Un programmeur travaillant au niveau nœud doit connaître certains détails de programmation.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>La propriété parente des nœuds enfants de XDocument a la valeur Null  
 La propriété <xref:System.Xml.Linq.XObject.Parent%2A> contient le <xref:System.Xml.Linq.XElement> parent, et non le nœud parent. Les nœuds enfants de <xref:System.Xml.Linq.XDocument> n'ont aucun <xref:System.Xml.Linq.XElement> parent. Leur parent étant le document, la propriété <xref:System.Xml.Linq.XObject.Parent%2A> de ces nœuds a la valeur Null.  
  
 Cela est illustré par l'exemple suivant :  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Des nœuds de texte adjacents sont possibles  
 Dans un certain nombre de modèles de programmation XML, les nœuds de texte adjacents sont toujours fusionnés. On appelle parfois cela la normalisation des nœuds de texte. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ne normalise pas les nœuds de texte. L'ajout de deux nœuds de texte au même élément entraîne l'existence de nœuds de texte adjacents. Toutefois, si vous ajoutez du contenu spécifié comme chaîne plutôt que comme nœud <xref:System.Xml.Linq.XText>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] peut fusionner la chaîne avec un nœud de texte adjacent.  
  
 Cela est illustré par l'exemple suivant :  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Des nœuds de texte vides sont possibles  
 Dans certains modèles de programmation XML, les nœuds de texte sont assurés de ne pas contenir la chaîne vide. Le raisonnement est qu'un tel nœud de texte n'a aucun impact sur la sérialisation du code XML. Toutefois, pour la même raison que les nœuds de texte adjacents sont possibles, si vous supprimez le texte d'un nœud de texte en lui affectant comme valeur la chaîne vide, le nœud de texte lui-même ne sera pas supprimé.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Un nœud de texte vide a un impact sur la sérialisation  
 Si un élément contient uniquement un nœud de texte enfant vide, il est sérialisé avec la syntaxe de balise longue : `<Child></Child>`. Si un élément ne contient aucun nœud enfant, il est sérialisé avec la syntaxe de balise abrégée : `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Les espaces de noms sont des attributs dans l'arborescence LINQ to XML  
 Bien que les déclarations d'espaces de noms aient une syntaxe identique aux attributs, dans certaines interfaces de programmation (telles que XSLT et XPath) les déclarations d'espaces de noms ne sont pas considérées comme des attributs. Toutefois, dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], les espaces de noms sont stockés en tant qu'objets <xref:System.Xml.Linq.XAttribute> dans l'arborescence XML. Si vous itérez au sein des attributs à la recherche d'un élément qui contient une déclaration d'espace de noms, vous verrez la déclaration d'espace de noms comme l'un des éléments dans la collection retournée.  
  
 La propriété <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indique si un attribut est une déclaration d'espace de noms.  
  
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
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Les méthodes d'axe XPath ne retournent pas les espaces blancs enfants de XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] autorise l'existence des nœuds de texte enfants d'un objet <xref:System.Xml.Linq.XDocument>, à condition que les nœuds de texte contiennent uniquement des espaces blancs. Toutefois, le modèle objet XPath n’inclut pas d’espace blanc comme nœuds enfants d’un document ; par conséquent, lorsque vous itérez au sein des enfants d’un objet <xref:System.Xml.Linq.XDocument> à l’aide de l’axe <xref:System.Xml.Linq.XContainer.Nodes%2A>, des nœuds de texte avec espaces blancs sont retournés. Toutefois, lorsque vous itérez au sein des enfants d'un objet <xref:System.Xml.Linq.XDocument> à l'aide des méthodes d'axe XPath, aucun nœud de texte avec espaces blancs n'est retourné.  
  
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
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Les objets XDeclaration ne sont pas des nœuds  
 Lorsque vous itérez au sein des enfants nœuds d'un objet <xref:System.Xml.Linq.XDocument>, vous ne voyez pas l'objet de déclaration XML. Il s'agit d'une propriété du document, et non d'un de ses nœuds enfants.  
  
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
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />
1
```  
  
## <a name="see-also"></a>Voir aussi

- [Visual Basic (Advanced LINQ to XML Programming)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
