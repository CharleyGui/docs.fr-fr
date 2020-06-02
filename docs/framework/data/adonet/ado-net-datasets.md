---
title: DataSets
description: En savoir plus sur le jeu de données, une représentation de données résidant en mémoire qui fournit un modèle de programmation relationnel cohérent, quelle que soit la source de données dans ADO.NET.
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 2fc5963937f7bf15dc192c6dc0a980d544a23194
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287127"
---
# <a name="adonet-datasets"></a>Datasets ADO.NET
L' <xref:System.Data.DataSet> objet est essentiel à la prise en charge des scénarios de données déconnectées et distribuées avec ADO.net. Le **DataSet** est une représentation résidente en mémoire de données qui fournit un modèle de programmation relationnel cohérent, quelle que soit la source de données. Il peut être utilisé avec plusieurs sources de données différentes, utilisé avec des données XML ou utilisé pour gérer des données locales de l'application. Le **DataSet** représente un jeu complet de données, y compris des tables associées, des contraintes et des relations entre les tables. L’illustration suivante montre le modèle d’objet **DataSet** .  
  
 ![Graphique ADO.NET](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Modèle d'objet DataSet  
  
 Les méthodes et les objets d’un **DataSet** sont cohérents avec ceux du modèle de base de données relationnelle.  
  
 Le **DataSet** peut également conserver et recharger son contenu en tant que XML et son schéma en tant que schéma en langage XSD (XML Schema Definition). Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 Un **jeu de données** ADO.net contient une collection de zéro ou plusieurs tables représentées par des <xref:System.Data.DataTable> objets. <xref:System.Data.DataTableCollection>Contient tous les objets **DataTable** d’un **DataSet**.  
  
 Un **DataTable** est défini dans l' <xref:System.Data> espace de noms et représente une seule table de données résidant en mémoire. Il contient une collection de colonnes, représentées par un <xref:System.Data.DataColumnCollection> et des contraintes représentées par un <xref:System.Data.ConstraintCollection>, qui ensemble définissent le schéma de la table. Un **DataTable** contient également une collection de lignes représentées par le <xref:System.Data.DataRowCollection> , qui contient les données de la table. En plus de son état actuel, un <xref:System.Data.DataRow> conserve ses versions d'origine et actuelle afin de permettre l'identification des modifications apportées aux valeurs stockées dans la ligne.  
  
## <a name="the-dataview-class"></a>Classe DataView  
 Un objet <xref:System.Data.DataView> vous permet de créer différentes vues des données stockées dans un objet <xref:System.Data.DataTable>, possibilité qui est souvent utilisée dans les applications de liaison de données. En utilisant un <xref:System.Data.DataView>, vous pouvez présenter les données d'une table en appliquant différents ordres de tri et filtrer les données en fonction d'un état de ligne ou d'une expression de filtre. Pour plus d’informations, consultez les [DataView](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 Un **DataSet** contient des relations dans son <xref:System.Data.DataRelationCollection> objet. Une relation, représentée par l' <xref:System.Data.DataRelation> objet, associe les lignes d’un **DataTable** aux lignes d’un autre **DataTable**. Une relation est similaire à une jointure qui peut exister entre les colonnes clé primaire et clé étrangère dans une base de données relationnelle. Un **DataRelation** identifie les colonnes correspondantes dans deux tables d’un **DataSet**.  
  
 Les relations permettent de naviguer d’une table à l’autre dans un **jeu de données**. Les éléments essentiels d’un **DataRelation** sont le nom de la relation, le nom des tables en relation et les colonnes associées dans chaque table. Une relation peut être générée avec plusieurs colonnes par table en spécifiant un tableau d'objets <xref:System.Data.DataColumn> en tant que colonnes clés. Lorsque vous ajoutez une relation au <xref:System.Data.DataRelationCollection> , vous pouvez éventuellement ajouter un **UniqueKeyConstraint** et un **ForeignKeyConstraint** pour appliquer des contraintes d’intégrité quand des modifications sont apportées à des valeurs de colonne associées.  
  
 Pour plus d’informations, consultez [Ajout de DataRelations](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Vous pouvez remplir un **DataSet** à partir d’un flux ou d’un document XML. Vous pouvez utiliser le flux ou le document XML pour fournir au **DataSet** des données, des informations de schéma ou les deux. Les informations fournies à partir du flux ou du document XML peuvent être combinées avec des données existantes ou des informations de schéma déjà présentes dans le **DataSet**. Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 Le **DataSet**, le **DataTable**et le **DataColumn** ont tous une propriété **ExtendedProperties** . **ExtendedProperties** est un **PropertyCollection** dans lequel vous pouvez placer des informations personnalisées, telles que l’instruction SELECT utilisée pour générer le jeu de résultats, ou l’heure à laquelle les données ont été générées. La collection **ExtendedProperties** est conservée avec les informations de schéma pour le **DataSet**.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet fournit des fonctionnalités de requête intégrée au langage pour les données déconnectées stockées dans un jeu de données. LINQ to DataSet utilise la syntaxe LINQ standard et fournit la vérification de la syntaxe au moment de la compilation, le typage statique et la prise en charge IntelliSense lorsque vous utilisez l’IDE de Visual Studio.  
  
 Pour plus d’informations, [consultez LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
- [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md)
- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
