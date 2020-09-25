---
title: Gestion de l'accès concurrentiel avec DependentTransaction
description: Gérer l’accès concurrentiel aux transactions, y compris les tâches asynchrones, à l’aide de la classe DependentTransaction dans .NET.
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 1e99006c127d83892155bd81e683f5995ac517ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186742"
---
# <a name="managing-concurrency-with-dependenttransaction"></a>Gestion de l'accès concurrentiel avec DependentTransaction

L'objet <xref:System.Transactions.Transaction> est créé à l'aide de la méthode <xref:System.Transactions.Transaction.DependentClone%2A>. Il garantit que la transaction n'est pas validée tant que d'autres parties de code (par exemple, un thread de travail) travaillent encore sur la transaction. Une fois le travail sur la transaction clonée effectué et prêt pour validation, il peut informer le créateur de la transaction à l'aide de la méthode <xref:System.Transactions.DependentTransaction.Complete%2A>. Cela vous permet de conserver la cohérence et l'exactitude des données.  
  
 La classe <xref:System.Transactions.DependentTransaction> permet également de gérer l'accès concurrentiel entre des tâches asynchrones. Dans ce cas, la transaction parent peut continuer d'exécuter du code tandis que le clone dépendant travaille sur ses propres tâches. En d'autres termes, l'exécution de la transaction parent n'est pas bloquée lorsque le clone dépendant travaille.  
  
## <a name="creating-a-dependent-clone"></a>Création d'un clone dépendant  

 Pour créer une transaction dépendante, appelez la méthode <xref:System.Transactions.Transaction.DependentClone%2A> et passez l'énumération <xref:System.Transactions.DependentCloneOption> en tant que paramètre. Ce paramètre définit le comportement de la transaction lorsque `Commit` est appelé sur la transaction parent avant que le clone dépendant n'indique qu'il est prêt pour validation de la transaction (par appel à la méthode <xref:System.Transactions.DependentTransaction.Complete%2A>). Les valeurs valides pour ce paramètre sont les suivantes :  
  
- <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> crée une transaction dépendante qui bloque le processus de validation de la transaction parente jusqu’à ce que la transaction parent expire, ou jusqu’à ce que <xref:System.Transactions.DependentTransaction.Complete%2A> soit appelé sur tous les dépendants qui indiquent leur achèvement. Cela est utile lorsque le client ne souhaite pas valider la transaction parent avant la fin des transactions dépendantes. Si la transaction parent termine son travail avant les transactions dépendantes et qu'elle appelle <xref:System.Transactions.CommittableTransaction.Commit%2A> sur la transaction, le processus de validation est bloqué à un état permettant un travail supplémentaire sur la transaction et la création d'inscriptions jusqu'à ce que tous les clones dépendants aient appelé <xref:System.Transactions.DependentTransaction.Complete%2A>. Une fois qu'ils ont tous terminé leur travail et appelé <xref:System.Transactions.DependentTransaction.Complete%2A>, le processus de validation de la transaction démarre.  
  
- <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> crée une transaction dépendante qui est automatiquement abandonnée si <xref:System.Transactions.CommittableTransaction.Commit%2A> est appelée sur la transaction parent avant l'appel à <xref:System.Transactions.DependentTransaction.Complete%2A>. Dans ce cas, l'ensemble du travail effectué dans la transaction dépendante reste intact au cours d'une transaction et personne ne peut en valider une seule partie.  
  
 La méthode <xref:System.Transactions.DependentTransaction.Complete%2A> ne doit être appelée qu'une fois lorsque votre application termine son travail sur la transaction dépendante ; sinon, une <xref:System.InvalidOperationException> est levée. Après cet appel, ne tentez pas d'effectuer un travail supplémentaire sur la transaction sous peine de lever une exception.  
  
 L'exemple de code suivant montre comment créer une transaction dépendante pour la gestion de deux tâches concurrentes, en clonant une transaction dépendante et en la passant à un thread de travail.  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);
    }  
  
    public void ThreadMethod(object transaction)
    {
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();
             dependentTransaction.Dispose();
        }  
    }  
  
//Client code
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 Le code client crée une étendue transactionnelle qui définit également la transaction ambiante. Ne passez pas la transaction ambiante au thread de travail. À la place, clonez la transaction (ambiante) en cours en appelant la méthode <xref:System.Transactions.Transaction.DependentClone%2A> sur la transaction en cours et passez le clone dépendant au thread de travail.  
  
 La méthode `ThreadMethod` s'exécute sur le nouveau thread. Le client lance un nouveau thread, passant la transaction dépendante en tant que paramètre `ThreadMethod`.  
  
 La transaction dépendante est créée avec <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, la transaction ne peut donc pas être validée avant que le travail transactionnel ne soit effectué sur le deuxième thread et que <xref:System.Transactions.DependentTransaction.Complete%2A> soit appelée sur la transaction dépendante. Cela signifie que si l’étendue du client se termine (quand il tente de supprimer l’objet de transaction à la fin de l' `using` instruction) avant que le nouveau thread <xref:System.Transactions.DependentTransaction.Complete%2A> n’appelle sur la transaction dépendante, le code client se bloque jusqu’à ce que <xref:System.Transactions.DependentTransaction.Complete%2A> soit appelé sur le dépendant. La transaction peut ensuite terminer la validation ou l'abandon.  
  
## <a name="concurrency-issues"></a>Problèmes liés à l'accès concurrentiel  

 Vous devez avoir connaissance de quelques autres problèmes liés à l'accès concurrentiel lorsque vous utilisez la classe <xref:System.Transactions.DependentTransaction> :  
  
- Si le thread de travail restaure la transaction mais que le parent tente sa validation, une <xref:System.Transactions.TransactionAbortedException> est levée.  
  
- Vous devez créer un clone dépendant pour chaque thread de travail de la transaction. Veillez à ne pas passer un même clone dépendant à plusieurs threads, car seul l'un d'entre eux peut appeler <xref:System.Transactions.DependentTransaction.Complete%2A> sur ce clone.  
  
- Si le thread de travail génère un autre thread de travail, créez un clone dépendant à partir du clone dépendant et passez-le au nouveau thread.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Transactions.DependentTransaction>
