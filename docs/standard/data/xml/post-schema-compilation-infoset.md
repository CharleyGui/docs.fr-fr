---
title: Jeu d'informations de post-compilation de schéma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
ms.openlocfilehash: 2b91a74f7dbb31ee47535dbed7cf5fa5243e364c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820438"
---
# <a name="post-schema-compilation-infoset"></a>Jeu d'informations de post-compilation de schéma
La [recommandation du World Wide Web Consortium (W3C) sur le schéma XML](https://www.w3.org/XML/Schema) décrit le jeu d'informations qui doit être exposé pour la pré-validation de schéma et la post-compilation de schéma. Le Modèle Objet du schéma (SOM) XML observe cette exposition avant et après l'appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Le jeu d'informations de pré-validation de schéma est généré pendant la modification du schéma. Le jeu d'informations de post-compilation de schéma est généré après l'appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>, lors de la compilation du schéma et est exposé comme des propriétés.  
  
 Le SOM est le modèle d’objet qui représente les jeux d’informations de pré-validation de schéma et de post-compilation de schéma. Il est composé de classes dans l’espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>. Toutes les propriétés de lecture et d'écriture des classes de l'espace de noms <xref:System.Xml.Schema> appartiennent au jeu d'informations de pré-validation de schéma, alors que toutes les propriétés en lecture seule des classes de l'espace de noms <xref:System.Xml.Schema> appartiennent au jeu d'informations de post-compilation de schéma. Les propriétés suivantes, qui sont des propriétés des jeux d’informations de pré-validation de schéma et de post-compilation de schéma, constituent une exception à la règle.  
  
|Classe|Propriété|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Par exemple, les classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaComplexType> ont des propriétés `BlockResolved` et `FinalResolved`. Ces propriétés permettent de contenir les valeurs des propriétés `Block` et `Final` après validation et compilation du schéma. `BlockResolved` et `FinalResolved` sont des propriétés en lecture seule qui font partie du jeu d'informations de post-compilation de schéma.  
  
 L'exemple suivant montre la propriété <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> de la classe <xref:System.Xml.Schema.XmlSchemaElement> définie après la validation du schéma. Avant la validation, la propriété contient une référence `null` et la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> est définie sur le nom du type en question. Après la validation, la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> est résolue en un type valide et l’objet de type est disponible par l’intermédiaire de la propriété <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A>.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle Objet du schéma (SOM) XML](xml-schema-object-model-som.md)
