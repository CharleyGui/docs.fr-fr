---
title: Modification de schémas XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: e900a558c6599d00e8f848ea50e5b30985475d1b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830257"
---
# <a name="editing-xml-schemas"></a>Modification de schémas XML

La modification d’un schéma XML est l’une des fonctionnalités les plus importantes du SOM (Schema Object Model). Toutes les propriétés de pré-compilation de schéma du SOM peuvent être utilisées pour changer les valeurs existantes d'un schéma XML. Le schéma XML peut ensuite être recompilé pour que les changements prennent effet.

La première étape de la modification d'un schéma chargé dans le SOM consiste à parcourir le schéma. Vous devriez savoir comment traverser un schéma à l'aide de l'API du SOM avant de tenter de modifier un schéma. Vous devez aussi bien connaître les propriétés de pré- et post-compilation de schéma du PSCI (Post-Schema-Compilation-Infoset).

## <a name="editing-an-xml-schema"></a>Modification d'un schéma XML

Cette section présente deux exemples de code, qui modifient tous deux le schéma utilisateur créé dans la rubrique [Création de schémas XML](building-xml-schemas.md). Le premier exemple de code ajoute un nouvel élément `PhoneNumber` à l'élément `Customer` ; le second ajoute un nouvel attribut `Title` à l'élément `FirstName`. Le premier exemple utilise aussi la collection de post-compilation de schéma <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> comme moyen de traverser le schéma utilisateur, tandis que le second utilise la collection <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma.

### <a name="phonenumber-element-example"></a>Exemple d'élément PhoneNumber

Le premier exemple de code ajoute un nouvel élément `PhoneNumber` à l'élément `Customer` du schéma utilisateur. Cet exemple de code modifie le schéma utilisateur en plusieurs étapes comme suit.

1. Il ajoute le schéma utilisateur à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis le compile. Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation du schéma sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.

2. Il extrait l'objet <xref:System.Xml.Schema.XmlSchema> compilé de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Le schéma étant compilé, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.

3. Il crée l’élément `PhoneNumber` à l’aide de la classe <xref:System.Xml.Schema.XmlSchemaElement>, la restriction de type simple `xs:string` à l’aide des classes <xref:System.Xml.Schema.XmlSchemaSimpleType> et <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>, il ajoute une facette de modèle à la propriété <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> de la restriction et ajoute la restriction à la propriété <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> du type simple et le type simple à la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> de l’élément `PhoneNumber`.

4. Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaElement> contenu dans la collection <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> de la collection <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de post-compilation de schéma.

5. Si la propriété <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> de l'élément est `"Customer"`, il obtient le type complexe de l'élément `Customer` à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaComplexType> et la particule de séquence du type complexe à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSequence>.

6. Il ajoute le nouvel élément `PhoneNumber` à la séquence contenant les éléments `FirstName` et `LastName` existants à la collection <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> de pré-compilation de schéma de la séquence.

7. Enfin, il retraite et compile l'objet <xref:System.Xml.Schema.XmlSchema> modifié à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> et <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit le résultat à la console.

Voici l'exemple de code complet.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Voici le schéma utilisateur modifié créé dans la rubrique [Création de schémas XML](building-xml-schemas.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
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

### <a name="title-attribute-example"></a>Exemple d'attribut Title

Le second exemple de code ajoute un nouvel attribut `Title` à l'élément `FirstName` du schéma utilisateur. Dans le premier exemple, le type de l'élément `FirstName` est `xs:string`. Pour que l'élément `FirstName` ait un attribut en plus de son contenu de type chaîne, le type de l'élément doit être changé en un type complexe avec un modèle de contenu d'extension de contenu simple.

Cet exemple de code modifie le schéma utilisateur en plusieurs étapes comme suit.

1. Il ajoute le schéma utilisateur à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis le compile. Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation du schéma sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.

2. Il extrait l'objet <xref:System.Xml.Schema.XmlSchema> compilé de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Le schéma étant compilé, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.

3. Il crée un type complexe pour l'élément `FirstName` en utilisant la classe <xref:System.Xml.Schema.XmlSchemaComplexType>.

4. Il crée une extension de contenu simple, avec `xs:string` comme type de base, à l'aide des classes <xref:System.Xml.Schema.XmlSchemaSimpleContent> et <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension>.

5. Il crée l'attribut `Title` à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaAttribute>, avec un <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> comme propriété `xs:string` et ajoute l'attribut à l'extension de contenu simple.

6. Il définit le modèle de contenu du contenu simple comme étant l’extension de contenu simple et celui du type complexe comme étant le contenu simple.

7. Il ajoute le nouveau type complexe à la collection de pré-compilation de schéma <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>.

8. Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaObject> contenu dans la collection <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma.

> [!NOTE]
> Puisque l'élément `FirstName` n'est pas un élément global dans le schéma, il n'est pas disponible dans les collections <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> ou <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>. L'exemple de code localise l'élément `FirstName` en localisant d'abord l'élément `Customer`.
>
> Le premier exemple de code traversait le schéma en utilisant la collection <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de post-compilation de schéma. Dans ce deuxième exemple, c’est la collection <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma qui est utilisée pour traverser le schéma. Les deux collections offrent un accès aux éléments globaux du schéma, mais une itération via la collection <xref:System.Xml.Schema.XmlSchema.Items%2A> prend plus de temps car vous devez effectuer l’itération sur tous les éléments globaux du schéma et cette collection n’a pas de propriétés PSCI. Les collections PSCI (propriétés <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, etc.) offrent un accès direct à leurs éléments, attributs et types globaux ainsi qu’à leurs propriétés PSCI.

1. Si l'objet <xref:System.Xml.Schema.XmlSchemaObject> est un élément dont la propriété <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> est `"Customer"`, il obtient le type complexe de l'élément `Customer` à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaComplexType> et la particule de séquence du type complexe à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSequence>.

2. Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaParticle> contenu dans la collection <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma.

3. Si l'objet <xref:System.Xml.Schema.XmlSchemaParticle> est un élément dont la propriété <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> est `"FirstName"`, il définit la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> de l'élément `FirstName` comme étant le nouveau type complexe `FirstName`.

4. Enfin, il retraite et compile l'objet <xref:System.Xml.Schema.XmlSchema> modifié à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> et <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit le résultat à la console.

Voici l'exemple de code complet.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Voici le schéma utilisateur modifié créé dans la rubrique [Création de schémas XML](building-xml-schemas.md).

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du Modèle Objet du schéma XML](xml-schema-object-model-overview.md)
- [Lecture et écriture de schémas XML](reading-and-writing-xml-schemas.md)
- [Création de schémas XML](building-xml-schemas.md)
- [Traversée de schémas XML](traversing-xml-schemas.md)
- [Inclusion ou importation de schémas XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md)
- [Jeu d'informations de post-compilation de schéma](post-schema-compilation-infoset.md)
