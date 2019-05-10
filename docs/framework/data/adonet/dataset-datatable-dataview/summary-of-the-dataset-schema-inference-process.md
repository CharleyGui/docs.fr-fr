---
title: Résumé du processus d'inférence du schéma de données
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 3c43b834f7a85f43cefd29a1ceba2260145e7d1b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607080"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Résumé du processus d'inférence du schéma de données
Le processus d'inférence identifie d'abord, à partir du document XML, les éléments qui seront déduits en tant que tables. À partir du XML restant, le processus d'inférence détermine les colonnes qui feront partie de ces tables. Pour les tables imbriquées, le processus d'inférence génère des objets <xref:System.Data.DataRelation> et <xref:System.Data.ForeignKeyConstraint> imbriqués.  
  
 Les règles d'inférence sont brièvement résumées ci-après :  
  
- Les éléments assortis d'attributs sont déduits en tant que tables.  
  
- Les éléments possédant des éléments enfants sont déduits en tant que tables.  
  
- Les éléments qui se répètent sont déduits une seule fois en tant que table.  
  
- Si l'élément de document, ou racine, ne comporte pas d'attributs ni d'éléments enfants qui seraient déduits en tant que colonnes, il est déduit en tant qu'objet <xref:System.Data.DataSet>. Sinon, l'élément de document est déduit en tant que table.  
  
- Les attributs sont déduits en tant que colonnes.  
  
- Les éléments dépourvus d'attributs ou d'éléments enfants et qui ne se répètent pas sont déduits en tant que colonnes.  
  
- Pour les éléments qui sont déduits en tant que tables imbriquées dans d’autres éléments également déduits en tant que tables, imbriquée **DataRelation** est créé entre les deux tables. Une nouvelle colonne clé primaire nommée **TableName_Id** est ajoutée aux deux tables et utilisée par le **DataRelation**. Un **ForeignKeyConstraint** est créé entre les deux tables à l’aide de la **TableName_Id** colonne.  
  
- Pour les éléments qui sont déduits en tant que tables et qui contiennent du texte mais n’ont pas d’éléments enfants, une nouvelle colonne nommée **TableName_Text** est créé pour le texte de chacun des éléments. Si un élément déduit en tant que table comprend du texte, mais également des éléments enfants, le texte est ignoré.  
  
## <a name="see-also"></a>Voir aussi

- [Inférence de la structure relationnelle d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Chargement d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
