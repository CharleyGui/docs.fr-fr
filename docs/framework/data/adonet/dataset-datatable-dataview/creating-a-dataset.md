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
# <a name="creating-a-dataset"></a><span data-ttu-id="a53d0-102">Création d'un DataSet</span><span class="sxs-lookup"><span data-stu-id="a53d0-102">Creating a DataSet</span></span>

<span data-ttu-id="a53d0-103">Pour créer une instance d'un objet <xref:System.Data.DataSet>, appelez le constructeur de l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="a53d0-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="a53d0-104">Vous pouvez également spécifier un argument de nom.</span><span class="sxs-lookup"><span data-stu-id="a53d0-104">Optionally specify a name argument.</span></span> <span data-ttu-id="a53d0-105">Si vous ne spécifiez pas de nom pour l'objet <xref:System.Data.DataSet>, le nom est défini sur « NewDataSet ».</span><span class="sxs-lookup"><span data-stu-id="a53d0-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="a53d0-106">Vous pouvez également créer un objet <xref:System.Data.DataSet> à partir d'un objet <xref:System.Data.DataSet> existant.</span><span class="sxs-lookup"><span data-stu-id="a53d0-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="a53d0-107">Le nouvel objet <xref:System.Data.DataSet> peut être : une copie exacte de l'objet <xref:System.Data.DataSet> existant ; un clône de l'objet <xref:System.Data.DataSet> qui copie la structure relationnelle ou le schéma, mais sans aucune des données de l'objet <xref:System.Data.DataSet> existant ; un sous-ensemble de l'objet <xref:System.Data.DataSet>, qui ne contient que les lignes modifiées de l'objet <xref:System.Data.DataSet> existant, à l'aide de la méthode <xref:System.Data.DataSet.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="a53d0-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="a53d0-108">Pour plus d’informations, consultez copie du contenu d’un [jeu de données](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="a53d0-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="a53d0-109">L'exemple de code suivant montre comment construire une instance d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="a53d0-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="a53d0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a53d0-110">See also</span></span>

- [<span data-ttu-id="a53d0-111">Remplissage d'un DataSet à partir d'un DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a53d0-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="a53d0-112">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a53d0-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a53d0-113">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a53d0-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
