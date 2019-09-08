---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785343"
---
# <a name="datatablereaders"></a><span data-ttu-id="40b21-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="40b21-102">DataTableReaders</span></span>
<span data-ttu-id="40b21-103">L'objet <xref:System.Data.DataTableReader> présente le contenu d'un objet <xref:System.Data.DataTable> ou d'un objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="40b21-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="40b21-104">Quand vous créez un **DataTableReader** à partir d’un **DataTable**, l’objet **DataTableReader** résultant contient un jeu de résultats avec les mêmes données que le **DataTable** à partir duquel il a été créé, à l’exception des lignes qui ont été marquées comme supprimé.</span><span class="sxs-lookup"><span data-stu-id="40b21-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="40b21-105">Les colonnes apparaissent dans le même ordre que dans le **DataTable**d’origine.</span><span class="sxs-lookup"><span data-stu-id="40b21-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="40b21-106">Un **DataTableReader** peut contenir plusieurs jeux de résultats s’il a été créé <xref:System.Data.DataSet.CreateDataReader%2A>en appelant.</span><span class="sxs-lookup"><span data-stu-id="40b21-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="40b21-107">Les résultats sont dans le même ordre que les **DataTables** dans la collection de <xref:System.Data.DataSet.Tables%2A> l’objet DataSet.</span><span class="sxs-lookup"><span data-stu-id="40b21-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40b21-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="40b21-108">In This Section</span></span>  
 [<span data-ttu-id="40b21-109">Création d’un DataReader</span><span class="sxs-lookup"><span data-stu-id="40b21-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="40b21-110">Explique comment créer un objet **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="40b21-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="40b21-111">Navigation dans les DataTables</span><span class="sxs-lookup"><span data-stu-id="40b21-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="40b21-112">Décrit l’utilisation de la méthode **Read** pour parcourir le contenu d’un **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="40b21-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b21-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40b21-113">See also</span></span>

- [<span data-ttu-id="40b21-114">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="40b21-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="40b21-115">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="40b21-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
