---
title: Accès à des données XML fortement typées à l'aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: e6ec30e3c7c2318b199122cd63c7f56584707a98
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158049"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Accès à des données XML fortement typées à l'aide de XPathNavigator
En tant qu’instance du modèle de données XPath 2.0, la classe <xref:System.Xml.XPath.XPathNavigator> peut contenir des données fortement typées correspondant aux types CLR (Common Language Runtime) courants. Conformément au modèle de données XPath 2.0, seuls les éléments et les attributs peuvent contenir des données fortement typées. La classe <xref:System.Xml.XPath.XPathNavigator> offre des mécanismes d'accès aux données dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> sous la forme de données fortement typées et des mécanismes de conversion d'un type de données en un autre.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informations sur le type exposées par XPathNavigator  
 D'un point de vue technique, les données XML 1.0 ne présentent pas de type, sauf si elles sont traitées avec une DTD, un schéma de langage XSD (XML schema definition) ou un autre mécanisme. Un certain nombre de catégories d'informations sur le type peuvent être associées à un attribut ou un élément XML.  
  
- Types CLR simples : aucun des langages de schéma XML ne prend directement en charge les types CLR (Common Language Runtime). Puisqu'il est utile de pouvoir afficher du contenu d'attribut ou d'élément simple en tant que type CLR le plus approprié, tout contenu simple peut être typé <xref:System.String> en l'absence d'informations de schéma avec des informations complémentaires sur le schéma qui redéfinissent potentiellement ce contenu en type plus approprié. La propriété <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> permet de trouver le type CLR le plus adapté à un contenu d'attribut ou d'élément simple. Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Listes de types (CLR) simples : un élément ou un attribut avec du contenu simple peut contenir une liste de valeurs séparées par des espaces blancs. Les valeurs sont spécifiées par un schéma XML comme « type de liste ». En l'absence d'un schéma XML, un tel contenu simple est traité comme un nœud de texte simple. Si un schéma XML est disponible, ce contenu simple peut être exposé comme une série de valeurs atomiques ayant chacune un type simple qui correspond à un ensemble d'objets CLR. Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Valeur typée : élément ou attribut validé par rapport à un schéma avec un type simple qui présente une valeur typée. Cette valeur est un type primitif tel qu'un type numérique, de chaîne ou de date. Tous les types intégrés simples de XSD peuvent être mappés à des types CLR fournissant un accès à la valeur d'un nœud en tant que type le plus approprié, au lieu d'un simple objet <xref:System.String>. Un élément avec des attributs ou des éléments enfants est considéré comme un type complexe. La valeur typée d'un type complexe avec un contenu simple (uniquement des nœuds de texte comme enfants) est identique à celui du type simple de son contenu. La valeur typée d'un type complexe avec un contenu complexe (un ou plusieurs éléments enfants) est la valeur de chaîne de la concaténation de tous ses nœuds de texte enfant retournée sous la forme d'un objet <xref:System.String>. Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Nom du type spécifique au langage du schéma : dans la plupart des cas, les types CLR, définis comme l'effet secondaire de l'application d'un schéma externe, permettent de fournir un accès à la valeur d'un nœud. Toutefois, dans certaines situations, il se peut que vous souhaitiez examiner le type associé à un schéma particulier appliqué à un document XML. Par exemple, il se peut que vous souhaitiez effectuer une recherche dans un document XML et extraire tous les éléments identifiés comme ayant un contenu de type « OrdreAchat » conformément à un schéma associé. Ces informations sur le type ne peuvent être définies que suite à une validation de schéma et sont accessibles via les propriétés <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> et <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>. Pour plus d'informations, consultez la section ci-dessous sur le jeu d'informations de post-validation de schéma (PSVI).  
  
- Réflexion du type spécifique au langage du schéma : dans d'autres cas, il se peut que vous souhaitiez obtenir d'autres détails sur le type spécifique au schéma appliqué à un document XML. Par exemple, lors de la lecture d'un fichier XML; il se peut que vous souhaitiez extraire l'attribut `maxOccurs` pour chaque nœud valide du document XML pour effectuer certains calculs personnalisés. Étant donné que ces informations ne sont définies que via la validation de schéma, elles sont accessibles par le biais de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>. Pour plus d'informations, consultez la section ci-dessous sur le jeu d'informations de post-validation de schéma (PSVI).  
  
