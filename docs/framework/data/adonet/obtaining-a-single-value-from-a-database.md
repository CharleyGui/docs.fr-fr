---
title: Obtention d'une valeur unique à partir d'une base de données
description: Découvrez comment retourner une seule valeur dans ADO.NET. Cet exemple de code retourne la valeur de la colonne d’identité pour un enregistrement inséré.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286700"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="e8b06-104">Obtention d'une valeur unique à partir d'une base de données</span><span class="sxs-lookup"><span data-stu-id="e8b06-104">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="e8b06-105">Vous aurez peut-être besoin de retourner des informations de base de données qui sont simplement une valeur unique plutôt qu'une table ou un flux de données.</span><span class="sxs-lookup"><span data-stu-id="e8b06-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="e8b06-106">Par exemple, vous pouvez retourner le résultat d’une fonction d’agrégation telle que COUNT ( \* ), Sum (Price) ou AVG (Quantity).</span><span class="sxs-lookup"><span data-stu-id="e8b06-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="e8b06-107">L’objet **Command** permet de retourner des valeurs uniques à l’aide de la méthode **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="e8b06-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="e8b06-108">La méthode **ExecuteScalar** retourne, sous la forme d’une valeur scalaire, la valeur de la première colonne de la première ligne du jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="e8b06-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="e8b06-109">L'exemple de code suivant insère une nouvelle valeur dans la base de données en utilisant un objet <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="e8b06-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="e8b06-110">La méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> est utilisée pour retourner la valeur de la colonne d'identité de l'enregistrement inséré.</span><span class="sxs-lookup"><span data-stu-id="e8b06-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8b06-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8b06-111">See also</span></span>

- [<span data-ttu-id="e8b06-112">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="e8b06-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="e8b06-113">Exécution d'une commande</span><span class="sxs-lookup"><span data-stu-id="e8b06-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="e8b06-114">DbConnection, DbCommand et DbException</span><span class="sxs-lookup"><span data-stu-id="e8b06-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="e8b06-115">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e8b06-115">ADO.NET Overview</span></span>](ado-net-overview.md)
