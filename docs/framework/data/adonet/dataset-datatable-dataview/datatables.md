---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 369855d1aff854b60c251010ec42557b70c093c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952649"
---
# <a name="datatables"></a>DataTables
Un objet <xref:System.Data.DataSet> est constitué d’une collection de tables, de relations et de contraintes. Dans ADO.net, <xref:System.Data.DataTable> les objets sont utilisés pour représenter les tables dans un **DataSet**. Un **DataTable** représente une table de données relationnelles en mémoire; les données sont locales au. Application .net dans laquelle elle réside, mais peut être remplie à partir d’une source de données telle que Microsoft SQL Server à l’aide d’un **DataAdapter** pour plus d’informations, consultez [remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).  
  
 La classe **DataTable** est un membre de l’espace de noms **System. Data** dans la bibliothèque de classes .NET Framework. Vous pouvez créer et utiliser un **DataTable** indépendamment ou en tant que membre d’un **DataSet**, et les objets **DataTable** peuvent également être utilisés conjointement avec d’autres objets .NET Framework, <xref:System.Data.DataView>y compris le. Vous accédez à la collection de tables d’un **DataSet** via la propriété **tables** de l’objet **DataSet** .  
  
 Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes. Vous définissez le schéma d’un **DataTable** à <xref:System.Data.DataColumn> l’aide d’objets <xref:System.Data.ForeignKeyConstraint> ainsi <xref:System.Data.UniqueConstraint> que d’objets et. Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.  
  
 En plus d’un schéma, un **DataTable** doit également avoir des lignes pour contenir et trier les données. La classe <xref:System.Data.DataRow> représente les données en cours contenues dans une table. Vous utilisez la **DataRow** et ses propriétés et méthodes pour récupérer, évaluer et manipuler les données d’une table. Lorsque vous accédez et modifiez les données d’une ligne, l’objet **DataRow** conserve son état actuel et son état d’origine.  
  
 Vous pouvez créer des relations parent-enfant entre des tables à l'aide d'une ou plusieurs colonnes connexes de ces tables. Vous créez une relation entre des objets **DataTable** à <xref:System.Data.DataRelation>l’aide d’un. Les objets **DataRelation** peuvent ensuite être utilisés pour retourner les lignes enfants ou parentes associées d’une ligne particulière. Pour plus d’informations, consultez [Ajout de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Explique comment créer un **DataTable** et l’ajouter à un **DataSet**.  
  
 [Définition de schéma de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Fournit des informations sur la création et l’utilisation d’objets et de contraintes **DataColumn** .  
  
 [Manipulation des données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Explique comment ajouter, modifier et supprimer des données dans une table. Explique comment utiliser des événements **DataTable** pour examiner les modifications apportées aux données de la table.  
  
 [Gestion des événements de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Fournit des informations sur les événements disponibles pour une utilisation avec un **DataTable**, y compris les événements lorsque les valeurs de colonne sont modifiées et que les lignes sont ajoutées ou supprimées.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.  
  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Fournit des informations sur le **jeu de données** ADO.net, notamment sur la création de relations entre des tables.  
  
 <xref:System.Data.Constraint>  
 Fournit des informations de référence sur l’objet de **contrainte** .  
  
 <xref:System.Data.DataColumn>  
 Fournit des informations de référence sur l’objet **DataColumn** .  
  
 <xref:System.Data.DataSet>  
 Fournit des informations de référence sur l’objet **DataSet** .  
  
 <xref:System.Data.DataTable>  
 Fournit des informations de référence sur l’objet **DataTable** .  
  
 [Présentation des bibliothèques de classes .NET](../../../../standard/class-library-overview.md)  
 Fournit une vue d’ensemble de la bibliothèque de classes .NET Framework, y compris l’espace de noms **System** , ainsi que son espace de noms de second niveau, **System. Data**.  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
