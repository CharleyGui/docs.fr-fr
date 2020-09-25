---
title: Plusieurs opérations de copie en bloc
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: d447f09fcbfe108346b81a2bced44cf305e2844b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172669"
---
# <a name="multiple-bulk-copy-operations"></a>Plusieurs opérations de copie en bloc

Vous pouvez effectuer plusieurs opérations de copie en bloc à l’aide d’une seule instance d’une classe <xref:System.Data.SqlClient.SqlBulkCopy>. Si les paramètres de l’opération changent entre les copies (par exemple, le nom de la table de destination), vous devez les mettre à jour avant tout appel ultérieur à l’une des méthodes **WriteToServer** , comme illustré dans l’exemple suivant. Sans modification explicite, toutes les valeurs de propriété restent identiques à celles utilisées lors de la précédente opération de copie pour une instance donnée.  
  
> [!NOTE]
> L’exécution de plusieurs opérations de copie en bloc à l’aide de la même instance de <xref:System.Data.SqlClient.SqlBulkCopy> est généralement plus efficace que l’utilisation d’une instance distincte pour chaque opération.  
  
 Si vous effectuez plusieurs opérations de copie en bloc à l’aide du même objet <xref:System.Data.SqlClient.SqlBulkCopy>, aucune restriction ne s’applique selon que les informations sources ou cibles sont égales ou différentes dans chaque opération. Toutefois, vous devez vous assurer que les informations d'association de colonnes sont définies correctement chaque fois que vous écrivez sur le serveur.  
  
> [!IMPORTANT]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de copie en bloc dans SQL Server](bulk-copy-operations-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
