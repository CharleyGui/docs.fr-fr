---
title: Insertion de données XML à l’aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 1dbe1a709f7c1b527a1754ab943a0a10ff52c6e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289185"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Insertion de données XML à l’aide de XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes permettant d'insérer des nœuds frères, enfants et d'attribut dans un document XML. Pour pouvoir utiliser ces méthodes, vous devez pouvoir modifier l'objet <xref:System.Xml.XPath.XPathNavigator>, ce qui signifie que sa propriété <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> doit être `true`.  
  
 Les objets <xref:System.Xml.XPath.XPathNavigator> qui permettent d'éditer un document XML sont créés par la méthode <xref:System.Xml.XmlDocument.CreateNavigator%2A> de la classe <xref:System.Xml.XmlDocument>. Les objets <xref:System.Xml.XPath.XPathNavigator> créés par la classe <xref:System.Xml.XPath.XPathDocument> sont en lecture seule et toute tentative d'utilisation des méthodes de modification d'un objet <xref:System.Xml.XPath.XPathNavigator> créé par un objet <xref:System.Xml.XPath.XPathDocument> se traduit par un objet <xref:System.NotSupportedException>.  
  
 Pour plus d’informations sur la création d’objets <xref:System.Xml.XPath.XPathNavigator> modifiables, consultez [Lecture de données XML à l’aide de XPathDocument et XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Insertion de nœuds  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit des méthodes permettant d'insérer des nœuds frères, enfants et d'attribut dans un document XML. Ces méthodes permettent d'insérer des nœuds et des attributs à différents emplacements par rapport à la position actuelle d'un objet <xref:System.Xml.XPath.XPathNavigator> et sont décrites dans les sections suivantes.  
  
### <a name="inserting-sibling-nodes"></a>Insertion de nœuds frères  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes suivantes pour l'insertion de nœuds frères.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Ces méthodes insèrent des nœuds frères avant et après le nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.  
  
 Les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> sont surchargées et acceptent un objet `string`, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> contenant le nœud frère à ajouter comme paramètre. Ces deux méthodes retournent également un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds frères.  
  
 Les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> insèrent un nœud frère unique avant et après le nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné à l'aide du préfixe d'espace de noms, du nom local, de l'URI d'espace de noms et de la valeur spécifiés comme paramètres.  
  
 Dans l'exemple suivant, un nouvel élément `pages` est inséré avant l'élément `price` enfant du premier élément `book` du fichier `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>, voir la documentation de référence sur la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="inserting-child-nodes"></a>Insertion de nœuds enfants  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes suivantes pour l'insertion de nœuds enfants.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Ces méthodes ajoutent des nœuds enfants à la fin et au début de la liste de nœuds enfants du nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.  
  
 À l'instar des méthodes décrites dans la section sur l'insertion de nœuds frères, les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> acceptent un objet `string`, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> contenant le nœud enfant à ajouter comme paramètre. Ces deux méthodes retournent également un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds enfants.  
  
 À l'instar également des méthodes décrites dans la section sur l'insertion de nœuds frères, les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> insèrent un nœud enfant unique à la fin et au début de la liste de nœuds enfants du nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné à l'aide du préfixe d'espace de noms, du nom local, de l'URI d'espace de noms et de la valeur spécifiés comme paramètres.  
  
 Dans l'exemple suivant, un nouvel élément `pages` enfant est ajouté à la liste d'éléments enfants du premier élément `book` du fichier `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>, voir la documentation de référence sur la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="inserting-attribute-nodes"></a>Insertion de nœuds d'attribut  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes suivantes pour l'insertion de nœuds d'attribut.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Ces méthodes insèrent des nœuds d'attribut sur le nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné. La méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> crée un nœud d'attribut sur le nœud d'élément sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné à l'aide du préfixe d'espace de noms, du nom local, de l'URI d'espace de noms et de la valeur spécifiés comme paramètres. La méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> retourne un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds d'attribut.  
  
 Dans l'exemple suivant, de nouveaux attributs `discount` et `currency` sont créés sur l'élément `price` enfant du premier élément `book` du fichier `contosoBooks.xml` à l'aide de l'objet <xref:System.Xml.XmlWriter> retourné par la méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> et <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>, voir la documentation de référence sur la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="copying-nodes"></a>Copie de nœuds  
 Dans certains cas, il se peut que vous souhaitiez remplir un document XML avec le contenu d'un autre document XML. Les classes <xref:System.Xml.XPath.XPathNavigator> et <xref:System.Xml.XmlWriter> peuvent copier des nœuds dans un objet <xref:System.Xml.XmlDocument> à partir d'un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> existant.  
  
 Les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> présentent des surcharges qui peuvent accepter un objet <xref:System.Xml.XPath.XPathNavigator> ou <xref:System.Xml.XmlReader> comme paramètre.  
  
 La méthode <xref:System.Xml.XmlWriter.WriteNode%2A> de la classe <xref:System.Xml.XmlWriter> présente des surcharges qui peuvent accepter un objet <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator>.  
  
 L'exemple suivant copie tous les éléments `book` d'un document dans un autre.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a>Insertion de valeurs  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> afin d'insérer des valeurs pour un nœud dans un objet <xref:System.Xml.XmlDocument>.  
  
### <a name="inserting-untyped-values"></a>Insertion de valeurs non typées  
 La méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> insère simplement la valeur `string` non typée transmise sous la forme d'un paramètre comme la valeur du nœud sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné. La valeur est insérée sans type ou sans vérifier que la nouvelle valeur est valide par rapport au type de nœud si les informations sur le schéma sont disponibles.  
  
 Dans l'exemple suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> permet de mettre à jour tous les éléments `price` du fichier `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Insertion de valeurs typées  
 Si le type d'un nœud est un type simple des schémas XML du W3C, la nouvelle valeur insérée par la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> est vérifiée par rapport aux facettes du type simple avant d'être définie. Si la nouvelle valeur n'est pas valide par rapport au type du nœud (par exemple, une valeur est définie sur `-1` pour un élément dont le type est `xs:positiveInteger`), une exception se produit.  
  
 L'exemple suivant tente de modifier la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` en valeur <xref:System.DateTime>. Étant donné que le type de schéma XML de l'élément `price` est défini comme `xs:decimal` dans les fichiers `contosoBooks.xsd`, une exception se produit.  
  
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
  
navigator.SetTypedValue(DateTime.Now)  
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
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Propriétés InnerXml et OuterXml  
 Les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> modifient le balisage XML des nœuds sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.  
  
 La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné avec le contenu analysé de la `string` XML donnée. De même, la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné, ainsi que le nœud actuel proprement dit.  
  
 Outre les méthodes décrites dans cette rubrique, les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> peuvent permettre d'insérer des nœuds et des valeurs dans un document XML. Pour plus d'informations sur l'utilisation des propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pour insérer des nœuds et des valeurs, consultez la rubrique [Modification de données XML à l’aide de XPathNavigator](modify-xml-data-using-xpathnavigator.md).  
  
## <a name="namespace-and-xmllang-conflicts"></a>Conflits d'espace de noms et xml:lang  
 Certains conflits relatifs à la portée de l'espace de noms et aux déclarations `xml:lang` peuvent survenir lors de l'insertion de données XML à l'aide des méthodes <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> qui prend les objets <xref:System.Xml.XmlReader> comme paramètres.  
  
 Les conflits d'espace de noms possibles sont les suivants.  
  
- Si un espace de noms se trouve dans la portée du contexte de l'objet <xref:System.Xml.XmlReader> où le préfixe du mappage de l'URI d'espace de noms ne se trouve pas dans le contexte de l'objet <xref:System.Xml.XPath.XPathNavigator>, une nouvelle déclaration d'espace de noms est ajoutée au nœud qui vient d'être inséré.  
  
- Si le même URI d'espace de noms se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, mais dont le préfixe mappé est différent dans les deux contextes, une nouvelle déclaration d'espace de noms est ajoutée au nœud qui vient d'être inséré. Le préfixe et l'URI d'espace de noms de cette déclaration sont ceux de l'objet <xref:System.Xml.XmlReader>.  
  
- Si le même préfixe d'espace de noms se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, mais dont l'URI d'espace de noms mappé est différent dans les deux contextes, une nouvelle déclaration d'espace de noms est ajoutée au nœud qui vient d'être inséré. Celle-ci redéclare ce préfixe avec l'URI d'espace de noms provenant de l'objet <xref:System.Xml.XmlReader>.  
  
- Si le préfixe et l'URI d'espace de noms sont identiques dans le contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, aucune déclaration d'espace de noms n'est ajoutée au nœud qui vient d'être inséré.  
  
> [!NOTE]
> La description ci-dessus s'applique également aux déclarations d'espaces de noms ayant pour préfixe la `string` vide (par exemple, la déclaration d'espace de noms par défaut).  
  
 Les conflits `xml:lang` possibles sont les suivants.  
  
- Si un attribut `xml:lang` se trouve dans la portée du contexte de l'objet <xref:System.Xml.XmlReader>, mais pas de l'objet <xref:System.Xml.XPath.XPathNavigator>, un attribut `xml:lang` dont la valeur est reprise dans l'objet <xref:System.Xml.XmlReader> est ajouté au nœud qui vient d'être inséré.  
  
- Si un attribut `xml:lang` se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, mais si chacun présente une valeur différente, un attribut `xml:lang` dont la valeur est reprise dans l'objet <xref:System.Xml.XmlReader> est ajouté au nœud qui vient d'être inséré.  
  
- Si un attribut `xml:lang` se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator> et si chacun présente la même valeur, aucun attribut `xml:lang` n'est ajouté au nœud qui vient d'être inséré.  
  
- Si un attribut `xml:lang` se trouve dans la portée du contexte de l'objet <xref:System.Xml.XPath.XPathNavigator> et si aucun n'existe dans le contexte de l'objet <xref:System.Xml.XmlReader>, aucun attribut `xml:lang` n'est ajouté au nœud qui vient d'être inséré.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Insertion de nœuds avec XmlWriter  
 Les méthodes permettant d'insérer des nœuds frères, enfants et d'attribut décrites dans la section sur l'insertion de nœuds et de valeurs sont surchargées. Les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> et <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> retournent un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds.  
  
### <a name="unsupported-xmlwriter-methods"></a>Méthodes XmlWriter non prises en charge  
 Toutes les méthodes permettant d’écrire des informations dans un document XML à l’aide de la classe <xref:System.Xml.XmlWriter> ne sont pas prises en charge par la classe <xref:System.Xml.XPath.XPathNavigator> en raison de la différence entre le modèle de données XPath et le DOM (Document Object Model).  
  
 Le tableau suivant décrit les méthodes de la classe <xref:System.Xml.XmlWriter> non prises en charge par la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Lève une exception <xref:System.NotSupportedException>.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorée au niveau racine et lève une exception <xref:System.NotSupportedException> en cas d'appel à tout autre niveau du document XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Traitée comme un appel à la méthode <xref:System.Xml.XmlWriter.WriteString%2A> pour le ou les caractères équivalents.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Traitée comme un appel à la méthode <xref:System.Xml.XmlWriter.WriteString%2A> pour le ou les caractères équivalents.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Traitée comme un appel à la méthode <xref:System.Xml.XmlWriter.WriteString%2A> pour le ou les caractères équivalents.|  
  
 Pour plus d'informations sur la classe <xref:System.Xml.XmlWriter>, voir la documentation de référence sur la classe <xref:System.Xml.XmlWriter>.  
  
### <a name="multiple-xmlwriter-objects"></a>Objets XmlWriter multiples  
 Il est possible que plusieurs objets <xref:System.Xml.XPath.XPathNavigator> pointent sur différentes parties d'un document XML avec au moins un objet <xref:System.Xml.XmlWriter> ouvert. Plusieurs objets <xref:System.Xml.XmlWriter> sont autorisés et pris en charge dans des scénarios monothread.  
  
 Les remarques suivantes sont importantes en cas d'utilisation de plusieurs objets <xref:System.Xml.XmlWriter>.  
  
- Les fragments XML écrits par les objets <xref:System.Xml.XmlWriter> sont ajoutés au document XML en cas d'appel de la méthode <xref:System.Xml.XmlWriter.Close%2A> de chaque objet <xref:System.Xml.XmlWriter>. Dans les autres cas, l'objet <xref:System.Xml.XmlWriter> écrit un fragment déconnecté. Si une opération est effectuée sur le document XML, avant l'appel de <xref:System.Xml.XmlWriter>, aucun fragment en cours d'écriture par un objet <xref:System.Xml.XmlWriter.Close%2A> n'est affecté.  
  
- Si un objet <xref:System.Xml.XmlWriter> ouvert existe dans une sous-arborescence XML particulière et si cette sous-arborescence est supprimée, l’objet <xref:System.Xml.XmlWriter> peut encore être ajouté à la sous-arborescence. La sous-arborescence devient simplement un fragment supprimé.  
  
- Si plusieurs objets <xref:System.Xml.XmlWriter> sont ouverts au même point du document XML, ils sont ajoutés au document XML dans l'ordre dans lequel les objets <xref:System.Xml.XmlWriter> sont fermés, pas dans l'ordre dans lequel ils ont été ouverts.  
  
 L'exemple suivant crée un objet <xref:System.Xml.XmlDocument> et un objet <xref:System.Xml.XPath.XPathNavigator>, puis utilise l'objet <xref:System.Xml.XmlWriter> retourné par la méthode <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> pour créer la structure du premier livre du fichier `books.xml`. L'exemple l'enregistre ensuite comme fichier `book.xml`.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a>Enregistrement d'un document XML  
 L'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument> suite aux méthodes décrites dans cette rubrique s'effectue à l'aide des méthodes de la classe <xref:System.Xml.XmlDocument>. Pour plus d'informations sur l'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument>, consultez [Enregistrement et écriture d'un document](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)
- [Modification de données XML à l’aide de XPathNavigator](modify-xml-data-using-xpathnavigator.md)
- [Suppression de données XML à l'aide de XPathNavigator](remove-xml-data-using-xpathnavigator.md)
