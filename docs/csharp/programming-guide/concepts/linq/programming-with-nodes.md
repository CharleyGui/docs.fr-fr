---
title: Programmation avec des nœuds (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 05c2e95fe97effda7b537a7ac2d8f5780f4e212b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168312"
---
# <a name="programming-with-nodes-c"></a>Programmation avec des nœuds (C#)
Les développeurs [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] qui doivent écrire des programmes tels qu'un éditeur XML, un système de transformation ou un générateur de rapports doivent souvent écrire des programmes qui fonctionnent à un niveau de granularité plus élevé que les éléments et attributs. Ils doivent souvent travailler au niveau des nœuds, manipuler des nœuds de texte et traiter des instructions et des commentaires. Cette rubrique fournit quelques détails sur la programmation au niveau nœud.  
  
## <a name="node-details"></a>Détails concernant les nœuds  
 Un programmeur travaillant au niveau nœud doit connaître certains détails de programmation.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>La propriété parente des nœuds enfants de XDocument a la valeur Null  
 La propriété <xref:System.Xml.Linq.XObject.Parent%2A> contient le <xref:System.Xml.Linq.XElement> parent, et non le nœud parent. Les nœuds enfants de <xref:System.Xml.Linq.XDocument> n'ont aucun <xref:System.Xml.Linq.XElement> parent. Leur parent étant le document, la propriété <xref:System.Xml.Linq.XObject.Parent%2A> de ces nœuds a la valeur Null.  
  
 Cela est illustré par l'exemple suivant :  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Des nœuds de texte adjacents sont possibles  
 Dans un certain nombre de modèles de programmation XML, les nœuds de texte adjacents sont toujours fusionnés. On appelle parfois cela la normalisation des nœuds de texte. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ne normalise pas les nœuds de texte. L'ajout de deux nœuds de texte au même élément entraîne l'existence de nœuds de texte adjacents. Toutefois, si vous ajoutez du contenu spécifié comme chaîne plutôt que comme nœud <xref:System.Xml.Linq.XText>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] peut fusionner la chaîne avec un nœud de texte adjacent.  
  
 Cela est illustré par l'exemple suivant :  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Des nœuds de texte vides sont possibles  
 Dans certains modèles de programmation XML, les nœuds de texte sont assurés de ne pas contenir la chaîne vide. Le raisonnement est qu'un tel nœud de texte n'a aucun impact sur la sérialisation du code XML. Toutefois, pour la même raison que les nœuds de texte adjacents sont possibles, si vous supprimez le texte d'un nœud de texte en lui affectant comme valeur la chaîne vide, le nœud de texte lui-même ne sera pas supprimé.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Un nœud de texte vide a un impact sur la sérialisation  
 Si un élément contient uniquement un nœud de texte enfant vide, il est sérialisé avec la syntaxe de balise longue : `<Child></Child>`. Si un élément ne contient aucun nœud enfant, il est sérialisé avec la syntaxe de balise abrégée : `<Child />`.  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Les espaces de noms sont des attributs dans l'arborescence LINQ to XML  
 Bien que les déclarations d'espaces de noms aient une syntaxe identique aux attributs, dans certaines interfaces de programmation (telles que XSLT et XPath) les déclarations d'espaces de noms ne sont pas considérées comme des attributs. Toutefois, dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], les espaces de noms sont stockés en tant qu'objets <xref:System.Xml.Linq.XAttribute> dans l'arborescence XML. Si vous itérez au sein des attributs à la recherche d'un élément qui contient une déclaration d'espace de noms, vous verrez la déclaration d'espace de noms comme l'un des éléments dans la collection retournée.  
  
 La propriété <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> indique si un attribut est une déclaration d'espace de noms.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Les méthodes d'axe XPath ne retournent pas les espaces blancs enfants de XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] autorise l'existence des nœuds de texte enfants d'un objet <xref:System.Xml.Linq.XDocument>, à condition que les nœuds de texte contiennent uniquement des espaces blancs. Toutefois, le modèle objet XPath n’inclut pas d’espaces blancs comme nœuds enfants d’un document. Par conséquent, quand vous itérez des enfants d’un objet <xref:System.Xml.Linq.XDocument> à l’aide de l’axe <xref:System.Xml.Linq.XContainer.Nodes%2A>, des nœuds de texte avec des espaces blancs sont retournés. Toutefois, si vous itérez les enfants d’un objet <xref:System.Xml.Linq.XDocument> à l’aide des méthodes d’axe XPath, les nœuds de texte avec espaces blancs ne sont pas retournés.  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Les objets XDeclaration ne sont pas des nœuds  
 Lorsque vous itérez au sein des enfants nœuds d'un objet <xref:System.Xml.Linq.XDocument>, vous ne voyez pas l'objet de déclaration XML. Il s'agit d'une propriété du document, et non d'un de ses nœuds enfants.  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  