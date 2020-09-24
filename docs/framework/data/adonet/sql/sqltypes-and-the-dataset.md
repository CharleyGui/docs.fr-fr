---
title: SqlTypes et le DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 04f95cd7d3f6e52f644f23dd8a32c77d56a5ddda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147506"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes et le DataSet

ADO.NET 2.0 inclut une prise en charge améliorée de type pour le `DataSet` via l’espace de noms <xref:System.Data.SqlTypes>. Les types dans <xref:System.Data.SqlTypes> sont conçus pour fournir des types de données avec les mêmes sémantique et précision que les types de données dans une base de données SQL Server. Chaque type de données dans <xref:System.Data.SqlTypes> a un type de données équivalent dans SQL Server, avec la même représentation de données sous-jacentes.  
  
 L’utilisation de <xref:System.Data.SqlTypes> directement dans un <xref:System.Data.DataSet> confère plusieurs avantages lors de l’utilisation de types de données SQL Server. <xref:System.Data.SqlTypes> prend en charge la même sémantique que les types de données natifs SQL Server. La spécification de l’un des <xref:System.Data.SqlTypes> dans la définition d’une <xref:System.Data.DataColumn> élimine la perte de précision qui peut se produire lors de la conversion de types de données décimales ou numériques en l’un des types de données Common Language Runtime (CLR).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant crée un objet <xref:System.Data.DataTable>, définissant de façon explicite les types de données <xref:System.Data.DataColumn> en utilisant <xref:System.Data.SqlTypes> au lieu de types CLR. Le code remplit l’objet <xref:System.Data.DataTable> de données de la table Sales.SalesOrderDetail dans la base de données AdventureWorks dans SQL Server. La sortie affichée dans la fenêtre de console affiche le type de données de chaque colonne et les valeurs récupérées à partir de SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Mappages de types de données SQL Server](../sql-server-data-type-mappings.md)
- [Configuration des paramètres et des types de données des paramètres](../configuring-parameters-and-parameter-data-types.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
