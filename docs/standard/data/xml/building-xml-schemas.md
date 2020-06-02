---
title: Création de schémas XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: adc1a10bb9acb14ee88589c13e28c49773e42100
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291589"
---
# <a name="building-xml-schemas"></a>Création de schémas XML
Les classes de l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> correspondent aux structures définies dans la recommandation du W3C (World Wide Web Consortium) sur les schémas XML et peuvent permettre de créer des schémas XML en mémoire.  
  
## <a name="building-an-xml-schema"></a>Création d'un schéma XML  
 Dans les exemples de code suivants, l'API du SOM permet de créer un schéma XML client en mémoire.  
  
### <a name="creating-element-and-attributes"></a>Création d'éléments et d'attributs  
 Les exemples de codes génèrent le schéma client à partir de rien en créant les attributs et les éléments enfants, puis les types qui leur correspondent et enfin les éléments de niveau supérieur.  
  
 Dans l'exemple de code suivant, les éléments `FirstName` et `LastName` ainsi que l'attribut `CustomerId` du schéma client sont créés à l'aide des classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAttribute> du SOM. Exception faite des propriétés <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAttribute>, qui correspondent à l'attribut « name » des éléments `<xs:element />` et `<xs:attribute />` d'un schéma XML, tous les autres attributs autorisés par le schéma (`defaultValue`, `fixedValue`, `form`, etc.) possèdent des propriétés correspondantes dans les classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAttribute>.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Création de types de schéma  
 Le contenu des éléments et des attributs est défini par leurs types. Pour créer des éléments et des attributs dont les types sont l'un des types de schéma intégrés, la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute> sont définies sur le nom qualifié correspondant du type intégré à l'aide de la classe <xref:System.Xml.XmlQualifiedName>. Pour créer un type défini par l'utilisateur pour les éléments et les attributs, un nouveau type simple ou complexe est créé à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSimpleType> ou <xref:System.Xml.Schema.XmlSchemaComplexType>.  
  
> [!NOTE]
> Pour créer des types simples ou complexes sans nom qui sont des enfants anonymes d'un élément ou d'un attribut (seuls les types simples s'appliquent aux attributs), définissez la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute> sur le type simple ou complexe sans nom au lieu de la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute>.  
  
 Les schémas XML autorisent les types simples nommés et sans nom à être dérivés par restriction à partir d'autres types simples (intégrés ou définis par l'utilisateur) ou construits comme une liste ou l'union d'autres types simples. La classe <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> permet de créer un type simple par restriction du type `xs:string` intégré. Vous pouvez également utiliser les classes <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> ou <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> pour créer des types liste ou union. La propriété <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> indique s'il s'agit d'une union, d'une liste ou d'une restriction de types simples.  
  
 Dans l'exemple de code suivant, le type de l'élément `FirstName` est le type `xs:string` intégré, le type de l'élément `LastName` est un type simple nommé qui est une restriction du type `xs:string`, avec une valeur de facette `MaxLength` de 20 et le type de l'attribut `CustomerId` est le type `xs:positiveInteger` intégré. L'élément `Customer` est un type complexe anonyme dont la particule est la séquence des éléments `FirstName` et `LastName` et dont les attributs contiennent l'attribut `CustomerId`.  
  
> [!NOTE]
> Vous pouvez également utiliser les classes <xref:System.Xml.Schema.XmlSchemaChoice> ou <xref:System.Xml.Schema.XmlSchemaAll> comme particule du type complexe pour répliquer les sémantiques `<xs:choice />` ou `<xs:all />`.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Création et compilation de schémas  
 À ce stade, les attributs et les éléments enfants, les types qui leur correspondent et les éléments `Customer` de niveau supérieur ont été créés en mémoire à l'aide de l'API du SOM. Dans l'exemple de code suivant, l'élément de schéma est créé à l'aide de la classe <xref:System.Xml.Schema.XmlSchema>, les éléments de niveau supérieur et les types y sont ajoutés à l'aide de la propriété <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> et le schéma complet est compilé à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit dans la console.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 La méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> valide le schéma client par rapport aux règles d'un schéma XML et rend les propriétés de post-compilation de schéma disponibles.  
  
> [!NOTE]
> Toutes les propriétés de post-compilation de schéma de l’API du SOM diffèrent de celles du jeu d’informations de post-validation de schéma.  
  
 L'objet <xref:System.Xml.Schema.ValidationEventHandler> ajouté à <xref:System.Xml.Schema.XmlSchemaSet> est un délégué qui appelle la méthode de rappel `ValidationCallback` pour gérer les erreurs et les avertissements de validation de schéma.  
  
 L'exemple de code suivant est complet et le schéma client est écrit dans la console.  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du Modèle Objet du schéma XML](xml-schema-object-model-overview.md)
- [Lecture et écriture de schémas XML](reading-and-writing-xml-schemas.md)
- [Traversée de schémas XML](traversing-xml-schemas.md)
- [Modification de schémas XML](editing-xml-schemas.md)
- [Inclusion ou importation de schémas XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md)
- [Jeu d'informations de post-compilation de schéma](post-schema-compilation-infoset.md)
