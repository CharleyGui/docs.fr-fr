---
title: Transactions et accès simultané
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 049e402345e1abbb46739e48c89101207a43bb27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191669"
---
# <a name="transactions-and-concurrency"></a>Transactions et accès simultané

Une transaction est composée d’une seule commande ou d’un groupe de commandes qui s’exécutent sous forme de package. Les transactions vous permettent de combiner plusieurs opérations en une seule unité de travail. Si une panne se produit pendant la transaction, toutes les mises à jour sont ramenées dans l’état qui était le leur avant le début de la transaction.  
  
 Une transaction doit être conforme aux propriétés ACID (atomicité, cohérence, isolation et durabilité) afin de garantir la cohérence des données. La plupart des systèmes de bases de données relationnelles, tels que Microsoft SQL Server, prennent en charge des transactions en offrant des fonctionnalités de verrouillage, de journalisation et de gestion des transactions lorsqu’une application cliente exécute une opération de mise à jour, d’insertion ou de suppression.  
  
> [!NOTE]
> Les transactions impliquant plusieurs ressources peuvent réduire l'accès concurrentiel si des verrous sont conservés trop longtemps. Par conséquent, réduisez autant que possible les transactions.  
  
 Si une transaction implique plusieurs tables dans la même base de données ou le même serveur, des transactions explicites dans des procédures stockées fonctionnent souvent mieux. Vous pouvez créer des transactions dans des procédures stockées SQL Server à l'aide des instructions Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` et `ROLLBACK TRANSACTION`. Pour plus d'informations, consultez la documentation en ligne de SQL Server.  
  
 Les transactions impliquant différents gestionnaires de ressources, telles qu’une transaction entre SQL Server et Oracle, requièrent une transaction distribuée.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Transactions locales](local-transactions.md)  
 Montre comment effectuer des transactions sur une base de données.  
  
 [Transactions distribuées](distributed-transactions.md)  
 Décrit comment effectuer des transactions distribuées dans ADO.NET.  
  
 [Intégration de System.Transactions à SQL Server](system-transactions-integration-with-sql-server.md)  
 Décrit l' <xref:System.Transactions> intégration avec SQL Server pour l’utilisation de transactions distribuées.  
  
 [Accès concurrentiel optimiste](optimistic-concurrency.md)  
 Décrit les accès concurrentiels optimiste et pessimiste et la manière de tester les violations d'accès concurrentiel.  
  
## <a name="see-also"></a>Voir aussi

- [Notions de base des transactions](../transactions/transaction-fundamentals.md)
- [Connexion à une source de données](connecting-to-a-data-source.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [DbProviderFactories](dbproviderfactories.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
