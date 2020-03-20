---
title: Implémentation d'une transaction explicite à l'aide de CommittableTransaction
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: f8db79db6c4a66dfe13ec936313c4cf2c3b93be5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174405"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>Implémentation d'une transaction explicite à l'aide de CommittableTransaction
La classe <xref:System.Transactions.CommittableTransaction> permet aux applications d’utiliser une transaction de façon explicite au lieu d’utiliser la classe <xref:System.Transactions.TransactionScope> de façon implicite. Cela se révèle utile pour les applications qui souhaitent utiliser une même transaction pour plusieurs appels de fonction ou plusieurs appels de thread. Contrairement à la classe <xref:System.Transactions.TransactionScope>, le writer d’application doit absolument appeler les méthodes <xref:System.Transactions.CommittableTransaction.Commit%2A> et <xref:System.Transactions.Transaction.Rollback%2A> pour valider ou abandonner la transaction.  
  
## <a name="overview-of-the-committabletransaction-class"></a>Vue d'ensemble de la classe CommittableTransaction  
 La classe <xref:System.Transactions.CommittableTransaction> est dérivée de la classe <xref:System.Transactions.Transaction> et offre donc toutes les fonctionnalités de cette classe. Particulièrement utile, la méthode <xref:System.Transactions.Transaction.Rollback%2A> de la classe <xref:System.Transactions.Transaction> permet également de restaurer un objet <xref:System.Transactions.CommittableTransaction>.  
  
 La classe <xref:System.Transactions.Transaction> est similaire à la classe <xref:System.Transactions.CommittableTransaction> mais ne fournit pas la méthode `Commit`. Cela permet de passer l'objet transaction (ou ses clones) à d'autres méthodes (potentiellement sur d'autres threads) tout en contrôlant l'instant de validation de la transaction. Le code appelé peut s'inscrire à la transaction et voter, mais seul le créateur de l'objet <xref:System.Transactions.CommittableTransaction> a la responsabilité de valider la transaction.  
  
 Si vous utilisez la classe <xref:System.Transactions.CommittableTransaction>, notez les éléments suivants :  
  
- La création d'une transaction <xref:System.Transactions.CommittableTransaction> ne définit pas la transaction ambiante. Vous devez définir et réinitialiser la transaction ambiante pour que le gestionnaire de ressources fonctionne sous le contexte de transaction approprié et de façon adaptée. Pour configurer la transaction ambiante en cours, affectez la propriété <xref:System.Transactions.Transaction.Current%2A> statique à l'objet <xref:System.Transactions.Transaction> global.  
  
- Un objet <xref:System.Transactions.CommittableTransaction> ne peut pas être réutilisé. Un objet <xref:System.Transactions.CommittableTransaction> qui a été validé ou restauré ne peut pas être réutilisé pour une transaction. Autrement dit, on ne peut pas l'utiliser en tant que contexte de la transaction ambiante en cours.  
  
## <a name="creating-a-committabletransaction"></a>Création d'une CommittableTransaction  
 L'exemple suivant illustre la création et la validation d'une nouvelle <xref:System.Transactions.CommittableTransaction>.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 La création d'une instance de <xref:System.Transactions.CommittableTransaction> n'entraîne pas automatiquement la définition du contexte de transaction ambiante. Par conséquent, les opérations effectuées sur un gestionnaire de ressources ne font pas partie de cette transaction. La propriété <xref:System.Transactions.Transaction.Current%2A> statique de l'objet <xref:System.Transactions.Transaction> global permet de définir ou de récupérer la transaction ambiante. Puis l'application doit la configurer manuellement pour s'assurer que le gestionnaire de ressources peut participer à la transaction. Il est également conseillé d'enregistrer l'ancienne transaction ambiante et de la restaurer après l'utilisation de l'objet <xref:System.Transactions.CommittableTransaction>.  
  
 Pour valider la transaction, vous devez explicitement appeler la méthode <xref:System.Transactions.CommittableTransaction.Commit%2A>. Pour restaurer une transaction, appelez la méthode <xref:System.Transactions.Transaction.Rollback%2A>. Il est important de noter que, jusqu'à la validation ou la restauration d'une <xref:System.Transactions.CommittableTransaction>, toutes les ressources concernées par la transaction sont verrouillées.  
  
 Un objet <xref:System.Transactions.CommittableTransaction> peut être utilisé pour plusieurs appels de fonction et threads. Toutefois, le développeur d'applications reste responsable de la gestion des exceptions et de l'appel à la méthode <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> en cas de défaillance.  
  
## <a name="asynchronous-commit"></a>Validation asynchrone  
 La classe <xref:System.Transactions.CommittableTransaction> fournit également un mécanisme de validation asynchrone des transactions. La validation d'une transaction peut prendre un moment, puisqu'elle peut impliquer l'accès à plusieurs bases de données et un temps de latence du réseau. Pour éviter les blocages des applications à haut débit, utilisez la validation asynchrone pour terminer le travail transactionnel aussi rapidement que possible et exécutez l'opération de validation en arrière-plan. Cela est possible grâce aux méthodes <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> et <xref:System.Transactions.CommittableTransaction.EndCommit%2A> de la classe <xref:System.Transactions.CommittableTransaction>.  
  
 Vous pouvez appeler <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> pour transmettre la suspension de la validation à un thread du pool de threads. Vous pouvez également appeler <xref:System.Transactions.CommittableTransaction.EndCommit%2A> pour contrôler si la transaction a bien été validée. Si la transaction n'a pas été validée, pour quelque raison que ce soit, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> lève une exception de transaction. Si la transaction n'a toujours pas été validée lors de l'appel à <xref:System.Transactions.CommittableTransaction.EndCommit%2A>, l'appelant reste bloqué jusqu'à ce que la transaction soit validée ou abandonnée.  
  
 La méthode la plus simple pour réaliser une validation asynchrone consiste à fournir une méthode de rappel à appeler une fois la validation terminée. Vous devez toutefois appeler la méthode <xref:System.Transactions.CommittableTransaction.EndCommit%2A> sur l'objet <xref:System.Transactions.CommittableTransaction> d'origine utilisé pour l'appel. Pour obtenir cet objet, vous pouvez abattre le paramètre *IAsyncResult* de <xref:System.IAsyncResult> la méthode de rappel, puisque la classe implémente la <xref:System.Transactions.CommittableTransaction> classe.  
  
 L'exemple suivant illustre la réalisation d'une validation asynchrone.  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation d’une transaction implicite à l’aide de l’étendue de transaction](implementing-an-implicit-transaction-using-transaction-scope.md)
- [Traitement des transactions](index.md)
