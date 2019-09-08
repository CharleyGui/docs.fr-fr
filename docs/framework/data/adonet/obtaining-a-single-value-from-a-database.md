---
title: Obtention d'une valeur unique à partir d'une base de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794751"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="31f7c-102">Obtention d'une valeur unique à partir d'une base de données</span><span class="sxs-lookup"><span data-stu-id="31f7c-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="31f7c-103">Vous aurez peut-être besoin de retourner des informations de base de données qui sont simplement une valeur unique plutôt qu'une table ou un flux de données.</span><span class="sxs-lookup"><span data-stu-id="31f7c-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="31f7c-104">Par exemple, vous pouvez retourner le résultat d’une fonction d’agrégation telle que Count (\*), Sum (Price) ou AVG (Quantity).</span><span class="sxs-lookup"><span data-stu-id="31f7c-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="31f7c-105">L’objet **Command** permet de retourner des valeurs uniques à l’aide de la méthode **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="31f7c-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="31f7c-106">La méthode **ExecuteScalar** retourne, sous la forme d’une valeur scalaire, la valeur de la première colonne de la première ligne du jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="31f7c-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="31f7c-107">L'exemple de code suivant insère une nouvelle valeur dans la base de données en utilisant un objet <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="31f7c-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="31f7c-108">La méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> est utilisée pour retourner la valeur de la colonne d'identité de l'enregistrement inséré.</span><span class="sxs-lookup"><span data-stu-id="31f7c-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="31f7c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31f7c-109">See also</span></span>

- [<span data-ttu-id="31f7c-110">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="31f7c-110">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="31f7c-111">Exécution d’une commande</span><span class="sxs-lookup"><span data-stu-id="31f7c-111">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="31f7c-112">DbConnection, DbCommand et DbException</span><span class="sxs-lookup"><span data-stu-id="31f7c-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="31f7c-113">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="31f7c-113">ADO.NET Overview</span></span>](ado-net-overview.md)
