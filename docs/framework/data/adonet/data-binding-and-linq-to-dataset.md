---
title: Liaison de données et LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 3203310029f463e55d7517e79f5a1f0424a0a80c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166870"
---
# <a name="data-binding-and-linq-to-dataset"></a>Liaison de données et LINQ to DataSet

La *liaison de données* est le processus qui établit une connexion entre l’interface utilisateur de l’application et la logique métier. Si la liaison est correctement paramétrée et si les données fournissent les notifications appropriées, lorsque les données changent de valeur, les éléments qui sont liés aux données reflètent automatiquement ces changements. Le <xref:System.Data.DataSet> est une représentation de données résidente en mémoire qui propose un modèle de programmation relationnel cohérent, quelle que soit la source des données qu'il contient. Le <xref:System.Data.DataView> ADO.NET 2.0 vous permet de trier et de filtrer les données stockées dans un <xref:System.Data.DataTable>. Cette fonctionnalité est souvent utilisée dans les applications de liaison de données. En utilisant un <xref:System.Data.DataView>, vous pouvez présenter les données d'une table en appliquant différents ordres de tri et filtrer les données en fonction d'un état de ligne ou d'une expression de filtre. Pour plus d’informations sur l' <xref:System.Data.DataView> objet, consultez les objets [DataView](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet permet aux développeurs de créer des requêtes complexes et puissantes sur un <xref:System.Data.DataSet> à l’aide de LINQ (Language-Integrated Query). Toutefois, une requête LINQ to DataSet retourne une énumération d' <xref:System.Data.DataRow> objets, qui n’est pas facile à utiliser dans un scénario de liaison. Pour simplifier la liaison, vous pouvez créer un <xref:System.Data.DataView> à partir d’une requête de LINQ to DataSet. Cela <xref:System.Data.DataView> utilise le filtrage et le tri spécifiés dans la requête, mais est mieux adapté à la liaison de données. LINQ to DataSet étend les fonctionnalités du <xref:System.Data.DataView> en fournissant un filtrage et un tri basés sur une expression LINQ, ce qui permet des opérations de filtrage et de tri bien plus complexes et puissantes que le filtrage et le tri basés sur une chaîne.  
  
 Notez que le <xref:System.Data.DataView> représente la requête elle-même et n'est pas une vue au-dessus de la requête. Le <xref:System.Data.DataView> est lié à un contrôle d’interface utilisateur, tel qu’un <xref:System.Windows.Forms.DataGrid> ou un <xref:System.Windows.Forms.DataGridView>, fournissant ainsi un modèle de liaison de données simple. Un <xref:System.Data.DataView> peut également être créé à partir d'un <xref:System.Data.DataTable>, fournissant ainsi une vue par défaut de cette table.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Création d’un objet DataView](creating-a-dataview-object-linq-to-dataset.md)  
 Fournit des informations sur la création d'un <xref:System.Data.DataView>.  
  
 [Filtrage avec DataView](filtering-with-dataview-linq-to-dataset.md)  
 Explique comment filtrer avec le <xref:System.Data.DataView>.  
  
 [Tri avec DataView](sorting-with-dataview-linq-to-dataset.md)  
 Explique comment trier avec le <xref:System.Data.DataView>.  
  
 [Interrogation de la collection DataRowView dans un DataView](querying-the-datarowview-collection-in-a-dataview.md)  
 Fournit des informations sur l’interrogation d’une collection <xref:System.Data.DataRowView> exposée par l’objet <xref:System.Data.DataView>.  
  
 [Performances des DataViews](dataview-performance.md)  
 Fournit des informations sur le <xref:System.Data.DataView> et les performances.  
  
 [Procédure : Lier un objet DataView à un contrôle DataGridView Windows Forms](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Explique comment lier un objet <xref:System.Data.DataView> à un <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](programming-guide-linq-to-dataset.md)
