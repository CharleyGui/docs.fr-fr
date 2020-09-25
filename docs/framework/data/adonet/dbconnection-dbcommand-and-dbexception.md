---
title: DbConnection, DbCommand et DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 3075999c15fccc3a41c191297a146c362b3638e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183323"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="dca38-102">DbConnection, DbCommand et DbException</span><span class="sxs-lookup"><span data-stu-id="dca38-102">DbConnection, DbCommand and DbException</span></span>

<span data-ttu-id="dca38-103">Une fois que vous avez créé un <xref:System.Data.Common.DbProviderFactory> et un <xref:System.Data.Common.DbConnection>, vous pouvez utiliser des commandes et des lecteurs de données pour extraire des données de la source de données.</span><span class="sxs-lookup"><span data-stu-id="dca38-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="dca38-104">Exemple d'extraction de données</span><span class="sxs-lookup"><span data-stu-id="dca38-104">Retrieving Data Example</span></span>  

 <span data-ttu-id="dca38-105">Cet exemple utilise un objet `DbConnection` comme argument.</span><span class="sxs-lookup"><span data-stu-id="dca38-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="dca38-106">Un <xref:System.Data.Common.DbCommand> est créé pour sélectionner des données à partir de la table Categories en spécifiant le <xref:System.Data.Common.DbCommand.CommandText%2A> pour une instruction SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="dca38-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="dca38-107">Le code suppose que la table Categories existe au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="dca38-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="dca38-108">La connexion est ouverte et les données sont extraites à l'aide d'un <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dca38-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="dca38-109">Exemple d'exécution d'une commande</span><span class="sxs-lookup"><span data-stu-id="dca38-109">Executing a Command Example</span></span>  

 <span data-ttu-id="dca38-110">Cet exemple utilise un objet `DbConnection` comme argument.</span><span class="sxs-lookup"><span data-stu-id="dca38-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="dca38-111">Si le `DbConnection` est valide, la connexion est ouverte et un <xref:System.Data.Common.DbCommand> est créé et exécuté.</span><span class="sxs-lookup"><span data-stu-id="dca38-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="dca38-112">Le <xref:System.Data.Common.DbCommand.CommandText%2A> est spécifié pour une instruction SQL INSERT, qui effectue une insertion dans la table Categories, dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="dca38-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="dca38-113">Le code suppose que la base de données Northwind existe au niveau de la source de données et que la syntaxe SQL utilisée dans l'instruction INSERT est valide pour le fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="dca38-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="dca38-114">Les erreurs qui se produisent au niveau de la source de données sont traitées par le bloc de code <xref:System.Data.Common.DbException> et toutes les autres exceptions sont traitées dans le bloc <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="dca38-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="dca38-115">Gestion des erreurs de données avec DbException</span><span class="sxs-lookup"><span data-stu-id="dca38-115">Handling Data Errors with DbException</span></span>  

 <span data-ttu-id="dca38-116">La classe <xref:System.Data.Common.DbException> correspond à la classe de base pour toutes les exceptions levées pour le compte d'une source de données.</span><span class="sxs-lookup"><span data-stu-id="dca38-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="dca38-117">Vous pouvez l'utiliser dans votre code de gestion des exceptions pour gérer les exceptions levées par des fournisseurs différents sans avoir à référencer une classe d'exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="dca38-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="dca38-118">Le fragment de code ci-dessous montre comment utiliser <xref:System.Data.Common.DbException> pour afficher les informations relatives aux erreurs retournées par la source de données à l'aide des propriétés <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> et <xref:System.Exception.Message%2A>.</span><span class="sxs-lookup"><span data-stu-id="dca38-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="dca38-119">La sortie indiquera le type d'erreur, la source indiquant le nom du fournisseur, un code d'erreur et le message associé à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="dca38-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="dca38-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dca38-120">See also</span></span>

- [<span data-ttu-id="dca38-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="dca38-121">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="dca38-122">Obtention d'un DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="dca38-122">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="dca38-123">Modification des données avec un DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="dca38-123">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="dca38-124">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dca38-124">ADO.NET Overview</span></span>](ado-net-overview.md)
