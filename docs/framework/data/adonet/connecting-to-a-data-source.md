---
title: Connexion à une source de données dans ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786763"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Connexion à une source de données dans ADO.NET
Dans ADO.NET, vous utilisez un objet de **connexion** pour vous connecter à une source de données spécifique en fournissant les informations d’authentification nécessaires dans une chaîne de connexion. L’objet de **connexion** que vous utilisez dépend du type de source de données.  
  
 Chaque fournisseur de données .NET Framework inclut dans le .NET Framework comprend un objet <xref:System.Data.Common.DbConnection> : le fournisseur de données .ENT Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbConnection>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlConnection>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcConnection> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Établissement de la connexion](establishing-the-connection.md)  
 Décrit comment utiliser un objet de **connexion** pour établir une connexion à une source de données.  
  
 [Événements de connexion](connection-events.md)  
 Décrit comment utiliser un événement **InfoMessage** pour extraire des messages d’information d’une source de données.  
  
## <a name="see-also"></a>Voir aussi

- [Chaînes de connexion](connection-strings.md)
- [Regroupement de connexions](connection-pooling.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Transactions et accès concurrentiel](transactions-and-concurrency.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
