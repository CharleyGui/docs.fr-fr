---
title: Oracle et ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 5683f2b4ba57021ff6dda3a51baca016f886b605
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980078"
---
# <a name="oracle-and-adonet"></a>Oracle et ADO.NET
> [!NOTE]
> Les types dans <xref:System.Data.OracleClient> sont déconseillés. Les types restent pris en charge dans la version actuelle du .NET Framework, mais seront supprimés dans une mise en production ultérieure. Microsoft recommande l'utilisation d'un fournisseur Oracle tiers.  
  
 Cette section décrit les fonctionnalités et les comportements spécifiques aux Fournisseur de données .NET Framework pour Oracle.  
  
 La .NET Framework Fournisseur de données pour Oracle permet d’accéder à une base de données Oracle à l’aide de l’interface OCI (Oracle Call Interface) fournie par le logiciel client Oracle. La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour SQL Server, OLE DB et ODBC.  
  
 Pour utiliser le Fournisseur de données .NET Framework pour Oracle, une application doit référencer l’espace de noms <xref:System.Data.OracleClient> comme suit :  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Vous devez également inclure une référence à la DLL lorsque vous compilez votre code. Par exemple, si vous compilez un programme C#, votre ligne de commande doit inclure :  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configuration système requise](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Décrit la configuration requise pour l’utilisation du Fournisseur de données .NET Framework pour Oracle et décrit un certain nombre de problèmes à prendre en compte lors de son utilisation.  
  
 [BFILE Oracle](oracle-bfiles.md)  
 Décrit la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour travailler avec le type de données Oracle BFILE.  
  
 [LOB Oracle](oracle-lobs.md)  
 Décrit la classe <xref:System.Data.OracleClient.OracleLob> qui est utilisée pour travailler avec les types de données Oracle LOB.  
  
 [REF CURSOR Oracle](oracle-ref-cursors.md)  
 Décrit la prise en charge pour le type de données Oracle REF CURSOR.  
  
 [OracleTypes](oracletypes.md)  
 Décrit les structures que vous pouvez utiliser pour travailler avec des types de données Oracle, notamment <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.  
  
 [Séquences Oracle](oracle-sequences.md)  
 Décrit la prise en charge de l'extraction des valeurs de séquence Oracle générées par le serveur.  
  
 [Mappages de types de données Oracle](oracle-data-type-mappings.md)  
 Répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transactions distribuées Oracle](oracle-distributed-transactions.md)  
 Décrit la manière dont l’objet <xref:System.Data.OracleClient.OracleConnection> s’inscrit automatiquement dans une transaction distribuée existante s’il détermine qu’une transaction est active.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)  
 Décrit des pratiques de codage sécurisées dans ADO.NET.  
  
 [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md)  
 Explique comment créer et utiliser des `DataSets`, des `DataSets` typés, des `DataTables` et des `DataViews`.  
  
 [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)  
 Décrit comment utiliser des données dans ADO.NET.  
  
 [SQL Server et ADO.NET](./sql/index.md)  
 Décrit comment utiliser des fonctions et fonctionnalités spécifiques à SQL Server.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Décrit des classes génériques qui vous permettent d'écrire du code indépendant du fournisseur dans ADO.NET.  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
