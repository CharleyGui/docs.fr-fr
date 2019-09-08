---
title: Transaction et opérations de copie en bloc
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: 73c375f9acfd193680982994ed0852454cefebe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791442"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transaction et opérations de copie en bloc
Les opérations de copie en bloc peuvent être réalisées sous forme d'opérations isolées ou en tant qu'étape d'une transaction en comptant plusieurs. Cette dernière option vous permet d'effectuer plus d'une opération de copie en bloc dans la même transaction et d'effectuer d'autres opérations de base de données (telles que des insertions, des mises à jour et des suppressions) tout en vous laissant la possibilité de valider ou de restaurer toute la transaction.  
  
 Par défaut, une opération de copie en bloc est exécutée sous forme d'opération isolée : elle se produit de manière non traitée, sans possibilité de restauration. Si vous devez restaurer tout ou partie de la copie en bloc en cas d’erreur, vous pouvez utiliser une <xref:System.Data.SqlClient.SqlBulkCopy>transaction managée, effectuer l’opération de copie en bloc dans une transaction existante ou être inscrite dans un **System. transactions**<xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Exécution d'une opération de copie en bloc non traitée  
 L'application console suivante montre ce qui se passe lorsqu'une opération de copie en bloc non traitée rencontre une erreur dans l'opération.  
  
 Dans l’exemple, la table source et la table de destination incluent `Identity` chacune une colonne nommée **ProductID**. Le code commence par préparer la table de destination en supprimant toutes les lignes, puis en insérant une ligne unique dont le **ProductID** est connu pour exister dans la table source. Par défaut, une nouvelle valeur pour la colonne `Identity` est générée dans la table de destination pour chaque ligne ajoutée. Dans cet exemple, une option est définie lorsque la connexion est ouverte qui oblige le processus de chargement en bloc à utiliser les valeurs `Identity` de la table source.  
  
 L'opération de copie en bloc est exécutée avec la propriété <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> ayant la valeur 10. Lorsque l'opération rencontre la ligne non valide, une exception est levée. Dans ce premier exemple, l'opération de copie en bloc n'est pas traitée. Tous les lots copiés jusqu’au moment de l’erreur sont validés ; le lot contenant la clé dupliquée est annulé et l’opération de copie en bloc est suspendue avant la reprise du traitement des autres lots.  
  
> [!NOTE]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy** uniquement. Si les tables source et de destination se trouvent dans la même instance de SQL Server, il est plus facile et plus rapide d’utiliser`INSERT … SELECT` une instruction Transact-SQL pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Exécution d’une opération de copie en bloc dédiée dans une transaction  
 Par défaut, une opération de copie en bloc est sa propre transaction. Si vous voulez effectuer une opération de copie en bloc dédiée, créez une nouvelle instance de <xref:System.Data.SqlClient.SqlBulkCopy> avec une chaîne de connexion ou utilisez un objet <xref:System.Data.SqlClient.SqlConnection> existant sans transaction active. Dans chaque scénario, l'opération de copie en bloc crée puis valide ou annule la transaction.  
  
 Vous pouvez spécifier explicitement l’option <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> dans le constructeur de classe <xref:System.Data.SqlClient.SqlBulkCopy> pour exécuter explicitement une opération de copie en bloc dans sa propre transaction. Chaque lot de l’opération de copie en bloc s’exécute alors dans une transaction distincte.  
  
> [!NOTE]
> Puisque des lots différents sont exécutés dans différentes transactions, si une erreur se produit durant l'opération de copie en bloc, toutes les lignes du lot en cours seront annulées mais les lignes des lots précédents resteront dans la base de données.  
  
 L'application console suivante est similaire à l'exemple précédent, à une exception près : Dans cet exemple, l'opération de copie en bloc gère ses propres transactions. Tous les lots copiés jusqu’au moment de l’erreur sont validés ; le lot contenant la clé dupliquée est annulé et l’opération de copie en bloc est suspendue avant la reprise du traitement des autres lots.  
  
> [!IMPORTANT]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy** uniquement. Si les tables source et de destination se trouvent dans la même instance de SQL Server, il est plus facile et plus rapide d’utiliser`INSERT … SELECT` une instruction Transact-SQL pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Utilisation de transactions existantes  
 Vous pouvez spécifier un objet <xref:System.Data.SqlClient.SqlTransaction> existant comme paramètre dans un constructeur <xref:System.Data.SqlClient.SqlBulkCopy>. Dans cette situation, l’opération de copie en bloc est effectuée dans une transaction existante et l’état de la transaction ne subit aucune modification (c’est-à-dire qu’elle n’est ni validée ni abandonnée). Cela permet à une application d'inclure l'opération de copie en bloc dans une transaction avec d'autres opérations de base de données. Cependant, si vous ne spécifiez pas un objet <xref:System.Data.SqlClient.SqlTransaction> et passez une référence null, et que la connexion a une transaction active, une exception est levée.  
  
 Si vous devez restaurer toute l'opération de copie en bloc en raison d'une d'erreur ou si la copie en bloc doit s'exécuter dans le cadre d'un plus grand processus pouvant être restauré, vous pouvez fournir un objet <xref:System.Data.SqlClient.SqlTransaction> au constructeur <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 L’application console suivante est semblable au premier exemple (non accompli), avec une exception : dans cet exemple, l’opération de copie en bloc est incluse dans une transaction externe plus large. Si l'erreur de violation de clé primaire se produit, toute la transaction est annulée et aucune ligne n'est ajoutée à la table de destination.  
  
> [!IMPORTANT]
> Cet exemple ne s’exécute pas, sauf si vous avez créé les tables de travail comme décrit dans l' [exemple de configuration de copie en bloc](bulk-copy-example-setup.md). Ce code est fourni pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy** uniquement. Si les tables source et de destination se trouvent dans la même instance de SQL Server, il est plus facile et plus rapide d’utiliser`INSERT … SELECT` une instruction Transact-SQL pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de copie en bloc dans SQL Server](bulk-copy-operations-in-sql-server.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
