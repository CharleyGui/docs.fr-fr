---
title: Inclusion ou importation de schémas XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: d9a18876d8a5ba3067aa35c617b1e20fce0411f5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710776"
---
# <a name="including-or-importing-xml-schemas"></a>Inclusion ou importation de schémas XML
Un schéma XML peut contenir des éléments `<xs:import />`, `<xs:include />` et `<xs:redefine />`. Ces éléments de schéma réfèrent à d'autres schémas XML qui peuvent être utilisés pour compléter la structure du schéma où ils sont inclus ou importés. Les classes <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> et <xref:System.Xml.Schema.XmlSchemaRedefine> sont mappées à ces éléments dans l'API SOM (Schema Object Model).  
  
## <a name="including-or-importing-an-xml-schema"></a>Inclusion ou importation d'un schéma XML  
 L'exemple de code suivant complète le schéma utilisateur créé dans la rubrique [Création de schémas XML](../../../../docs/standard/data/xml/building-xml-schemas.md) avec le schéma d'adresse. Cette opération rend les types d'adresses disponibles dans le schéma utilisateur.  
  
 Le schéma d'adresse peut être incorporé à l'aide d'éléments `<xs:include />` ou `<xs:import />` pour utiliser les composants du schéma d'adresse tels quels, ou à l'aide d'un élément `<xs:redefine />` pour modifier l'un quelconque de ses composants en fonction des besoins du schéma utilisateur. Le schéma d'adresse ayant un `targetNamespace` différent de celui du schéma utilisateur, on utilise l'élément `<xs:import />` et donc la sémantique d'importation.  
  
 L'exemple de code inclut le schéma d'adresse en plusieurs étapes comme suit.  
  
1. Il ajoute le schéma utilisateur et le schéma d'adresse à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis les compile. Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation des schémas sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.  
  
2. Il extrait les objets <xref:System.Xml.Schema.XmlSchema> compilés, tant pour le schéma utilisateur que pour le schéma d'adresse, de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Les schémas étant compilés, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.  
  
3. Il crée un objet <xref:System.Xml.Schema.XmlSchemaImport>, définit la propriété <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> de l'importation comme étant l'espace de noms du schéma d'adresse, définit la propriété <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> de l'importation comme étant l'objet <xref:System.Xml.Schema.XmlSchema> du schéma d'adresse et ajoute l'importation à la propriété <xref:System.Xml.Schema.XmlSchema.Includes%2A> du schéma utilisateur.  
  
4. Il retraite et compile l'objet <xref:System.Xml.Schema.XmlSchema> modifié du schéma utilisateur à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> et <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit le résultat à la console.  
  
5. Enfin, de manière récursive, il écrit à la console tous les schémas importés dans le schéma utilisateur en utilisant la propriété <xref:System.Xml.Schema.XmlSchema.Includes%2A> du schéma utilisateur. La propriété <xref:System.Xml.Schema.XmlSchema.Includes%2A> fournit l'accès à toutes les inclusions, importations ou redéfinitions ajoutées à un schéma.  
  
 Voici l'exemple de code complet et les schémas utilisateur et d'adresse écrits à la console.  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
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
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 Pour plus d'informations sur les éléments `<xs:import />`, `<xs:include />` et `<xs:redefine />`, ainsi que sur les classes <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> et <xref:System.Xml.Schema.XmlSchemaRedefine>, consultez [W3C XML Schema](https://www.w3.org/XML/Schema) (en anglais) et la documentation de référence de la classe d'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du Modèle Objet du schéma XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Lecture et écriture de schémas XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Création de schémas XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Traversée de schémas XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Modification de schémas XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XmlSchemaSet pour la compilation de schémas](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
