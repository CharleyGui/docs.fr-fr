---
title: Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: a2b28b0dcb2e2858c7328854650667f51e83166a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185286"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet

Le langage XSD (XML Schema Definition) permet la spécification de contraintes sur les éléments et attributs qu'il définit. Lors du mappage d’un schéma XML à un schéma relationnel dans un <xref:System.Data.DataSet> , les contraintes de schéma XML sont mappées à des contraintes relationnelles appropriées sur les tables et les colonnes du **jeu de données**.  
  
 Cette section présente le mappage des contraintes de schéma XML suivantes :  
  
- Contrainte d’unicité spécifiée à l’aide de l’élément **unique** .  
  
- Contrainte de clé spécifiée à l’aide de l’élément **Key** .  
  
- Contrainte keyref spécifiée à l’aide de l’élément **keyref** .  
  
 En utilisant une contrainte sur un élément ou un attribut, vous spécifiez certaines restrictions sur les valeurs de l'élément dans toute instance du document. Par exemple, une contrainte de clé sur un élément enfant **CustomerID** d’un élément **Customer** dans le schéma indique que les valeurs de l’élément enfant **CustomerID** doivent être uniques dans toute instance de document et que les valeurs NULL ne sont pas autorisées.  
  
 Des contraintes peuvent également être spécifiées entre les éléments et les attributs figurant dans un document afin d'établir une relation dans ce document. Les contraintes key et keyref sont utilisées dans le schéma pour spécifier les contraintes au sein du document, créant ainsi une relation entre éléments et attributs du document.  
  
 Le processus de mappage convertit ces contraintes de schéma en contraintes appropriées sur les tables créées dans le **jeu de données**.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes uniques dans un **DataSet**.  
  
 [Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé (contraintes uniques où les valeurs NULL ne sont pas autorisées) dans un **DataSet**.  
  
 [Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes keyref (clé étrangère) dans un **DataSet**.  
  
## <a name="related-sections"></a>Sections connexes  

 [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d’un **DataSet** créé à partir du schéma XSD.  
  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML utilisés pour créer des relations entre des colonnes de table dans un **DataSet**.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
