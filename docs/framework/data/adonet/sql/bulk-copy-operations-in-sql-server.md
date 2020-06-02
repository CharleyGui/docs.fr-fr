---
title: Opérations de copie en bloc dans SQL Server
description: Apprenez à utiliser la classe SqlBulkCopy pour écrire des solutions de code managé qui copient en bloc des fichiers volumineux dans des tables ou des vues dans des bases de données SQL Server.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286518"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Opérations de copie en bloc dans SQL Server
Microsoft SQL Server inclut un utilitaire en ligne de commande connu, **bcp**, pour rapidement copier en bloc des fichiers volumineux dans des tables ou des vues de bases de données SQL Server. La classe <xref:System.Data.SqlClient.SqlBulkCopy> vous permet d’écrire des solutions de code managé, qui fournissent des fonctionnalités similaires. Il existe d’autres façons de charger des données dans une table SQL Server (instructions INSERT, par exemple) mais <xref:System.Data.SqlClient.SqlBulkCopy> offre de meilleures performances.  
  
 La classe <xref:System.Data.SqlClient.SqlBulkCopy> peut être utilisée pour écrire des données uniquement sur les tables SQL Server. Toutefois, la source de données n'est pas limitée à SQL Server ; n'importe quelle source de données peut être utilisée, pour autant que les données puissent être chargées dans une instance de <xref:System.Data.DataTable> ou lues avec une instance de <xref:System.Data.IDataReader>.  
  
 À l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>, vous pouvez :  
  
- Une opération unique de copie en bloc  
  
- Plusieurs opérations de copie en bloc  
  
- Une opération de copie en bloc dans une transaction  
  
> [!NOTE]
> Quand vous utilisez .NET Framework version 1.1 ou antérieure (ne prenant pas en charge la classe <xref:System.Data.SqlClient.SqlBulkCopy>), vous pouvez exécuter l’instruction SQL Server Transact-SQL **BULK INSERT** à l’aide de l’objet <xref:System.Data.SqlClient.SqlCommand>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configuration de l’exemple de copie en bloc](bulk-copy-example-setup.md)  
 Décrit les tables utilisées dans les exemples de copie en bloc et fournit des scripts SQL pour créer les tables dans la base de données AdventureWorks.  
  
 [Opérations de copie en bloc uniques](single-bulk-copy-operations.md)  
 Décrit comment effectuer une seule copie en bloc de données dans une instance de SQL Server à l’aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy> et comment effectuer l’opération de copie en bloc à l’aide d’instructions Transact-SQL et de la classe <xref:System.Data.SqlClient.SqlCommand>.  
  
 [Plusieurs opérations de copie en bloc](multiple-bulk-copy-operations.md)  
 Décrit comment effectuer plusieurs opérations de copie en bloc de données dans une instance de SQL Server à l’aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 [Transaction et opérations de copie en bloc](transaction-and-bulk-copy-operations.md)  
 Décrit comment effectuer une opération de copie en bloc dans une transaction, y compris la validation ou la restauration de la transaction.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
