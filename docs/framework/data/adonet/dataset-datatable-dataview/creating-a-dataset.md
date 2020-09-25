---
title: Création d'un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: cbf652cc3742cb880fe060743dcc2615e6283ca7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202355"
---
# <a name="creating-a-dataset"></a>Création d'un DataSet

Pour créer une instance d'un objet <xref:System.Data.DataSet>, appelez le constructeur de l'objet <xref:System.Data.DataSet>. Vous pouvez également spécifier un argument de nom. Si vous ne spécifiez pas de nom pour l'objet <xref:System.Data.DataSet>, le nom est défini sur « NewDataSet ».  
  
 Vous pouvez également créer un objet <xref:System.Data.DataSet> à partir d'un objet <xref:System.Data.DataSet> existant. Le nouvel objet <xref:System.Data.DataSet> peut être : une copie exacte de l'objet <xref:System.Data.DataSet> existant ; un clône de l'objet <xref:System.Data.DataSet> qui copie la structure relationnelle ou le schéma, mais sans aucune des données de l'objet <xref:System.Data.DataSet> existant ; un sous-ensemble de l'objet <xref:System.Data.DataSet>, qui ne contient que les lignes modifiées de l'objet <xref:System.Data.DataSet> existant, à l'aide de la méthode <xref:System.Data.DataSet.GetChanges%2A>. Pour plus d’informations, consultez copie du contenu d’un [jeu de données](copying-dataset-contents.md).  
  
 L'exemple de code suivant montre comment construire une instance d'un objet <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Voir aussi

- [Remplissage d'un DataSet à partir d'un DataAdapter](../populating-a-dataset-from-a-dataadapter.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
