---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203819"
---
# <a name="datatablereaders"></a><span data-ttu-id="789f7-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="789f7-102">DataTableReaders</span></span>
<span data-ttu-id="789f7-103">L'objet <xref:System.Data.DataTableReader> présente le contenu d'un objet <xref:System.Data.DataTable> ou d'un objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="789f7-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="789f7-104">Quand vous créez un **DataTableReader** à partir d’un **DataTable**, l’objet **DataTableReader** résultant contient un jeu de résultats avec les mêmes données que le **DataTable** à partir duquel il a été créé, à l’exception des lignes qui ont été marquées comme supprimé.</span><span class="sxs-lookup"><span data-stu-id="789f7-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="789f7-105">Les colonnes apparaissent dans le même ordre que dans le **DataTable**d’origine.</span><span class="sxs-lookup"><span data-stu-id="789f7-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="789f7-106">Un **DataTableReader** peut contenir plusieurs jeux de résultats s’il a été créé <xref:System.Data.DataSet.CreateDataReader%2A>en appelant.</span><span class="sxs-lookup"><span data-stu-id="789f7-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="789f7-107">Les résultats sont dans le même ordre que les **DataTables** dans la collection de <xref:System.Data.DataSet.Tables%2A> l’objet DataSet.</span><span class="sxs-lookup"><span data-stu-id="789f7-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="789f7-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="789f7-108">In This Section</span></span>  
 [<span data-ttu-id="789f7-109">Création d’un DataReader</span><span class="sxs-lookup"><span data-stu-id="789f7-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="789f7-110">Explique comment créer un objet **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="789f7-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="789f7-111">Navigation dans les DataTables</span><span class="sxs-lookup"><span data-stu-id="789f7-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="789f7-112">Décrit l’utilisation de la méthode **Read** pour parcourir le contenu d’un **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="789f7-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789f7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="789f7-113">See also</span></span>

- [<span data-ttu-id="789f7-114">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="789f7-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="789f7-115">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="789f7-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
