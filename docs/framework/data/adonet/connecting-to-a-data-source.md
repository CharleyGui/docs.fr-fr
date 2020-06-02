---
title: Connexion à une source de données
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287075"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Connexion à une source de données dans ADO.NET

Dans ADO.NET, vous utilisez un objet de **connexion** pour vous connecter à une source de données spécifique en fournissant les informations d’authentification nécessaires dans une chaîne de connexion. L’objet de **connexion** que vous utilisez dépend du type de source de données.  
  
 Chaque fournisseur de données .NET Framework inclut dans le .NET Framework comprend un objet <xref:System.Data.Common.DbConnection> : le fournisseur de données .ENT Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbConnection>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlConnection>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcConnection> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Établissement de la connexion](establishing-the-connection.md)\
 Décrit comment utiliser un objet de **connexion** pour établir une connexion à une source de données.  
  
 [Événements de connexion](connection-events.md)\
 Décrit comment utiliser un événement **InfoMessage** pour extraire des messages d’information d’une source de données.  
  
## <a name="see-also"></a>Voir aussi

- [Chaînes de connexion](connection-strings.md)
- [Regroupement de connexions](connection-pooling.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Transactions et accès simultané](transactions-and-concurrency.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
