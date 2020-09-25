---
title: Déduction de la structure relationnelle des DataSet à partir de XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: fca50491120346dea3e09c82324225f2114380fc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177577"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Déduction de la structure relationnelle des DataSet à partir de XML

La structure relationnelle, ou schéma, d'un objet <xref:System.Data.DataSet> est constituée de tables, de colonnes, de contraintes et de relations. Lors du chargement d'un objet <xref:System.Data.DataSet> à partir de XML, le schéma peut être prédéfini ou créé, explicitement ou par inférence, à partir du XML en cours de chargement. Pour plus d’informations sur le chargement du schéma et du contenu d’un <xref:System.Data.DataSet> objet à partir d’un fichier XML, consultez [chargement d’un DataSet à partir de XML](loading-a-dataset-from-xml.md) et [chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md).  
  
 Si le schéma d’un <xref:System.Data.DataSet> est créé à partir de XML, la méthode recommandée consiste à spécifier explicitement le schéma en utilisant le langage XSD (XML Schema Definition) (comme décrit dans dérivation de la [structure relationnelle du DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) ou XDR (XML-Data Reduced). Si aucun schéma XML ou XDR n'est disponible dans le XML, le schéma de l'objet <xref:System.Data.DataSet> peut être déduit de la structure des éléments et attributs XML.  
  
 Cette section décrit les règles d'inférence du schéma de l'objet <xref:System.Data.DataSet> en montrant les éléments et attributs XML et leur structure, ainsi que le schéma de l'objet <xref:System.Data.DataSet> obtenu par inférence.  
  
 Tous les attributs présents dans un document XML ne doivent pas être inclus dans le processus d'inférence. Les attributs qualifiés par espaces de noms peuvent inclure des métadonnées revêtant une importance pour le document XML mais pas pour le schéma de l'objet <xref:System.Data.DataSet>. En utilisant la méthode <xref:System.Data.DataSet.InferXmlSchema%2A>, vous pouvez définir des espaces de noms spécifiques qui devront être ignorés au cours du processus d'inférence. Pour plus d’informations, consultez [chargement d’informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Résumé du processus d'inférence du schéma de données](summary-of-the-dataset-schema-inference-process.md)  
 Propose un résumé succinct des règles qui permettent de déduire le schéma d'un objet <xref:System.Data.DataSet> à partir de XML.  
  
 [Déduction de tables](inferring-tables.md)  
 Décrit les éléments XML qui sont déduits en tant que tables dans un objet <xref:System.Data.DataSet>.  
  
 [Déduction des colonnes](inferring-columns.md)  
 Décrit les éléments et attributs XML qui sont déduits en tant que colonnes de table.  
  
 [Déduction des relations](inferring-relationships.md)  
 Décrit les objets <xref:System.Data.DataRelation> et <xref:System.Data.ForeignKeyConstraint> créés pour les tables imbriquées déduites.  
  
 [Déduction du texte d'un élément](inferring-element-text.md)  
 Décrit les colonnes créées pour le texte figurant dans les éléments XML et explique les cas où ce texte est ignoré.  
  
 [Limitations des inférences](inference-limitations.md)  
 Présente les limitations liées à l'inférence des schémas.  
  
## <a name="related-sections"></a>Sections connexes  

 [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)  
 Explique comment l'objet <xref:System.Data.DataSet> interagit avec des données XML.  
  
 [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d'un objet <xref:System.Data.DataSet> créée à partir d'un schéma en langage XSD (XML Schema Definition).  
  
 [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
