---
title: Transaction et opérations de copie en bloc
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: 27fafc0ef45b80eddd993229f52d119b40b4956f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155431"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transaction et opérations de copie en bloc

Les opérations de copie en bloc peuvent être effectuées comme des opérations isolées ou dans le cadre d'une transaction à plusieurs étapes. Cette dernière option permet d'effectuer plusieurs opérations de copie en bloc dans la même transaction ainsi que d'autres opérations de base de données (telles que des insertions, mises à jour et suppressions), tout en étant en mesure de valider ou restaurer toute la transaction.  
  
 Par défaut, une opération de copie en bloc est effectuée comme une opération isolée. L'opération de copie en bloc se produit de façon non transactionnelle, sans possibilité de restauration. Si vous devez restaurer tout ou partie de la copie en bloc en cas d’erreur, vous pouvez utiliser une <xref:System.Data.SqlClient.SqlBulkCopy> transaction managée, effectuer l’opération de copie en bloc dans une transaction existante ou être inscrite dans un **System. transactions** <xref:System.Transactions.Transaction> .  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Exécution d'une opération de copie en bloc non traitée  

 L’application console suivante montre ce qui se passe quand une opération de copie en bloc non transactionnelle rencontre une erreur au cours de l’opération.  
  
 Dans l’exemple, la table source et la table de destination incluent une colonne `Identity` nommée **ProductID**. Le code commence par préparer la table de destination en supprimant toutes les lignes, puis en insérant une ligne dont la colonne **ProductID** existe dans la table source. Par défaut, une nouvelle valeur pour la colonne `Identity` est générée dans la table de destination pour chaque ligne ajoutée. Dans cet exemple, quand la connexion est ouverte, une option est définie qui oblige le processus de chargement en bloc à utiliser à la place les valeurs `Identity` de la table source.  
  
 L’opération de copie en bloc est exécutée avec la propriété <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> définie avec la valeur 10. Quand l'opération rencontre la ligne non valide, une exception est levée. Dans ce premier exemple, l'opération de copie en bloc est non transactionnel. Tous les lots copiés avant l'erreur sont validés. Le lot contenant la clé dupliquée est restauré et l'opération de copie en bloc est interrompue avant le traitement des autres lots.  
  
> [!NOTE]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Exécution d’une opération de copie en bloc dédiée dans une transaction  

 Par défaut, une opération de copie en bloc est sa propre transaction. Si vous voulez effectuer une opération de copie en bloc dédiée, créez une instance de <xref:System.Data.SqlClient.SqlBulkCopy> avec une chaîne de connexion, ou utilisez un objet <xref:System.Data.SqlClient.SqlConnection> existant sans transaction active. Dans chaque scénario, l’opération de copie en bloc crée, puis valide ou restaure la transaction.  
  
 Vous pouvez spécifier explicitement l’option <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> dans le constructeur de classe <xref:System.Data.SqlClient.SqlBulkCopy> pour qu’une opération de copie en bloc s’exécute dans sa propre transaction, chaque lot de l’opération de copie en bloc s’exécutant alors dans une transaction distincte.  
  
> [!NOTE]
> Puisque des lots différents sont exécutés dans différentes transactions, si une erreur se produit pendant l'opération de copie en bloc, toutes les lignes du lot actuel sont restaurées, mais les lignes des lots précédents restent dans la base de données.  
  
 L’application console suivante est similaire à l’exemple précédent, à une exception près : dans cet exemple, l’opération de copie en bloc gère ses propres transactions. Tous les lots copiés avant l'erreur sont validés. Le lot contenant la clé dupliquée est restauré et l'opération de copie en bloc est interrompue avant le traitement des autres lots.  
  
> [!IMPORTANT]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Utilisation de transactions existantes  

 Vous pouvez spécifier un objet <xref:System.Data.SqlClient.SqlTransaction> existant en tant que paramètre dans un constructeur <xref:System.Data.SqlClient.SqlBulkCopy>. Dans ce cas, l’opération de copie en bloc est effectuée dans une transaction existante, et aucune modification n’est apportée à l’état de la transaction (autrement dit, elle n’est ni validée ni abandonnée). Cela permet à une application d'inclure l'opération de copie en bloc dans une transaction avec d'autres opérations de base de données. Toutefois, si vous ne spécifiez pas d’objet <xref:System.Data.SqlClient.SqlTransaction> et que vous transmettez une référence null et que la connexion a une transaction active, une exception est levée.  
  
 Si vous devez restaurer toute l'opération de copie en bloc en raison d'une erreur, ou si la copie en bloc doit s'exécuter dans le cadre d'un processus plus vaste pouvant être restauré, vous pouvez fournir un objet <xref:System.Data.SqlClient.SqlTransaction> au constructeur <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 L’application console suivante est similaire au premier exemple (non transactionnelle), à une exception près : dans cet exemple, l’opération de copie en bloc est incluse dans une transaction externe plus vaste. Quand l'erreur de violation de clé primaire se produit, toute la transaction est restaurée et aucune ligne n'est ajoutée à la table de destination.  
  
> [!IMPORTANT]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**. Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de copie en bloc dans SQL Server](bulk-copy-operations-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
