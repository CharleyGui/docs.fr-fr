---
title: Chargement de données dans un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794958"
---
# <a name="loading-data-into-a-dataset"></a>Chargement de données dans un DataSet
Un <xref:System.Data.DataSet> objet doit d’abord être rempli pour que vous puissiez l’interroger avec LINQ to DataSet. Il existe plusieurs manières de remplir le <xref:System.Data.DataSet>. Par exemple, vous pouvez utiliser [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] pour interroger la base de données et charger les <xref:System.Data.DataSet>résultats dans le. Pour plus d’informations, consultez [LINQ to SQL](./sql/linq/index.md).  
  
 Une autre manière de charger des données dans un <xref:System.Data.DataSet> consiste à utiliser la classe <xref:System.Data.Common.DataAdapter> pour extraire des données de la base de données. L'exemple suivant illustre cette opération.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise un <xref:System.Data.Common.DataAdapter> pour interroger la base de données AdventureWorks et en extraire des informations de vente à partir de l'année 2002, et charge les résultats dans un <xref:System.Data.DataSet>. Une fois <xref:System.Data.DataSet> que le a été rempli, vous pouvez y écrire des requêtes à l’aide de LINQ to DataSet. La `FillDataSet` méthode de cet exemple est utilisée dans les exemples de requêtes de [LINQ to DataSet exemples](linq-to-dataset-examples.md). Pour plus d’informations, consultez [interrogation de jeux de données](querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de LINQ to DataSet](linq-to-dataset-overview.md)
- [Interrogation de DataSets](querying-datasets-linq-to-dataset.md)
- [Exemples LINQ to DataSet](linq-to-dataset-examples.md)
