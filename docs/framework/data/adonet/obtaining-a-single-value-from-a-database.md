---
title: Obtention d'une valeur unique à partir d'une base de données
description: Découvrez comment retourner une seule valeur dans ADO.NET. Cet exemple de code retourne la valeur de la colonne d’identité pour un enregistrement inséré.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 9ce29bc1321814bd60cfaacd222fc55a3fbf12ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150724"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Obtention d'une valeur unique à partir d'une base de données

Vous aurez peut-être besoin de retourner des informations de base de données qui sont simplement une valeur unique plutôt qu'une table ou un flux de données. Par exemple, vous pouvez retourner le résultat d’une fonction d’agrégation telle que COUNT ( \* ), Sum (Price) ou AVG (Quantity). L’objet **Command** permet de retourner des valeurs uniques à l’aide de la méthode **ExecuteScalar** . La méthode **ExecuteScalar** retourne, sous la forme d’une valeur scalaire, la valeur de la première colonne de la première ligne du jeu de résultats.  
  
 L'exemple de code suivant insère une nouvelle valeur dans la base de données en utilisant un objet <xref:System.Data.SqlClient.SqlCommand>. La méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> est utilisée pour retourner la valeur de la colonne d'identité de l'enregistrement inséré.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Commandes et paramètres](commands-and-parameters.md)
- [Exécution d’une commande](executing-a-command.md)
- [DbConnection, DbCommand et DbException](dbconnection-dbcommand-and-dbexception.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
