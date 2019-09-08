---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784106"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
L'espace de noms <xref:System.Data.Common> fournit des classes permettant de créer des instances <xref:System.Data.Common.DbProviderFactory> afin d'utiliser des sources de données spécifiques. Lorsque vous créez une instance <xref:System.Data.Common.DbProviderFactory> et que vous lui passez des informations sur le fournisseur de données, `DbProviderFactory` peut déterminer l'objet de connexion fortement typé correct à retourner en fonction des informations qui lui ont été fournies.  
  
 Depuis .NET Framework version 4, les fournisseurs de données tels que <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient> et <xref:System.Data.OracleClient> ne sont plus répertoriés dans le fichier machine.config, contrairement aux fournisseurs personnalisés qui continueront à y figurer.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble du modèle Factory](factory-model-overview.md)  
 Fournit une vue d'ensemble du modèle de design factory et de l'interface de programmation.  
  
 [Obtention d’un DbProviderFactory](obtaining-a-dbproviderfactory.md)  
 Montre comment répertorier les fournisseurs de données installés et créer <xref:System.Data.Common.DbConnection> à partir de `DbProviderFactory`.  
  
 [DbConnection, DbCommand et DbException](dbconnection-dbcommand-and-dbexception.md)  
 Montre comment créer <xref:System.Data.Common.DbCommand> et <xref:System.Data.Common.DbDataReader> et comment gérer des erreurs de données à l'aide de <xref:System.Data.Common.DbException>.  
  
 [Modification des données avec un DbDataAdapter](modifying-data-with-a-dbdataadapter.md)  
 Montre comment utiliser <xref:System.Data.Common.DbCommandBuilder> avec <xref:System.Data.Common.DbDataAdapter> pour récupérer et modifier des données.  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
