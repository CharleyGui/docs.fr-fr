---
title: Traversée de schémas XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: 6371d7e16af45eebf09f95bce2864be3bf44321e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824673"
---
# <a name="traversing-xml-schemas"></a>Traversée de schémas XML

Traverser un schéma XML à l'aide de l'API SOM (Schema Object Model) permet d'accéder aux éléments, attributs et types stockés dans le SOM. Traverser un schéma XML chargé dans le SOM est également la première étape de l'édition d'un schéma XML avec l'API SOM.

## <a name="traversing-an-xml-schema"></a>Traversée d'un schéma XML

Les propriétés suivantes de la classe <xref:System.Xml.Schema.XmlSchema> fournissent un accès à la collection de tous les éléments globaux ajoutés au schéma XML.

|Propriété|Type d’objet stocké dans la collection ou le tableau|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport> ou <xref:System.Xml.Schema.XmlSchemaRedefine>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|Objet <xref:System.Xml.Schema.XmlSchemaObject> (fournit un accès à tous les éléments, attributs et types de niveau global).|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|Objet <xref:System.Xml.XmlAttribute> (fournit un accès aux attributs qui n'appartiennent pas à l'espace de noms du schéma)|

> [!NOTE]
> Toutes les propriétés répertoriées dans le tableau ci-dessus, à l'exception de la propriété <xref:System.Xml.Schema.XmlSchema.Items%2A>, sont des propriétés PSCI (Post-Schema-Compilation-Infoset) qui ne sont pas disponibles tant que le schéma n'a pas été compilé. La propriété <xref:System.Xml.Schema.XmlSchema.Items%2A> est une propriété de pré-compilation de schéma qui peut être utilisée avant que le schéma ait été compilé afin d'accéder à et d'éditer tous les éléments, attributs et types de niveau global.
>
> La propriété <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> permet d'accéder à tous les attributs qui n'appartiennent pas à l'espace de noms du schéma. Ces attributs ne sont pas traités par le processeur de schéma.

L'exemple de code suivant illustre la traversée du schéma utilisateur créé dans la rubrique [Création de schémas XML](building-xml-schemas.md). Il illustre la traversée du schéma à l'aide des collections décrites ci-dessus et l'envoi à la console de tous les éléments et attributs contenus dans le schéma.

Cet exemple de code traverse le schéma utilisateur en plusieurs étapes comme suit.

1. Il ajoute le schéma utilisateur à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis le compile. Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation du schéma sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.

2. Il extrait l'objet <xref:System.Xml.Schema.XmlSchema> compilé de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Le schéma étant compilé, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.

3. Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaElement> figurant dans la collection <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> de la collection de post-compilation de schéma <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> et écrit le nom de chaque élément à la console.

4. Il obtient le type complexe de l'élément `Customer` en utilisant la classe <xref:System.Xml.Schema.XmlSchemaComplexType>.

5. Si le type complexe possède des attributs, il obtient un objet <xref:System.Collections.IDictionaryEnumerator> à énumérer sur chaque objet <xref:System.Xml.Schema.XmlSchemaAttribute> et en écrit le nom à la console.

6. Il obtient la particule de séquence du type complexe en utilisant la classe <xref:System.Xml.Schema.XmlSchemaSequence>.

7. Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaElement> figurant dans la collection <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> et écrit le nom de chaque élément enfant à la console.

Voici l'exemple de code complet.

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

La propriété <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> peut être l'objet <xref:System.Xml.Schema.XmlSchemaSimpleType> ou <xref:System.Xml.Schema.XmlSchemaComplexType> si c'est un type complexe ou un type simple défini par l'utilisateur. Elle peut aussi être l'objet <xref:System.Xml.Schema.XmlSchemaDatatype> si c'est un des types de données intégrés définis dans la recommandation du W3C sur le schéma XML. Dans le schéma utilisateur, la propriété <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> de l'élément `Customer` est l'objet <xref:System.Xml.Schema.XmlSchemaComplexType> et les éléments `FirstName` et `LastName` sont des objets <xref:System.Xml.Schema.XmlSchemaSimpleType>.

L'exemple de code de la rubrique [Création de schémas XML](building-xml-schemas.md) utilisait la collection <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> pour ajouter l'attribut `CustomerId` à l'élément `Customer`. C'est une propriété de pré-compilation de schéma. La propriété PSCI correspondante est la collection <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType>, qui contient tous les attributs du type complexe, y compris ceux qui sont hérités par dérivation de type.

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du Modèle Objet du schéma XML](xml-schema-object-model-overview.md)
- [Lecture et écriture de schémas XML](reading-and-writing-xml-schemas.md)
- [Création de schémas XML](building-xml-schemas.md)
- [Modification de schémas XML](editing-xml-schemas.md)
- [Inclusion ou importation de schémas XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md)
- [Jeu d'informations de post-compilation de schéma](post-schema-compilation-infoset.md)
