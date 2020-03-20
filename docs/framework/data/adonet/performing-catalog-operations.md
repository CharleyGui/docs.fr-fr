---
title: Exécution d'opérations du catalogue
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: bedeb4e9c510a3feeedc038e9c4cef6c4721e345
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149243"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="64252-102">Exécution d'opérations du catalogue</span><span class="sxs-lookup"><span data-stu-id="64252-102">Performing Catalog Operations</span></span>
<span data-ttu-id="64252-103">Pour exécuter une commande pour modifier une base de données ou un catalogue, comme la TABLE CREATE ou la déclaration CREATE PROCEDURE, créez un objet **de commande** à l’aide des instructions SQL appropriées et **d’un** objet de connexion.</span><span class="sxs-lookup"><span data-stu-id="64252-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="64252-104">Exécutez la commande avec la méthode **ExecuteNonQuery** de l’objet **de commande.**</span><span class="sxs-lookup"><span data-stu-id="64252-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="64252-105">L'exemple de code suivant crée une procédure stockée dans une base de données Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="64252-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="64252-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64252-106">See also</span></span>

- [<span data-ttu-id="64252-107">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="64252-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="64252-108">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="64252-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="64252-109">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="64252-109">ADO.NET Overview</span></span>](ado-net-overview.md)
