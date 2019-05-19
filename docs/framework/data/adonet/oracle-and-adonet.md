---
title: Oracle et ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 012a5b55d052f5f06da5c152da79f4676b2bff4e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877945"
---
# <a name="oracle-and-adonet"></a>Oracle et ADO.NET
> [!NOTE]
>  Les types dans <xref:System.Data.OracleClient> sont déconseillés. Les types restent pris en charge dans la version actuelle du .NET Framework, mais seront supprimés dans une mise en production ultérieure. Microsoft recommande l'utilisation d'un fournisseur Oracle tiers.  
  
 Cette section décrit les fonctionnalités et comportements qui sont spécifiques au fournisseur de données .NET Framework pour Oracle.  
  
 Le fournisseur de données .NET Framework pour Oracle permet d’accéder à une base de données Oracle à l’aide de l’Interface OCI (Oracle Call) tel que fourni par le logiciel Client Oracle. La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour SQL Server, OLE DB et ODBC.  
  
 Pour utiliser le fournisseur de données .NET Framework pour Oracle, une application doit référencer le <xref:System.Data.OracleClient> espace de noms comme suit :  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Vous devez également inclure une référence à la DLL lorsque vous compilez votre code. Par exemple, si vous compilez un programme C#, votre ligne de commande doit inclure :  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configuration système requise](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Décrit la configuration requise pour utiliser le fournisseur de données .NET Framework pour Oracle et décrit un certain nombre de problèmes à connaître lors de son utilisation.  
  
 [BFILE Oracle](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Décrit la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour travailler avec le type de données Oracle BFILE.  
  
 [LOB Oracle](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Décrit la classe <xref:System.Data.OracleClient.OracleLob> qui est utilisée pour travailler avec les types de données Oracle LOB.  
  
 [REF CURSOR Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Décrit la prise en charge pour le type de données Oracle REF CURSOR.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Décrit les structures que vous pouvez utiliser pour travailler avec des types de données Oracle, notamment <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.  
  
 [Séquences Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Décrit la prise en charge de l'extraction des valeurs de séquence Oracle générées par le serveur.  
  
 [Mappages de types de données Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transactions distribuées Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Décrit la manière dont l’objet <xref:System.Data.OracleClient.OracleConnection> s’inscrit automatiquement dans une transaction distribuée existante s’il détermine qu’une transaction est active.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Décrit des pratiques de codage sécurisées dans ADO.NET.  
  
 [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Explique comment créer et utiliser des `DataSets`, des `DataSets` typés, des `DataTables` et des `DataViews`.  
  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Décrit comment utiliser des données dans ADO.NET.  
  
 [SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Décrit comment utiliser des fonctions et fonctionnalités spécifiques à SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Décrit des classes génériques qui vous permettent d'écrire du code indépendant du fournisseur dans ADO.NET.  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
