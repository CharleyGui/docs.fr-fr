---
title: Gestion de l'accès concurrentiel avec DependentTransaction
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: a8ddcab4b065c3400f9f9f7ec9ce04befdd0f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174379"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="52a57-102">Gestion de l'accès concurrentiel avec DependentTransaction</span><span class="sxs-lookup"><span data-stu-id="52a57-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="52a57-103">L'objet <xref:System.Transactions.Transaction> est créé à l'aide de la méthode <xref:System.Transactions.Transaction.DependentClone%2A>.</span><span class="sxs-lookup"><span data-stu-id="52a57-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="52a57-104">Il garantit que la transaction n'est pas validée tant que d'autres parties de code (par exemple, un thread de travail) travaillent encore sur la transaction.</span><span class="sxs-lookup"><span data-stu-id="52a57-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="52a57-105">Une fois le travail sur la transaction clonée effectué et prêt pour validation, il peut informer le créateur de la transaction à l'aide de la méthode <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="52a57-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="52a57-106">Cela vous permet de conserver la cohérence et l'exactitude des données.</span><span class="sxs-lookup"><span data-stu-id="52a57-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="52a57-107">La classe <xref:System.Transactions.DependentTransaction> permet également de gérer l'accès concurrentiel entre des tâches asynchrones.</span><span class="sxs-lookup"><span data-stu-id="52a57-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="52a57-108">Dans ce cas, la transaction parent peut continuer d'exécuter du code tandis que le clone dépendant travaille sur ses propres tâches.</span><span class="sxs-lookup"><span data-stu-id="52a57-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="52a57-109">En d'autres termes, l'exécution de la transaction parent n'est pas bloquée lorsque le clone dépendant travaille.</span><span class="sxs-lookup"><span data-stu-id="52a57-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="52a57-110">Création d'un clone dépendant</span><span class="sxs-lookup"><span data-stu-id="52a57-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="52a57-111">Pour créer une transaction dépendante, appelez la méthode <xref:System.Transactions.Transaction.DependentClone%2A> et passez l'énumération <xref:System.Transactions.DependentCloneOption> en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="52a57-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="52a57-112">Ce paramètre définit le comportement de la transaction lorsque `Commit` est appelé sur la transaction parent avant que le clone dépendant n'indique qu'il est prêt pour validation de la transaction (par appel à la méthode <xref:System.Transactions.DependentTransaction.Complete%2A>).</span><span class="sxs-lookup"><span data-stu-id="52a57-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="52a57-113">Les valeurs valides pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="52a57-113">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="52a57-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>crée une transaction à charge qui bloque le processus de validation <xref:System.Transactions.DependentTransaction.Complete%2A> de la transaction mère jusqu’à ce que la transaction mère soit annulée, ou jusqu’à ce qu’elle soit appelée sur toutes les personnes à charge indiquant leur achèvement.</span><span class="sxs-lookup"><span data-stu-id="52a57-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="52a57-115">Cela est utile lorsque le client ne souhaite pas valider la transaction parent avant la fin des transactions dépendantes.</span><span class="sxs-lookup"><span data-stu-id="52a57-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="52a57-116">Si la transaction parent termine son travail avant les transactions dépendantes et qu'elle appelle <xref:System.Transactions.CommittableTransaction.Commit%2A> sur la transaction, le processus de validation est bloqué à un état permettant un travail supplémentaire sur la transaction et la création d'inscriptions jusqu'à ce que tous les clones dépendants aient appelé <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="52a57-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="52a57-117">Une fois qu'ils ont tous terminé leur travail et appelé <xref:System.Transactions.DependentTransaction.Complete%2A>, le processus de validation de la transaction démarre.</span><span class="sxs-lookup"><span data-stu-id="52a57-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="52a57-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> crée une transaction dépendante qui est automatiquement abandonnée si <xref:System.Transactions.CommittableTransaction.Commit%2A> est appelée sur la transaction parent avant l'appel à <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="52a57-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="52a57-119">Dans ce cas, l'ensemble du travail effectué dans la transaction dépendante reste intact au cours d'une transaction et personne ne peut en valider une seule partie.</span><span class="sxs-lookup"><span data-stu-id="52a57-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="52a57-120">La méthode <xref:System.Transactions.DependentTransaction.Complete%2A> ne doit être appelée qu'une fois lorsque votre application termine son travail sur la transaction dépendante ; sinon, une <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="52a57-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="52a57-121">Après cet appel, ne tentez pas d'effectuer un travail supplémentaire sur la transaction sous peine de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="52a57-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="52a57-122">L'exemple de code suivant montre comment créer une transaction dépendante pour la gestion de deux tâches concurrentes, en clonant une transaction dépendante et en la passant à un thread de travail.</span><span class="sxs-lookup"><span data-stu-id="52a57-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
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
  
 <span data-ttu-id="52a57-123">Le code client crée une étendue transactionnelle qui définit également la transaction ambiante.</span><span class="sxs-lookup"><span data-stu-id="52a57-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="52a57-124">Ne passez pas la transaction ambiante au thread de travail.</span><span class="sxs-lookup"><span data-stu-id="52a57-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="52a57-125">À la place, clonez la transaction (ambiante) en cours en appelant la méthode <xref:System.Transactions.Transaction.DependentClone%2A> sur la transaction en cours et passez le clone dépendant au thread de travail.</span><span class="sxs-lookup"><span data-stu-id="52a57-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="52a57-126">La méthode `ThreadMethod` s'exécute sur le nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="52a57-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="52a57-127">Le client lance un nouveau thread, passant la transaction dépendante en tant que paramètre `ThreadMethod`.</span><span class="sxs-lookup"><span data-stu-id="52a57-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="52a57-128">La transaction dépendante est créée avec <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, la transaction ne peut donc pas être validée avant que le travail transactionnel ne soit effectué sur le deuxième thread et que <xref:System.Transactions.DependentTransaction.Complete%2A> soit appelée sur la transaction dépendante.</span><span class="sxs-lookup"><span data-stu-id="52a57-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="52a57-129">Cela signifie que si la portée du client prend fin (lorsqu’il `using` tente de disposer de <xref:System.Transactions.DependentTransaction.Complete%2A> l’objet de transaction à <xref:System.Transactions.DependentTransaction.Complete%2A> la fin de la déclaration) avant que le nouveau thread ne s’en remette à la transaction dépendante, le code client bloque jusqu’à ce qu’il soit appelé sur la personne à charge.</span><span class="sxs-lookup"><span data-stu-id="52a57-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="52a57-130">La transaction peut ensuite terminer la validation ou l'abandon.</span><span class="sxs-lookup"><span data-stu-id="52a57-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="52a57-131">Problèmes liés à l'accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="52a57-131">Concurrency Issues</span></span>  
 <span data-ttu-id="52a57-132">Vous devez avoir connaissance de quelques autres problèmes liés à l'accès concurrentiel lorsque vous utilisez la classe <xref:System.Transactions.DependentTransaction> :</span><span class="sxs-lookup"><span data-stu-id="52a57-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="52a57-133">Si le thread de travail restaure la transaction mais que le parent tente sa validation, une <xref:System.Transactions.TransactionAbortedException> est levée.</span><span class="sxs-lookup"><span data-stu-id="52a57-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="52a57-134">Vous devez créer un clone dépendant pour chaque thread de travail de la transaction.</span><span class="sxs-lookup"><span data-stu-id="52a57-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="52a57-135">Veillez à ne pas passer un même clone dépendant à plusieurs threads, car seul l'un d'entre eux peut appeler <xref:System.Transactions.DependentTransaction.Complete%2A> sur ce clone.</span><span class="sxs-lookup"><span data-stu-id="52a57-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="52a57-136">Si le thread de travail génère un autre thread de travail, créez un clone dépendant à partir du clone dépendant et passez-le au nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="52a57-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a57-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52a57-137">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
