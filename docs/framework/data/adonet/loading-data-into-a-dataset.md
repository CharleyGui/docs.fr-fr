---
title: Chargement de données dans un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 26b77269b21e1b365f81746ba2df66d7df91677e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504316"
---
# <a name="loading-data-into-a-dataset"></a>Chargement de données dans un DataSet
Un <xref:System.Data.DataSet> objet doit être rempli avant que vous puissiez l’interroger avec LINQ to DataSet. Il existe plusieurs manières de remplir le <xref:System.Data.DataSet>. Par exemple, vous pouvez utiliser [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] pour interroger la base de données et de charger les résultats dans le <xref:System.Data.DataSet>. Pour plus d’informations, consultez [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Une autre manière de charger des données dans un <xref:System.Data.DataSet> consiste à utiliser la classe <xref:System.Data.Common.DataAdapter> pour extraire des données de la base de données. L'exemple suivant illustre cette opération.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise un <xref:System.Data.Common.DataAdapter> pour interroger la base de données AdventureWorks et en extraire des informations de vente à partir de l'année 2002, et charge les résultats dans un <xref:System.Data.DataSet>. Après le <xref:System.Data.DataSet> a été rempli, vous pouvez écrire des requêtes à l’aide de LINQ to DataSet. Le `FillDataSet` méthode dans cet exemple est utilisée dans les exemples de requêtes de [exemples LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Pour plus d’informations, consultez [interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Exemples LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
