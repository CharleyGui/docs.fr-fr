---
title: Modification des données avec les procédures stockées
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 65116a48533fd6ce86894c6a4522929285f8e1f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150750"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="9ecb9-102">Modification des données avec les procédures stockées</span><span class="sxs-lookup"><span data-stu-id="9ecb9-102">Modifying Data with Stored Procedures</span></span>

<span data-ttu-id="9ecb9-103">Les procédures stockées peuvent accepter des données en tant que paramètres d'entrée et retourner des données en tant que paramètres de sortie, jeux de résultats et valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="9ecb9-104">L'exemple ci-dessous montre comment ADO.NET envoie et reçoit des paramètres d'entrée, des paramètres de sortie et des valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="9ecb9-105">L'exemple insère un nouvel enregistrement dans une table où la colonne de clé primaire est une colonne d'identité dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecb9-106">Si vous utilisez des procédures stockées SQL Server pour modifier ou supprimer des données à l'aide de <xref:System.Data.SqlClient.SqlDataAdapter>, assurez-vous que vous n'utilisez pas SET NOCOUNT ON dans la définition de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="9ecb9-107">En effet, le nombre de lignes affectées retourné serait alors la valeur zéro, ce que `DataAdapter` interprète comme un conflit d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="9ecb9-108">Dans ce cas, l'exception <xref:System.Data.DBConcurrencyException> est levée.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ecb9-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ecb9-109">Example</span></span>  

 <span data-ttu-id="9ecb9-110">L’exemple utilise la procédure stockée suivante pour insérer une nouvelle catégorie dans la table des **catégories** **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="9ecb9-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="9ecb9-111">La procédure stockée prend la valeur dans la colonne **CategoryName** comme paramètre d’entrée et utilise la fonction SCOPE_IDENTITY () pour récupérer la nouvelle valeur du champ Identity, **CategoryID**, et la renvoyer dans un paramètre OUTPUT.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="9ecb9-112">L’instruction return utilise la @ROWCOUNT fonction @ pour retourner le nombre de lignes insérées.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="9ecb9-113">L'exemple de code suivant utilise la procédure stockée `InsertCategory` présentée ci-dessus comme source pour <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> de <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="9ecb9-114">Le paramètre de sortie `@Identity` se reflète dans <xref:System.Data.DataSet> après que l'enregistrement a été inséré dans la base de données lors de l'appel de la méthode `Update` de <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="9ecb9-115">Le code récupère également la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecb9-116">Lorsque vous utilisez <xref:System.Data.OleDb.OleDbDataAdapter> , vous devez spécifier des paramètres avec un <xref:System.Data.ParameterDirection> de **returnValue** avant les autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="9ecb9-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9ecb9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ecb9-117">See also</span></span>

- [<span data-ttu-id="9ecb9-118">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9ecb9-118">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="9ecb9-119">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="9ecb9-119">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="9ecb9-120">Exécution d’une commande</span><span class="sxs-lookup"><span data-stu-id="9ecb9-120">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="9ecb9-121">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9ecb9-121">ADO.NET Overview</span></span>](ado-net-overview.md)
