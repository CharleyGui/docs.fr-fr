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
# <a name="select-nodes-using-xpath-navigation"></a>Sélection de nœuds à l'aide de la navigation XPath

Le DOM (Document Object Model) XML contient des méthodes permettant d’utiliser la navigation du langage XPath (XML Path) pour demander des informations dans le DOM. Vous pouvez utiliser XPath pour rechercher un nœud simple spécifique ou tous les nœuds qui correspondent à certains critères.  
  
## <a name="xpath-select-methods"></a>Méthodes de sélection XPath  

 Les classes DOM offrent deux méthodes pour la sélection XPath : la méthode <xref:System.Xml.XmlNode.SelectSingleNode%2A> et la méthode <xref:System.Xml.XmlNode.SelectNodes%2A>. La méthode <xref:System.Xml.XmlNode.SelectSingleNode%2A> retourne le premier nœud qui correspond aux critères de sélection. La méthode <xref:System.Xml.XmlNode.SelectNodes%2A> retourne un objet <xref:System.Xml.XmlNodeList> qui contient les nœuds correspondants.  
  
 L'exemple suivant utilise la méthode <xref:System.Xml.XmlNode.SelectSingleNode%2A> pour sélectionner le premier nœud `book` dans lequel le nom de l'auteur répond aux critères spécifiés. Le fichier bookstore.xml (qui est fourni à la fin de cette rubrique) est utilisé comme fichier d'entrée.  
  
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
  
 L'exemple suivant utilise la méthode <xref:System.Xml.XmlNode.SelectNodes%2A> pour sélectionner tous les nœuds book dont le prix est supérieur à un montant spécifié. Puis le prix de chaque book dans la liste sélectionnée est réduit à l'aide d'un programme de dix pour cent. Enfin, le fichier mis à jour est écrit dans la console. Le fichier bookstore.xml (qui est fourni à la fin de cette rubrique) est utilisé comme fichier d'entrée.  
  
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
  
 Les exemples ci-dessus commencent la requête XPath à l’élément de document. La définition du point de départ pour la requête XPath définit le nœud de contexte, qui constitue le point de départ de la requête XPath. Si vous ne souhaitez pas commencer à l'élément de document, mais au premier enfant de l'élément de document, vous pouvez coder l'instruction de sélection illustrée comme suit :  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Tous les objets <xref:System.Xml.XmlNodeList> sont synchronisés avec le document sous-jacent. Par conséquent, si vous itérez via la liste de nœuds et modifiez la valeur d'un nœud, celui-ci est également mis à jour dans le document dont il provient. Notez que, dans l'exemple précédent, lorsqu'un nœud est modifié dans la classe <xref:System.Xml.XmlNodeList> sélectionnée, le document sous-jacent est également modifié.  
  
> [!NOTE]
> En cas de modification du document sous-jacent, il est recommandé de réexécuter la sélection. Si le nœud modifié fait partie de ceux qui peuvent entraîner l'ajout du nœud à la liste dans laquelle il ne figure pas encore ou sa suppression de la liste, il n'est pas garanti que la liste de nœuds est à jour.  
  
## <a name="namespaces-in-xpath-expressions"></a>Espaces de noms dans les expressions XPath  

 Les expressions XPath peuvent inclure des espaces de noms. La résolution d'espace de noms n'est pas prise en charge par l'objet <xref:System.Xml.XmlNamespaceManager>. Si l'expression XPath comprend un préfixe, celui-ci et l'URI d'espace de noms doivent être ajoutés à l'objet <xref:System.Xml.XmlNamespaceManager> et l'objet <xref:System.Xml.XmlNamespaceManager> est transmis à la méthode <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> ou <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29>. Remarquez que les exemples de code ci-dessus utilisent le <xref:System.Xml.XmlNamespaceManager> pour trouver l'espace de noms du document bookstore.xml.  
  
> [!NOTE]
> Si l’expression XPath n’inclut pas de préfixe, l’URI (Uniform Resource Identifier) d’espace de noms est réputé être l’espace de noms vide. Si votre code XML inclut un espace de noms par défaut, vous devez toujours ajouter un préfixe et un URI d'espace de noms à l'objet <xref:System.Xml.XmlNamespaceManager> ; sinon, aucun nœud n'est sélectionné.  
  
#### <a name="input-file"></a>Fichier d'entrée  

 Le fichier bookstore.xml suivant est utilisé comme fichier d'entrée dans les exemples de cette rubrique :  
  
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
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
