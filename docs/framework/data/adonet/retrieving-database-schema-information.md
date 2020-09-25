---
title: Extraction des informations de schéma de base de données
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: c0aaadc82771d1c2a36d797bc157d88b8d3cacdc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177356"
---
# <a name="retrieving-database-schema-information"></a>Extraction des informations de schéma de base de données

L'obtention des informations de schéma à partir d'une base de données est effectuée avec le processus de découverte de schéma. La découverte de schéma permet aux applications de demander que les fournisseurs managés recherchent et retournent des informations sur le schéma de base de données, également appelées *métadonnées*, d’une base de données donnée. Différents éléments de schéma de base de données tels que des tables, des colonnes et des procédures stockées, sont exposés à l’aide de collections de schémas. Chaque collection de schémas contient une série d'informations de schéma spécifiques au fournisseur utilisé.  
  
 Chacun des .NET Framework fournisseurs managés implémente la méthode **GetSchema** dans la classe **Connection** , et les informations de schéma retournées par la méthode **GetSchema** sont fournies sous la forme d’un <xref:System.Data.DataTable> . La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collection de schémas à retourner et restreindre la quantité d’informations retournées.  
  
 Les fournisseurs de données .NET Framework pour OLE DB, ODBC, Oracle et SqlClient fournissent une méthode **GetSchemaTable** qui retourne un DataTable décrivant les métadonnées de colonne du **DataReader**.  
  
 Le fournisseur de données .NET Framework pour OLE DB expose également des informations de schéma à l'aide de la méthode <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> de l'objet <xref:System.Data.OleDb.OleDbConnection>. En tant qu’arguments, **GetOleDbSchemaTable** prend un <xref:System.Data.OleDb.OleDbSchemaGuid> qui identifie les informations de schéma à retourner et un tableau de restrictions sur ces colonnes retournées. **GetOleDbSchemaTable** retourne un <xref:System.Data.DataTable> rempli avec les informations de schéma demandées.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Collections GetSchema et Schema](getschema-and-schema-collections.md)  
 Décrit la méthode **GetSchema** et la façon dont elle peut être utilisée pour récupérer et restreindre les informations de schéma d’une base de données.  
  
 Restrictions de schéma  
 Décrit les restrictions de schéma qui peuvent être utilisées avec **GetSchema**.  
  
 [Collections de schémas courantes](common-schema-collections.md)  
 Décrit toutes les collections de schémas communes prises en charge par tous les fournisseurs .NET Framework managés.  
  
 [Collections de schémas SQL Server](sql-server-schema-collections.md)  
 Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour SQL Server.  
  
 [Collections de schémas Oracle](oracle-schema-collections.md)  
 Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour Oracle.  
  
 [Collections de schémas ODBC](odbc-schema-collections.md)  
 Décrit les collections de schémas pour les pilotes ODBC.  
  
 [Collections de schémas OLE DB](ole-db-schema-collections.md)  
 Décrit les collections de schémas pour les fournisseurs OLE DB.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la <xref:System.Data.Common.DbConnection> classe.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la <xref:System.Data.Odbc.OdbcConnection> classe.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la <xref:System.Data.OleDb.OleDbConnection> classe.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la <xref:System.Data.OracleClient.OracleConnection> classe.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la <xref:System.Data.SqlClient.SqlConnection> classe.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la <xref:System.Data.Common.DbDataReader> classe.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la <xref:System.Data.Odbc.OdbcDataReader> classe.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la <xref:System.Data.OleDb.OleDbDataReader> classe.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la <xref:System.Data.OracleClient.OracleDataReader> classe.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la <xref:System.Data.SqlClient.SqlDataReader> classe.  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
