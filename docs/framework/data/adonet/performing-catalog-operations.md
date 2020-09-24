---
title: Exécution d'opérations du catalogue
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 802762592a63a2046abcde8ed83ac67be47faf96
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161644"
---
# <a name="performing-catalog-operations"></a>Exécution d'opérations du catalogue

Pour exécuter une commande afin de modifier une base de données ou un catalogue, par exemple l’instruction CREATE TABLE ou CREATe PROCEDURE, créez un objet **Command** à l’aide des instructions SQL et d’un objet **Connection** appropriés. Exécutez la commande avec la méthode **ExecuteNonQuery** de l’objet **Command** .  
  
 L'exemple de code suivant crée une procédure stockée dans une base de données Microsoft SQL Server.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des commandes pour modifier les données](using-commands-to-modify-data.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
