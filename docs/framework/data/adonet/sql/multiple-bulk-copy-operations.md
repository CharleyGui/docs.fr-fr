---
title: Plusieurs opérations de copie en bloc
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 8ee0fdbfc167c819942d8282aca56b7c5168fd87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946853"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="6d1d7-102">Plusieurs opérations de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="6d1d7-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="6d1d7-103">Vous pouvez effectuer des opérations de copie multiples en bloc à l'aide d'une seule instance d'une classe <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="6d1d7-104">Si les paramètres de l’opération changent entre les copies (par exemple, le nom de la table de destination), vous devez les mettre à jour avant tout appel ultérieur à l’une des méthodes **WriteToServer** , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="6d1d7-105">Sauf modification explicite, toutes les valeurs de propriété sont identiques à ce qu'elles étaient lors de l'opération de copie en bloc précédente pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d1d7-106">L'exécution d'opérations de copie en bloc multiples à l'aide de la même instance de <xref:System.Data.SqlClient.SqlBulkCopy> est généralement plus efficace que l'utilisation d'une instance séparée pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="6d1d7-107">Si vous effectuez plusieurs opérations de copie en bloc à l'aide du même objet <xref:System.Data.SqlClient.SqlBulkCopy>, aucune restriction ne s'applique selon que les informations source ou cible sont identiques ou différentes dans chaque opération.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="6d1d7-108">Toutefois, vous devez veiller à ce que les informations d'association de colonne soient correctement définies chaque fois que vous écrivez sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6d1d7-109">Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="6d1d7-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="6d1d7-110">Ce code est fourni pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy** uniquement.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="6d1d7-111">Si les tables sources et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.</span><span class="sxs-lookup"><span data-stu-id="6d1d7-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6d1d7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d1d7-112">See also</span></span>

- [<span data-ttu-id="6d1d7-113">Opérations de copie en bloc dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="6d1d7-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="6d1d7-114">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="6d1d7-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