## <a name="xpathnavigator-typed-accessors"></a>Accesseurs typés XPathNavigator  
 Le tableau suivant illustre les différentes propriétés et méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> pouvant être utilisées pour accéder aux informations sur le type à propos d'un nœud.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Contient les informations sur le type de schéma XML pour le nœud s'il est valide.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Contient le jeu d’informations de post-validation de schéma du nœud ajouté après validation, notamment les informations sur le type de schéma XML et sur la validité.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Type CLR de la valeur typée du nœud.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Contenu du nœud si au moins une valeur CLR du type correspondant le plus au type de schéma XML du nœud.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Boolean> conformément aux règles de conversion de XPath 2.0 pour `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.DateTime> conformément aux règles de conversion de XPath 2.0 pour `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Double> conformément aux règles de conversion de XPath 2.0 pour `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Int32> conformément aux règles de conversion de XPath 2.0 pour `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Int64> conformément aux règles de conversion de XPath 2.0 pour `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Contenu du nœud cast en type cible conformément aux règles de conversion de XPath 2.0.|  
  
 Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Jeu d'informations de post-validation de schéma (PSVI)  
 Un processeur de schéma XML accepte un jeu d'informations XML et le convertit en jeu d'informations de post-validation de schéma (PSVI). Un PSVI est le jeu d'informations XML d'entrée original auquel sont ajoutés les nouveaux éléments d'informations et les nouvelles propriétés, elles-mêmes ajoutées aux éléments d'informations existants. Trois grandes classes d'informations sont ajoutées au jeu d'informations XML du PSVI exposé par l'objet <xref:System.Xml.XPath.XPathNavigator>.  
  
1. Résultats de validation : informations indiquant si un élément ou un attribut a été correctement validé ou non. Ces informations sont exposées par la propriété <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
2. Informations par défaut : indiquent si la valeur de l'élément ou de l'attribut a été obtenue via des valeurs par défaut spécifiées dans le schéma ou non. Ces informations sont exposées par la propriété <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
3. Annotations de type : références aux composants de schéma pouvant être des définitions de types ou des déclarations d'élément et d'attribut. La propriété <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> de l'objet <xref:System.Xml.XPath.XPathNavigator> contient les informations spécifiques sur le type du nœud s'il est valide. Si la validité d'un nœud est inconnue, par exemple s'il a été validé, puis modifié, la propriété <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> est définie sur `null`, mais les informations sur le type sont toujours disponibles à partir des différentes propriétés de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
 L’exemple suivant illustre l’utilisation des informations dans le jeu d’informations de post-validation de schéma exposé par l’objet <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 L'exemple prend le fichier `books.xml` comme entrée.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 L'exemple prend également le schéma `books.xsd` comme entrée.  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Obtention de valeurs typées à l'aide des propriétés ValueAs  
 Vous pouvez récupérer la valeur typée d'un nœud en accédant à la propriété <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> de l'objet <xref:System.Xml.XPath.XPathNavigator>. Dans certains cas, il se peut que vous souhaitiez convertir la valeur typée d'un nœud en un type différent. Un exemple courant consiste à obtenir une valeur numérique à partir d'un nœud XML. Considérez par exemple le document XML non typé et non validé suivant.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Si l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné sur l'élément `price`, la propriété <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> serait `null`, la propriété <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> serait l'objet <xref:System.String> et la propriété <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> serait la chaîne `10.00`.  
  
 Toutefois, il est toujours possible d'extraire la valeur sous la forme d'une valeur numérique à l'aide des propriétés et de la méthode <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> ou <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>. L'exemple suivant illustre l'exécution de ce type de conversion à l'aide de la méthode <xref:System.Xml.XPath.XPathItem.ValueAs%2A>.  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Prise en charge du type dans les classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [Traitement des données XML à l’aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigation dans la collection de nœuds à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Extraction de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
