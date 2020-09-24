---
title: Validation d'une transaction en une phase unique et en plusieurs phases
description: En savoir plus sur la validation des transactions en une ou deux phases dans .NET. Une validation en deux phases (2PC) doit être effectuée si la transaction implique plusieurs ressources.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: f46c22294da4db017eceb0bfd0b5cb2bb093c0b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147409"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="ef30f-104">Validation d'une transaction en une phase unique et en plusieurs phases</span><span class="sxs-lookup"><span data-stu-id="ef30f-104">Committing a Transaction in Single-Phase and Multi-Phase</span></span>

<span data-ttu-id="ef30f-105">Les ressources utilisées dans une transaction sont managées par un gestionnaire de ressources, dont les actions sont coordonnées par un gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="ef30f-105">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="ef30f-106">La rubrique [inscription de ressources en tant que participants dans une transaction](enlisting-resources-as-participants-in-a-transaction.md) explique comment une ressource (ou plusieurs ressources) peut être inscrite dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="ef30f-106">The [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="ef30f-107">Elle traite de la coordination de la validation d'une transaction entre les ressources inscrites.</span><span class="sxs-lookup"><span data-stu-id="ef30f-107">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="ef30f-108">À la fin de la transaction, l'application requiert que la transaction soit validée ou restaurée.</span><span class="sxs-lookup"><span data-stu-id="ef30f-108">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="ef30f-109">Le gestionnaire de transactions doit éliminer tous les risques, par exemple des gestionnaires de ressources votant pour la validation de la transaction et d'autres votant pour sa restauration.</span><span class="sxs-lookup"><span data-stu-id="ef30f-109">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="ef30f-110">Si votre transaction implique plusieurs ressources, vous devez effectuer une validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="ef30f-110">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="ef30f-111">Le protocole de validation en deux phases (une phase de préparation et une phase de validation) garantit, à la fin de la transaction, l'entière validation ou restauration de l'ensemble des modifications apportées aux ressources.</span><span class="sxs-lookup"><span data-stu-id="ef30f-111">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="ef30f-112">Tous les participants sont ensuite informés du résultat final.</span><span class="sxs-lookup"><span data-stu-id="ef30f-112">All the participants are then informed of the final result.</span></span> <span data-ttu-id="ef30f-113">Pour une présentation détaillée du protocole de validation en deux phases, consultez le livre traitant des*transactions : concepts et techniques (série Morgan Kaufmann dans gestion des données Systems) ISBN : 1558601902*» de Jim Gray.</span><span class="sxs-lookup"><span data-stu-id="ef30f-113">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="ef30f-114">Vous pouvez également optimiser les performances de votre transaction en suivant le protocole de validation en une phase.</span><span class="sxs-lookup"><span data-stu-id="ef30f-114">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="ef30f-115">Pour plus d’informations, consultez [optimisation à l’aide de la validation à phase unique et de la notification à phase unique pouvant être promue](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="ef30f-115">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="ef30f-116">Pour être informé du résultat d'une transaction sans participer au vote, inscrivez-vous à l'événement <xref:System.Transactions.Transaction.TransactionCompleted>.</span><span class="sxs-lookup"><span data-stu-id="ef30f-116">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="ef30f-117">Validation en deux phases (2PC)</span><span class="sxs-lookup"><span data-stu-id="ef30f-117">Two-phase Commit (2PC)</span></span>  

 <span data-ttu-id="ef30f-118">Lors de la première phase de transaction, le gestionnaire de transactions interroge chaque ressource afin de déterminer si la transaction doit être validée ou restaurée.</span><span class="sxs-lookup"><span data-stu-id="ef30f-118">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="ef30f-119">Lors de la seconde phase de transaction, le gestionnaire de transactions informe chaque ressource du résultat de ses recherches, lui permettant d'effectuer les nettoyages nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ef30f-119">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="ef30f-120">Pour participer à ce type de transaction, un gestionnaire de ressources doit implémenter l'interface <xref:System.Transactions.IEnlistmentNotification>, qui fournit des méthodes appelées par le gestionnaire de transactions en tant que notifications, au cours d'une validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="ef30f-120">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="ef30f-121">L'exemple suivant illustre une implémentation de ce type.</span><span class="sxs-lookup"><span data-stu-id="ef30f-121">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="ef30f-122">Phase de préparation (Phase 1)</span><span class="sxs-lookup"><span data-stu-id="ef30f-122">Prepare phase (Phase 1)</span></span>  

 <span data-ttu-id="ef30f-123">À la réception d'une requête <xref:System.Transactions.CommittableTransaction.Commit%2A> de l'application, le gestionnaire de transactions lance la phase de préparation des participants inscrits en appelant la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> sur chaque ressource inscrite, afin d'obtenir leur vote concernant la transaction.</span><span class="sxs-lookup"><span data-stu-id="ef30f-123">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="ef30f-124">Le gestionnaire de ressources qui implémente l'interface <xref:System.Transactions.IEnlistmentNotification> doit d'abord implémenter la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29>, comme illustré par l'exemple simple suivant.</span><span class="sxs-lookup"><span data-stu-id="ef30f-124">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="ef30f-125">Lorsque le gestionnaire de ressources durables reçoit cet appel, il doit consigner les informations de récupération de la transaction (disponibles par récupération de la propriété <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A>) ainsi que l'ensemble des informations nécessaires pour terminer la transaction en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="ef30f-125">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="ef30f-126">Il n'est pas nécessaire d'effectuer cette opération au sein de la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> car le gestionnaire de ressources peut le faire sur un thread de travail.</span><span class="sxs-lookup"><span data-stu-id="ef30f-126">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="ef30f-127">Une fois que le gestionnaire de ressources a terminé son travail de préparation, il doit voter pour la validation ou la restauration en appelant la méthode <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ou <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef30f-127">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="ef30f-128">Notez que la classe <xref:System.Transactions.PreparingEnlistment> hérite d'une méthode <xref:System.Transactions.Enlistment.Done%2A> de la classe <xref:System.Transactions.Enlistment>.</span><span class="sxs-lookup"><span data-stu-id="ef30f-128">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="ef30f-129">L'appel à cette méthode sur le rappel <xref:System.Transactions.PreparingEnlistment> au cours de la phase de préparation indique au gestionnaire de transactions qu'il s'agit d'une inscription en lecture seule (des gestionnaires de ressources qui peuvent être lus mais qui ne peuvent pas mettre à jour les données protégées par la transaction) et le gestionnaire de ressources ne reçoit plus de notification du gestionnaire de transaction jusqu'au résultat de la transaction en phase 2.</span><span class="sxs-lookup"><span data-stu-id="ef30f-129">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="ef30f-130">L'application est informée de la validation réussie de la transaction après le vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A> de tous les gestionnaires de ressources </span><span class="sxs-lookup"><span data-stu-id="ef30f-130">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="ef30f-131">Phase de validation (Phase 2)</span><span class="sxs-lookup"><span data-stu-id="ef30f-131">Commit phase (Phase 2)</span></span>  

 <span data-ttu-id="ef30f-132">Lors de la seconde phase de la transaction, si le gestionnaire de transactions a reçu les préparations réussies de tous les gestionnaires de ressources (c'est-à-dire, si tous les gestionnaires de ressources ont appelé <xref:System.Transactions.PreparingEnlistment.Prepared%2A> à la fin de la phase 1), il appelle la méthode <xref:System.Transactions.IEnlistmentNotification.Commit%2A> pour chaque gestionnaire de ressources.</span><span class="sxs-lookup"><span data-stu-id="ef30f-132">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="ef30f-133">Les gestionnaires de ressources peuvent ensuite confirmer les modifications et terminer la validation.</span><span class="sxs-lookup"><span data-stu-id="ef30f-133">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="ef30f-134">Si l'un des gestionnaires de ressources signale un échec de préparation en phase 1, le gestionnaire de transactions appelle la méthode <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> pour chaque gestionnaire de ressources et communique l'échec de la validation à l'application.</span><span class="sxs-lookup"><span data-stu-id="ef30f-134">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="ef30f-135">C'est pourquoi votre gestionnaire de ressources doit implémenter les méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ef30f-135">Thus, your resource manager should implement the following methods.</span></span>  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment
     enlistment.Done();
}  
```  
  
 <span data-ttu-id="ef30f-136">Le gestionnaire de ressources doit effectuer le nécessaire pour terminer la transaction d'après le type de notification, puis en informer le gestionnaire de transactions en appelant la méthode <xref:System.Transactions.Enlistment.Done%2A> sur le paramètre <xref:System.Transactions.Enlistment>.</span><span class="sxs-lookup"><span data-stu-id="ef30f-136">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="ef30f-137">Cela peut s'effectuer sur un thread de travail.</span><span class="sxs-lookup"><span data-stu-id="ef30f-137">This work can be done on a worker thread.</span></span> <span data-ttu-id="ef30f-138">Notez que les notifications de la phase 2 peuvent se produire en ligne sur le même thread qui a appelé la méthode <xref:System.Transactions.PreparingEnlistment.Prepared%2A> de la phase 1.</span><span class="sxs-lookup"><span data-stu-id="ef30f-138">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="ef30f-139">Par conséquent, vous ne devez effectuer aucun travail après l'appel <xref:System.Transactions.PreparingEnlistment.Prepared%2A> (par exemple, libérer des verrous) que vous devez avoir terminé avant de recevoir les notifications de phase 2.</span><span class="sxs-lookup"><span data-stu-id="ef30f-139">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="ef30f-140">Implémentation de la méthode InDoubt</span><span class="sxs-lookup"><span data-stu-id="ef30f-140">Implementing InDoubt</span></span>  

 <span data-ttu-id="ef30f-141">Enfin, implémentez la méthode <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> pour le gestionnaire de ressources volatiles.</span><span class="sxs-lookup"><span data-stu-id="ef30f-141">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="ef30f-142">Cette méthode est appelée si le gestionnaire de transactions perd contact avec un ou plusieurs participants, rendant leur état inconnu.</span><span class="sxs-lookup"><span data-stu-id="ef30f-142">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="ef30f-143">Dans ce cas, consignez ce fait afin de pouvoir ensuite contrôler si des participants à la transaction ont été laissés dans un état incohérent.</span><span class="sxs-lookup"><span data-stu-id="ef30f-143">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="ef30f-144">Optimisation de la validation en une phase</span><span class="sxs-lookup"><span data-stu-id="ef30f-144">Single Phase Commit Optimization</span></span>  

 <span data-ttu-id="ef30f-145">Le protocole de validation en une phase est plus efficace lors de l'exécution car toutes les mises à jour sont effectuées sans coordination explicite.</span><span class="sxs-lookup"><span data-stu-id="ef30f-145">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="ef30f-146">Pour plus d’informations sur ce protocole, consultez [optimisation à l’aide de la validation à phase unique et de la notification à phase unique pouvant être promue](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="ef30f-146">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef30f-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef30f-147">See also</span></span>

- [<span data-ttu-id="ef30f-148">Optimisation à l'aide de la validation à phase unique et de la notification de phase unique pouvant être promue</span><span class="sxs-lookup"><span data-stu-id="ef30f-148">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="ef30f-149">Inscription de ressources comme participants à une transaction</span><span class="sxs-lookup"><span data-stu-id="ef30f-149">Enlisting Resources as Participants in a Transaction</span></span>](enlisting-resources-as-participants-in-a-transaction.md)
