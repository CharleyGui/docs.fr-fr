---
title: Suppression de données XML à l'aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: fa331757fac3f30ee86a24bbd0ee12b5f1031a4b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288665"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Suppression de données XML à l'aide de XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes permettant de supprimer des nœuds et des valeurs d'un document XML. Pour pouvoir utiliser ces méthodes, vous devez pouvoir modifier l'objet <xref:System.Xml.XPath.XPathNavigator>, ce qui signifie que sa propriété <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> doit être `true`.  
  
 Les objets <xref:System.Xml.XPath.XPathNavigator> qui permettent d'éditer un document XML sont créés par la méthode <xref:System.Xml.XmlDocument.CreateNavigator%2A> de la classe <xref:System.Xml.XmlDocument>. Les objets <xref:System.Xml.XPath.XPathNavigator> créés par la classe <xref:System.Xml.XPath.XPathDocument> sont en lecture seule et toute tentative d'utilisation des méthodes de modification d'un objet <xref:System.Xml.XPath.XPathNavigator> créé par un objet <xref:System.Xml.XPath.XPathDocument> se traduit par un objet <xref:System.NotSupportedException>.  
  
 Pour plus d’informations sur la création d’objets <xref:System.Xml.XPath.XPathNavigator> modifiables, consultez [Lecture de données XML à l’aide de XPathDocument et XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Suppression de nœuds  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> permettant de supprimer des nœuds d'un document XML.  
  
### <a name="removing-a-node"></a>Suppression d'un nœud  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> permettant de supprimer d'un document XML le nœud actuel sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné.  
  
 Une fois qu'un nœud a été supprimé à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>, il n'est plus accessible depuis la racine de l'objet <xref:System.Xml.XmlDocument>. Après la suppression d'un nœud, l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné sur le nœud parent du nœud supprimé.  
  
 Une suppression n'affecte en rien la position des objets <xref:System.Xml.XPath.XPathNavigator> positionnés sur le nœud supprimé. Ces objets <xref:System.Xml.XPath.XPathNavigator> sont valides dans le sens où ils peuvent se déplacer dans la sous-arborescence supprimée, mais ils ne peuvent pas être déplacés vers le nœud principal avec les méthodes ordinaires de navigation dans les collections de nœuds de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> La méthode <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> peut être utilisée pour redéplacer ces objets <xref:System.Xml.XPath.XPathNavigator> vers l’arborescence de nœuds principale ou depuis l’arborescence de nœuds principale vers la sous-arborescence supprimée.  
  
 Dans l'exemple suivant, l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` est supprimé à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>. Après la suppression de l'élément <xref:System.Xml.XPath.XPathNavigator>, l'objet `price` est positionné sur l'élément `book` parent.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Suppression d'un nœud d'attribut  
 Les nœuds d'attribut d'un document XML se suppriment à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.  
  
 Une fois qu'un nœud d'attribut a été supprimé, il n'est plus accessible depuis le nœud racine d'un objet <xref:System.Xml.XmlDocument> et l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné sur l'élément parent.  
  
#### <a name="default-attributes"></a>Attributs par défaut  
 Quelle que soit la méthode utilisée pour la suppression des attributs, la suppression d'attributs définis comme des attributs par défaut dans la DTD ou dans le schéma XML du document XML est sujette à des restrictions spéciales. Les attributs par défaut ne peuvent pas être supprimés, à moins que l'élément auquel ils appartiennent ne le soit également. Il y a toujours des attributs par défaut pour les éléments pour lesquels des attributs par défaut ont été déclarés ; par conséquent, la suppression d'un attribut par défaut entraîne l'insertion, dans l'élément, d'un attribut de remplacement qui est initialisé à la valeur par défaut déclarée.  
  
## <a name="removing-values"></a>Suppression de valeurs  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> permettant de supprimer des valeurs typées et non typées d'un document XML.  
  
### <a name="removing-untyped-values"></a>Suppression de valeurs non typées  
 La méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> insère simplement la valeur `string` non typée transmise sous la forme d'un paramètre comme la valeur du nœud sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné. La transmission d'une chaîne vide à la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> supprime la valeur du nœud actuel.  
  
 L'exemple suivant supprime la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Suppression de valeurs typées  
 Si le type d'un nœud est un type simple des schémas XML du W3C, la nouvelle valeur insérée par la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> est vérifiée par rapport aux facettes du type simple avant d'être définie. Si la nouvelle valeur n'est pas valide par rapport au type du nœud (par exemple, une valeur est définie sur `-1` pour un élément dont le type est `xs:positiveInteger`), une exception se produit. De même, la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> ne peut pas recevoir la valeur `null` comme paramètre. Par conséquent, la suppression de la valeur d'un nœud typé doit être conforme au type de schéma du nœud.  
  
 L'exemple suivant supprime la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> en définissant la valeur sur `0`. La valeur du nœud n'est pas supprimée, mais le prix du livre a été supprimé d'après son type de données (`xs:decimal`).  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a>Nœuds d'espace de noms  
 Il est impossible de supprimer des nœuds d'espace de noms d'un objet <xref:System.Xml.XmlDocument>. Toute tentative de suppression des nœuds d'espace de noms avec la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> produit une exception.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Propriétés InnerXml et OuterXml  
 Les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> modifient le balisage XML des nœuds sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.  
  
 La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné avec le contenu analysé de la `string` XML donnée. De même, la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné, ainsi que le nœud actuel proprement dit.  
  
 Outre les méthodes décrites dans cette rubrique, les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> permettent de supprimer des nœuds et des valeurs d'un document XML. Pour plus d'informations sur l'utilisation des propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pour modifier des nœuds, consultez la rubrique [Modification de données XML à l’aide de XPathNavigator](modify-xml-data-using-xpathnavigator.md).  
  
## <a name="saving-an-xml-document"></a>Enregistrement d'un document XML  
 L'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument> suite aux méthodes décrites dans cette rubrique s'effectue à l'aide des méthodes de la classe <xref:System.Xml.XmlDocument>. Pour plus d'informations sur l'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument>, consultez [Enregistrement et écriture d'un document](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)
- [Insertion de données XML à l’aide de XPathNavigator](insert-xml-data-using-xpathnavigator.md)
- [Modification de données XML à l’aide de XPathNavigator](modify-xml-data-using-xpathnavigator.md)
