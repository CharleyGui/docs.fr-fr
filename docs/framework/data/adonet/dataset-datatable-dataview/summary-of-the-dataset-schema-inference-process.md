---
title: Résumé du processus d'inférence du schéma de données
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 8d517487b96aa7f204ea9f25d326500db7df413a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198507"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Résumé du processus d'inférence du schéma de données

Le processus d'inférence identifie d'abord, à partir du document XML, les éléments qui seront déduits en tant que tables. À partir du XML restant, le processus d'inférence détermine les colonnes qui feront partie de ces tables. Pour les tables imbriquées, le processus d'inférence génère des objets <xref:System.Data.DataRelation> et <xref:System.Data.ForeignKeyConstraint> imbriqués.  
  
 Voici un bref résumé des règles d’inférence :  
  
- Les éléments assortis d'attributs sont déduits en tant que tables.  
  
- Les éléments possédant des éléments enfants sont déduits en tant que tables.  
  
- Les éléments qui se répètent sont déduits une seule fois en tant que table.  
  
- Si l'élément de document, ou racine, ne comporte pas d'attributs ni d'éléments enfants qui seraient déduits en tant que colonnes, il est déduit en tant qu'objet <xref:System.Data.DataSet>. Sinon, l'élément de document est déduit en tant que table.  
  
- Les attributs sont déduits en tant que colonnes.  
  
- Les éléments dépourvus d'attributs ou d'éléments enfants et qui ne se répètent pas sont déduits en tant que colonnes.  
  
- Pour les éléments qui sont déduits en tant que tables imbriquées dans d’autres éléments également déduits en tant que tables, un **DataRelation** imbriqué est créé entre les deux tables. Une nouvelle colonne de clé primaire nommée **TableName_Id** est ajoutée aux deux tables et utilisée par le **DataRelation**. Un **ForeignKeyConstraint** est créé entre les deux tables à l’aide de la **TableName_Id** colonne.  
  
- Pour les éléments qui sont déduits en tant que tables et qui contiennent du texte mais n’ont pas d’éléments enfants, une nouvelle colonne nommée **TableName_Text** est créée pour le texte de chacun des éléments. Si un élément déduit en tant que table comprend du texte, mais également des éléments enfants, le texte est ignoré.  
  
## <a name="see-also"></a>Voir aussi

- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
