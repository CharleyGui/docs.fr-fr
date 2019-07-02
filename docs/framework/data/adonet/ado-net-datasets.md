---
title: Datasets ADO.NET
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: da6fb7bbe82e37787615518fa74a0d84bf95758f
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504268"
---
# <a name="adonet-datasets"></a>Datasets ADO.NET
Le <xref:System.Data.DataSet> objet est essentiel à prendre en charge déconnecté, des scénarios de données avec ADO.NET distribués. Le **DataSet** est une représentation résidente en mémoire de données qui fournit un modèle de programmation relationnel cohérent quelle que soit la source de données. Il peut être utilisé avec plusieurs sources de données différentes, utilisé avec des données XML ou utilisé pour gérer des données locales de l'application. Le **DataSet** représente un ensemble complet de données, y compris les tables associées, des contraintes et des relations entre les tables. L’illustration suivante montre le **DataSet** modèle objet.  
  
 ![Graphique ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Modèle d'objet DataSet  
  
 Les méthodes et les objets dans un **DataSet** sont cohérents avec ceux du modèle de base de données relationnelle.  
  
 Le **DataSet** peut également persister et recharger son contenu en tant que XML et son schéma en tant que schéma XML schema definition language (XSD). Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 Un élément ADO.NET **DataSet** contient une collection de zéro ou plusieurs tables représentées par <xref:System.Data.DataTable> objets. Le <xref:System.Data.DataTableCollection> contient tous les **DataTable** des objets dans un **jeu de données**.  
  
 Un **DataTable** est défini dans le <xref:System.Data> espace de noms et représente une seule table de données résidentes en mémoire. Il contient une collection de colonnes, représentées par un <xref:System.Data.DataColumnCollection> et des contraintes représentées par un <xref:System.Data.ConstraintCollection>, qui ensemble définissent le schéma de la table. Un **DataTable** contient également une collection de lignes représentées par le <xref:System.Data.DataRowCollection>, qui contient les données dans la table. En plus de son état actuel, un <xref:System.Data.DataRow> conserve ses versions d'origine et actuelle afin de permettre l'identification des modifications apportées aux valeurs stockées dans la ligne.  
  
## <a name="the-dataview-class"></a>Classe DataView  
 Un objet <xref:System.Data.DataView> vous permet de créer différentes vues des données stockées dans un objet <xref:System.Data.DataTable>, possibilité qui est souvent utilisée dans les applications de liaison de données. En utilisant un <xref:System.Data.DataView>, vous pouvez présenter les données d'une table en appliquant différents ordres de tri et filtrer les données en fonction d'un état de ligne ou d'une expression de filtre. Pour plus d’informations, consultez [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 Un **DataSet** contient des relations dans son <xref:System.Data.DataRelationCollection> objet. Une relation, représentée par le <xref:System.Data.DataRelation> associe les lignes d’un objet **DataTable** avec des lignes dans une autre **DataTable**. Une relation est similaire à une jointure qui peut exister entre les colonnes clé primaire et clé étrangère dans une base de données relationnelle. Un **DataRelation** identifie les colonnes correspondantes dans deux tables d’un **DataSet**.  
  
 Les relations permettent la navigation à partir d’une table à l’autre dans un **DataSet**. Les éléments essentiels d’un **DataRelation** sont le nom de la relation, le nom des tables mises en relation et les colonnes connexes dans chaque table. Une relation peut être générée avec plusieurs colonnes par table en spécifiant un tableau d'objets <xref:System.Data.DataColumn> en tant que colonnes clés. Lorsque vous ajoutez une relation avec la <xref:System.Data.DataRelationCollection>, vous pouvez éventuellement ajouter un **UniqueKeyConstraint** et un **ForeignKeyConstraint** pour appliquer des contraintes d’intégrité lorsque des modifications sont apportées à la colonne associée valeurs.  
  
 Pour plus d’informations, consultez [Ajout de DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Vous pouvez remplir un **DataSet** à partir d’un document ou flux XML. Vous pouvez utiliser le flux ou document XML à fournir à la **DataSet** données, informations de schéma ou les deux. Les informations fournies à partir du flux ou document XML peuvent être combinées aux données ou aux informations de schéma déjà présentes dans le **DataSet**. Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 Le **DataSet**, **DataTable**, et **DataColumn** ont toutes un **ExtendedProperties** propriété. **ExtendedProperties** est un **PropertyCollection** où vous pouvez placer des informations personnalisées, telles que l’instruction SELECT qui a été utilisée pour générer le jeu de résultats, ou l’heure à laquelle les données a été générées. Le **ExtendedProperties** collection est rendue persistante avec les informations de schéma pour le **DataSet**.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet offre des fonctionnalités d’interrogation intégrée au langage pour les données déconnectées stockées dans un jeu de données. LINQ to DataSet utilise standard [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] syntaxe et fournit la vérification de la syntaxe de la compilation, le typage statique et la prise en charge IntelliSense lorsque vous utilisez l’IDE Visual Studio.  
  
 Pour plus d’informations, [consultez LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
