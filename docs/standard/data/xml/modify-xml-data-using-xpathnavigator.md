---
title: Modification de données XML à l’aide de XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 79bb23b77557a5a10f021e2167c9fa8ae3ee044a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830192"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Modification de données XML à l’aide de XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes permettant de modifier les nœuds et les valeurs d'un document XML. Pour pouvoir utiliser ces méthodes, vous devez pouvoir modifier l'objet <xref:System.Xml.XPath.XPathNavigator>, ce qui signifie que sa propriété <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> doit être `true`.  
  
 Les objets <xref:System.Xml.XPath.XPathNavigator> qui permettent d'éditer un document XML sont créés par la méthode <xref:System.Xml.XmlDocument.CreateNavigator%2A> de la classe <xref:System.Xml.XmlDocument>. Les objets <xref:System.Xml.XPath.XPathNavigator> créés par la classe <xref:System.Xml.XPath.XPathDocument> sont en lecture seule et toute tentative d'utilisation des méthodes de modification d'un objet <xref:System.Xml.XPath.XPathNavigator> créé par un objet <xref:System.Xml.XPath.XPathDocument> se traduit par un objet <xref:System.NotSupportedException>.  
  
 Pour plus d’informations sur la création d’objets <xref:System.Xml.XPath.XPathNavigator> modifiables, consultez [Lecture de données XML à l’aide de XPathDocument et XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Modification de nœuds  
 Une technique simple de modification de la valeur d'un nœud consiste à utiliser les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
 Le tableau suivant répertorie les effets de ces méthodes sur différents types de nœuds.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Données modifiées|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Non pris en charge.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Contenu de l'élément.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Valeur de l'attribut.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Texte.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Contenu, cible exclue.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Contenu du commentaire.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Non pris en charge.|  
  
> [!NOTE]
> La modification des nœuds <xref:System.Xml.XPath.XPathNodeType.Namespace> ou <xref:System.Xml.XPath.XPathNodeType.Root> n'est pas prise en charge.  
  
 La classe <xref:System.Xml.XPath.XPathNavigator> fournit également un ensemble de méthodes permettant d'insérer et de supprimer des nœuds. Pour plus d’informations sur l’insertion et la suppression de nœuds d’un document XML, consultez les rubriques [Insertion de données XML à l’aide de XPathNavigator](insert-xml-data-using-xpathnavigator.md) et [Suppression de données XML à l’aide de XPathNavigator](remove-xml-data-using-xpathnavigator.md).  
  
### <a name="modifying-untyped-values"></a>Modification de valeurs non typées  
 La méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> insère simplement la valeur `string` non typée transmise sous la forme d'un paramètre comme la valeur du nœud sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné. La valeur est insérée sans type ou sans vérifier que la nouvelle valeur est valide par rapport au type de nœud si les informations sur le schéma sont disponibles.  
  
 Dans l'exemple suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> permet de mettre à jour tous les éléments `price` du fichier `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Modification de valeurs typées  
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
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Effets de la modification de données XML fortement typées  
 La <xref:System.Xml.XPath.XPathNavigator> classe utilise le schéma XML W3C comme base pour décrire le XML fortement typé. Les éléments et les attributs ne peuvent pas être annotés avec les informations sur le type en fonction de la validation par rapport au document du W3C sur les schémas XML. Les éléments pouvant contenir d'autres éléments ou attributs sont appelés types complexes, tandis que ceux qui ne peuvent avoir que du contenu textuel sont appelés types simples.  
  
> [!NOTE]
> Les attributs ne peuvent avoir que des types simples.  
  
 Un élément ou attribut peut être considéré comme valide pour le schéma s'il est conforme à toutes les règles spécifiques à sa définition de type. Un élément ayant le type simple `xs:int` doit contenir une valeur numérique comprise entre -2147483648 et 2147483647 pour être valide pour le schéma. Pour les types complexes, la validité de l'élément pour le schéma dépend de la validité pour le schéma de ses attributs et éléments enfants. Donc, si un élément est valide par rapport à sa définition de type complexe, tous ses attributs et éléments enfants sont valides par rapport à leur définition de type. De même, si un seul attribut ou élément enfant d'un élément n'est pas valide par rapport à sa définition de type ou dispose d'une validité inconnue, l'élément est également non valide ou de validité inconnue.  
  
 Étant donné que la validité d'un élément dépend de la validité de ses attributs et éléments enfants, les modifications apportées à l'un ou à l'autre se traduisent par une altération de la validité de l'élément s'il était précédemment valide. En particulier, si les attributs ou les éléments enfants d'un élément sont insérés, mis à jour ou supprimés, la validité de l'élément devient inconnue. Elle est représentée par la propriété <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de l'élément définie sur <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. En outre, cet effet se répercute vers le haut de manière récursive dans le document XML car la validité de élément parent de l'élément (et de son élément parent, etc.) devient également inconnue.  
  
 Pour plus d'informations sur la validation de schémas et la classe <xref:System.Xml.XPath.XPathNavigator>, voir [Validation de schéma à l’aide de XPathNavigator](schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Modification d'attributs  
 Les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> peuvent permettre de modifier des nœuds d'attribut typés et non typés, ainsi que les autres types de nœuds d'attribut répertoriés dans la section sur la modification de nœuds.  
  
 L'exemple suivant modifie la valeur de l'attribut `genre` du premier élément `book` du fichier `books.xml`.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, voir les sections sur la modification de valeurs non typées et de valeurs typées.  
  
## <a name="innerxml-and-outerxml-properties"></a>Propriétés InnerXml et OuterXml  
 Les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> modifient le balisage XML des nœuds sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.  
  
 La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné avec le contenu analysé de la `string` XML donnée. De même, la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné, ainsi que le nœud actuel proprement dit.  
  
 L'exemple suivant utilise la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pour modifier la valeur de l'élément `price` et insérer un nouvel attribut `discount` dans le premier élément `book` du fichier `contosoBooks.xml`.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
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
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Modification de nœuds d'espace de noms  
 Dans le DOM (Document Object Model), les déclarations d'espaces de noms sont traitées comme des attributs réguliers qui peuvent être insérés, mis à jour et supprimés. La classe <xref:System.Xml.XPath.XPathNavigator> n'autorise pas ce type d'opération sur les nœuds d'espace de noms car toute modification de la valeur d'un nœud d'espace de noms peut modifier l'identité des éléments et attributs dans la portée du nœud d'espace de noms comme illustré dans l'exemple suivant.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Si l'exemple XML ci-dessus est modifié de la manière suivante, chaque élément est effectivement renommé dans le document car la valeur de l'URI d'espace de noms de chaque élément est modifiée.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 L'insertion d'espaces de noms n'entrant pas en conflit avec les déclarations d'espaces de noms dans la portée dans laquelle ils sont insérés est autorisée par la classe <xref:System.Xml.XPath.XPathNavigator>. Dans ce cas, les déclarations d'espaces de noms ne sont pas déclarées dans des portées inférieures du document XML et ne se traduisent pas par l'attribution d'un nouveau nom comme illustré dans l'exemple suivant.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Si l'exemple XML ci-dessus est modifié de la manière suivante, les déclarations d'espaces de noms sont correctement propagées dans le document XML sous la portée de l'autre déclaration d'espace de noms.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 Dans l'exemple XML ci-dessus, l'attribut `a:parent-id` est inséré dans l'élément `parent` dans l'espace de noms `http://www.contoso.com/parent-id`. La méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> permet d'insérer l'attribut tout en étant positionné sur l'élément `parent`. La déclaration d'espace de noms `http://www.contoso.com` est automatiquement insérée par la classe <xref:System.Xml.XPath.XPathNavigator> pour conserver la cohérence du reste du document XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Modification de nœuds de référence d'entité  
 Les nœuds de référence d'entité d'un objet <xref:System.Xml.XmlDocument> sont en lecture seule et ne peuvent pas être modifiés à l'aide des classes <xref:System.Xml.XPath.XPathNavigator> ou <xref:System.Xml.XmlNode>. Toute tentative de modification d'un nœud de référence d'entité se traduit par un objet <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Modification de nœuds xsi:nil  
 La recommandation du W3C sur les schémas XML introduit le concept d'élément pouvant prendre la valeur null. Si un élément peut prendre la valeur null, il peut n'avoir aucun contenu et rester valide. Le concept d'élément pouvant prendre la valeur null est similaire à celui d'objet `null`. La principale différence est qu'il est possible d'accéder à un objet `null` de n'importe quelle manière, tandis qu'un élément `xsi:nil` possède toujours des propriétés telles que des attributs accessibles, mais n'ayant aucun contenu (texte ou éléments enfants). L'existence de l'attribut `xsi:nil` présentant la valeur `true` dans un élément d'un document XML permet d'indiquer qu'un élément n'a aucun contenu.  
  
 Si un objet <xref:System.Xml.XPath.XPathNavigator> permet d'ajouter du contenu à un élément valide avec un attribut `xsi:nil` ayant la valeur `true`, la valeur de son attribut `xsi:nil` est définie sur `false`.  
  
> [!NOTE]
> Si le contenu d'un élément possédant un attribut `xsi:nil` défini sur `false` est supprimé, la valeur de l'attribut n'est pas modifiée en `true`.  
  
## <a name="saving-an-xml-document"></a>Enregistrement d'un document XML  
 L'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument> suite aux méthodes de modification décrites dans cette rubrique s'effectue à l'aide des méthodes de la classe <xref:System.Xml.XmlDocument>. Pour plus d'informations sur l'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument>, consultez [Enregistrement et écriture d'un document](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)
- [Insertion de données XML à l’aide de XPathNavigator](insert-xml-data-using-xpathnavigator.md)
- [Suppression de données XML à l'aide de XPathNavigator](remove-xml-data-using-xpathnavigator.md)
