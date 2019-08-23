---
title: Compensation
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935430"
---
# <a name="compensation"></a><span data-ttu-id="121d8-102">Compensation</span><span class="sxs-lookup"><span data-stu-id="121d8-102">Compensation</span></span>
<span data-ttu-id="121d8-103">La compensation en Windows Workflow Foundation (WF) est le mécanisme par lequel le travail effectué précédemment peut être annulé ou compensé (selon la logique définie par l’application) lorsqu’une défaillance suivante se produit.</span><span class="sxs-lookup"><span data-stu-id="121d8-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="121d8-104">Cette section décrit comment utiliser une compensation dans les flux de travail.</span><span class="sxs-lookup"><span data-stu-id="121d8-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="121d8-105">Compensation et Transactions</span><span class="sxs-lookup"><span data-stu-id="121d8-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="121d8-106">Une transaction vous permet de combiner plusieurs opérations en une seule unité de travail.</span><span class="sxs-lookup"><span data-stu-id="121d8-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="121d8-107">L’utilisation d’une transaction permet à votre application d’annuler (restaurer) toute modification exécutée depuis une transaction en cas d’erreur au cours du processus de transaction.</span><span class="sxs-lookup"><span data-stu-id="121d8-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="121d8-108">Toutefois, l’utilisation de transactions peut ne pas convenir dans le cas d’un travail de longue durée.</span><span class="sxs-lookup"><span data-stu-id="121d8-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="121d8-109">Par exemple, une application de planification de voyage est implémentée en tant que flux de travail.</span><span class="sxs-lookup"><span data-stu-id="121d8-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="121d8-110">Les étapes du flux de travail peuvent porter sur la réservation d'un vol, l'attente de l'approbation du gestionnaire et le paiement du vol.</span><span class="sxs-lookup"><span data-stu-id="121d8-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="121d8-111">Ce processus pourrait prendre de nombreux jours et ne s’avère pas pratique pour que les étapes de réservation et de paiement du vol puissent participer à la même transaction.</span><span class="sxs-lookup"><span data-stu-id="121d8-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="121d8-112">Dans un tel scénario, la compensation pourrait être utilisée pour annuler l'étape de réservation du flux de travail en cas d'erreur ultérieure lors du traitement.</span><span class="sxs-lookup"><span data-stu-id="121d8-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="121d8-113">Cette rubrique couvre la compensation dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="121d8-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="121d8-114">Pour plus d’informations sur les transactions dans les workflows, <xref:System.Activities.Statements.TransactionScope>consultez [transactions](workflow-transactions.md) et.</span><span class="sxs-lookup"><span data-stu-id="121d8-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="121d8-115">Pour plus d’informations sur les transactions <xref:System.Transactions?displayProperty=nameWithType> , <xref:System.Transactions.Transaction?displayProperty=nameWithType>consultez et.</span><span class="sxs-lookup"><span data-stu-id="121d8-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="121d8-116">Utilisation de CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="121d8-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="121d8-117"><xref:System.Activities.Statements.CompensableActivity> est l'activité de compensation principale dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="121d8-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="121d8-118">Toutes les activités qui effectuent un travail pouvant nécessiter d'être compensé sont placées dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="121d8-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="121d8-119">Dans cet exemple, l'étape de réservation de l'achat d'un vol est placée dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un <xref:System.Activities.Statements.CompensableActivity> et l'annulation de la réservation est placée dans le <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="121d8-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="121d8-120">Juste après le <xref:System.Activities.Statements.CompensableActivity> dans le workflow, deux activités doivent être exécutées, d'une part l'approbation du gestionnaire, d'autre part l'achat du vol.</span><span class="sxs-lookup"><span data-stu-id="121d8-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="121d8-121">Si une condition d'erreur entraîne l'annulation du workflow une fois <xref:System.Activities.Statements.CompensableActivity> correctement terminé, les activités du gestionnaire <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> sont planifiées et le vol est annulé.</span><span class="sxs-lookup"><span data-stu-id="121d8-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="121d8-122">L'exemple suivant est le workflow en XAML.</span><span class="sxs-lookup"><span data-stu-id="121d8-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="121d8-123">Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="121d8-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="121d8-124">**ReserveFlight Le ticket est réservé.**</span><span class="sxs-lookup"><span data-stu-id="121d8-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="121d8-125">**ManagerApproval Approbation du gestionnaire reçue.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="121d8-126">**PurchaseFlight Le ticket est acheté.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="121d8-127">**Le workflow s’est terminé avec succès avec l’État: Légendes.**</span><span class="sxs-lookup"><span data-stu-id="121d8-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
> <span data-ttu-id="121d8-128">Les exemples d'activités de cette rubrique, telles que `ReserveFlight`, affichent leur nom et leur but dans la console pour faciliter l'illustration de l'ordre dans lequel les activités sont exécutées lorsque la compensation se produit.</span><span class="sxs-lookup"><span data-stu-id="121d8-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="121d8-129">Compensation de workflow par défaut</span><span class="sxs-lookup"><span data-stu-id="121d8-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="121d8-130">Par défaut, si le workflow est annulé, la logique de compensation est exécutée pour toute activité compensable ayant abouti et n'ayant pas encore été confirmée ou compensée.</span><span class="sxs-lookup"><span data-stu-id="121d8-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="121d8-131">Lorsqu’un <xref:System.Activities.Statements.CompensableActivity> est *confirmé*, la compensation pour l’activité ne peut plus être appelée.</span><span class="sxs-lookup"><span data-stu-id="121d8-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="121d8-132">Le processus de confirmation est décrit plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="121d8-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="121d8-133">Dans cet exemple, une exception est levée après que le vol a été réservé mais avant l'étape d'approbation par le gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="121d8-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="121d8-134">Cet exemple est le workflow en XAML.</span><span class="sxs-lookup"><span data-stu-id="121d8-134">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="121d8-135">Lorsque le workflow est appelé, l'exception de condition d'erreur simulée est gérée par l'application hôte dans <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, le workflow est annulé, et la logique de compensation est appelée.</span><span class="sxs-lookup"><span data-stu-id="121d8-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="121d8-136">**ReserveFlight Le ticket est réservé.**</span><span class="sxs-lookup"><span data-stu-id="121d8-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="121d8-137">**SimulatedErrorCondition Levée d’un ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="121d8-138">**Exception non gérée du flux de travail:**  </span><span class="sxs-lookup"><span data-stu-id="121d8-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="121d8-139">**System. ApplicationException: Condition d’erreur simulée dans le flux de travail.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="121d8-140">**CancelFlight Le ticket est annulé.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="121d8-141">**Le workflow s’est terminé avec succès avec l’État: Annulée.**</span><span class="sxs-lookup"><span data-stu-id="121d8-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="121d8-142">Annulation et CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="121d8-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="121d8-143">Si les activités dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un <xref:System.Activities.Statements.CompensableActivity> ne se sont pas terminées et que l'activité est annulée, les activités dans le <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="121d8-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="121d8-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> est appelé uniquement si les activités dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> ne se sont pas terminées et que l'activité est annulée.</span><span class="sxs-lookup"><span data-stu-id="121d8-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="121d8-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> est exécuté uniquement si les activités dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se sont terminées avec succès et que la compensation est, par la suite, appelée sur l'activité.</span><span class="sxs-lookup"><span data-stu-id="121d8-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="121d8-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> donne aux auteurs de workflow la possibilité de fournir n’importe quelle logique d’annulation appropriée.</span><span class="sxs-lookup"><span data-stu-id="121d8-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="121d8-147">Dans l'exemple suivant, une exception est levée pendant l'exécution de <xref:System.Activities.Statements.CompensableActivity.Body%2A>, puis <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="121d8-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="121d8-148">Cet exemple est le workflow en XAML.</span><span class="sxs-lookup"><span data-stu-id="121d8-148">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="121d8-149">Lorsque le workflow est appelé, l'exception de condition d'erreur simulée est gérée par l'application hôte dans <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, le workflow est annulé, et la logique d'annulation de <xref:System.Activities.Statements.CompensableActivity> est appelée.</span><span class="sxs-lookup"><span data-stu-id="121d8-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="121d8-150">Dans cet exemple, la logique de compensation et la logique d'annulation ont des objectifs différents.</span><span class="sxs-lookup"><span data-stu-id="121d8-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="121d8-151">Si <xref:System.Activities.Statements.CompensableActivity.Body%2A> se termine avec succès, cela signifie que la carte de crédit a été facturée et le vol réservé, donc la compensation doit annuler les deux étapes.</span><span class="sxs-lookup"><span data-stu-id="121d8-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="121d8-152">(Dans cet exemple, l'annulation de vol annule automatiquement les frais de carte de crédit.) Toutefois, si <xref:System.Activities.Statements.CompensableActivity> est annulé, cela signifie que <xref:System.Activities.Statements.CompensableActivity.Body%2A> n'est pas terminé et donc la logique de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> doit être en mesure de déterminer comment mieux gérer l'annulation.</span><span class="sxs-lookup"><span data-stu-id="121d8-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="121d8-153">Dans cet exemple, le <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> annule la facturation de la carte de crédit, mais comme `ReserveFlight` était la dernière activité dans <xref:System.Activities.Statements.CompensableActivity.Body%2A>, il n'essaie pas d'annuler le vol.</span><span class="sxs-lookup"><span data-stu-id="121d8-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="121d8-154">Comme `ReserveFlight` était la dernière activité dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A>, si elle s'est terminée avec succès, <xref:System.Activities.Statements.CompensableActivity.Body%2A> s'est terminé et aucune annulation n'est possible.</span><span class="sxs-lookup"><span data-stu-id="121d8-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="121d8-155">**ChargeCreditCard: Charger la carte de crédit pour le vol.**</span><span class="sxs-lookup"><span data-stu-id="121d8-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="121d8-156">**SimulatedErrorCondition Levée d’un ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="121d8-157">**Exception non gérée du flux de travail:**  </span><span class="sxs-lookup"><span data-stu-id="121d8-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="121d8-158">**System. ApplicationException: Condition d’erreur simulée dans le flux de travail.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="121d8-159">**CancelCreditCard: Annulez les frais de carte de crédit.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="121d8-160">**Le workflow s’est terminé avec succès avec l’État: Annulée.**</span><span class="sxs-lookup"><span data-stu-id="121d8-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="121d8-161">Pour plus d’informations sur l’annulation, consultez [annulation](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="121d8-161">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="121d8-162">Compensation explicite à l'aide de l'activité Compensate</span><span class="sxs-lookup"><span data-stu-id="121d8-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="121d8-163">Dans la section précédente, la compensation implicite a été couverte.</span><span class="sxs-lookup"><span data-stu-id="121d8-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="121d8-164">La compensation implicite peut convenir à des scénarios simples, mais si un contrôle explicite supplémentaire est requis sur la planification de compensation, la gestion de l'activité <xref:System.Activities.Statements.Compensate> peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="121d8-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="121d8-165">Pour initialiser le processus de compensation avec l'activité <xref:System.Activities.Statements.Compensate>, le <xref:System.Activities.Statements.CompensationToken> du <xref:System.Activities.Statements.CompensableActivity> pour lequel la compensation est désirée est utilisé.</span><span class="sxs-lookup"><span data-stu-id="121d8-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="121d8-166">L'activité <xref:System.Activities.Statements.Compensate> peut être utilisée pour initialiser la compensation sur tout <xref:System.Activities.Statements.CompensableActivity> ayant abouti et qui n'a pas été confirmé ou compensé.</span><span class="sxs-lookup"><span data-stu-id="121d8-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="121d8-167">Par exemple, une activité <xref:System.Activities.Statements.Compensate> pourrait être utilisée dans la section <xref:System.Activities.Statements.TryCatch.Catches%2A> d'une activité <xref:System.Activities.Statements.TryCatch>, ou à n'importe quel moment après que le <xref:System.Activities.Statements.CompensableActivity> a abouti.</span><span class="sxs-lookup"><span data-stu-id="121d8-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="121d8-168">Dans cet exemple, l'activité <xref:System.Activities.Statements.Compensate> est utilisée dans la propriété <xref:System.Activities.Statements.TryCatch.Catches%2A> d'une activité <xref:System.Activities.Statements.TryCatch> pour inverser l'action du <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="121d8-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="121d8-169">Cet exemple est le workflow en XAML.</span><span class="sxs-lookup"><span data-stu-id="121d8-169">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="121d8-170">Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="121d8-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="121d8-171">**ReserveFlight Le ticket est réservé.**</span><span class="sxs-lookup"><span data-stu-id="121d8-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="121d8-172">**SimulatedErrorCondition Levée d’un ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="121d8-173">**CancelFlight Le ticket est annulé.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="121d8-174">**Le workflow s’est terminé avec succès avec l’État: Légendes.**</span><span class="sxs-lookup"><span data-stu-id="121d8-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="121d8-175">Confirmer la compensation</span><span class="sxs-lookup"><span data-stu-id="121d8-175">Confirming Compensation</span></span>  
 <span data-ttu-id="121d8-176">Par défaut, les activités compensables peuvent être compensées à n'importe quel moment, à condition qu'elles soient achevées.</span><span class="sxs-lookup"><span data-stu-id="121d8-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="121d8-177">Toutefois, dans certains cas cela peut ne pas être suffisant.</span><span class="sxs-lookup"><span data-stu-id="121d8-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="121d8-178">Dans l'exemple précédent la compensation destinée à réserver le ticket devait permettre d'annuler la réservation.</span><span class="sxs-lookup"><span data-stu-id="121d8-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="121d8-179">Toutefois, une fois le vol effectué cette étape de compensation n'est plus valide.</span><span class="sxs-lookup"><span data-stu-id="121d8-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="121d8-180">La confirmation de l'activité compensable appelle l'activité spécifiée dans la section <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="121d8-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="121d8-181">Une utilisation possible de cela est de permettre la libération de toutes les ressources qui sont nécessaires pour effectuer la compensation.</span><span class="sxs-lookup"><span data-stu-id="121d8-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="121d8-182">Lorsqu'une activité compensable est confirmée, il n'est pas possible de la dédommager, et si vous tentez cette opération, une exception <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="121d8-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="121d8-183">Lorsqu'un flux de travail aboutit, toutes les activités non confirmées et non dédommagées ayant abouti sont confirmées dans l'ordre inverse d'achèvement.</span><span class="sxs-lookup"><span data-stu-id="121d8-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="121d8-184">Dans cet exemple le vol est réservé, acheté et finalisé, puis, l'activité compensable est confirmée.</span><span class="sxs-lookup"><span data-stu-id="121d8-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="121d8-185">Pour confirmer un <xref:System.Activities.Statements.CompensableActivity>, utilisez l'activité <xref:System.Activities.Statements.Confirm> et spécifiez le <xref:System.Activities.Statements.CompensationToken> du <xref:System.Activities.Statements.CompensableActivity> à confirmer.</span><span class="sxs-lookup"><span data-stu-id="121d8-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="121d8-186">Cet exemple est le workflow en XAML.</span><span class="sxs-lookup"><span data-stu-id="121d8-186">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="121d8-187">Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="121d8-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="121d8-188">**ReserveFlight Le ticket est réservé.**</span><span class="sxs-lookup"><span data-stu-id="121d8-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="121d8-189">**ManagerApproval Approbation du gestionnaire reçue.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="121d8-190">**PurchaseFlight Le ticket est acheté.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="121d8-191">**TakeFlight Le vol est terminé.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="121d8-192">**ConfirmFlight Le vol a été pris, aucune compensation possible.**  </span><span class="sxs-lookup"><span data-stu-id="121d8-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="121d8-193">**Le workflow s’est terminé avec succès avec l’État: Légendes.**</span><span class="sxs-lookup"><span data-stu-id="121d8-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="121d8-194">Imbrication d'activités de compensation</span><span class="sxs-lookup"><span data-stu-id="121d8-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="121d8-195">Un <xref:System.Activities.Statements.CompensableActivity> peut être placé dans la section <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un autre <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="121d8-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="121d8-196"><xref:System.Activities.Statements.CompensableActivity> ne peut pas être placé dans un gestionnaire d'un autre <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="121d8-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="121d8-197">Il est de la responsabilité d'un <xref:System.Activities.Statements.CompensableActivity> parent de garantir que lorsqu'il est annulé, confirmé, ou compensé, toutes les activités enfants compensables terminées avec succès et qui n'ont pas encore été confirmées ou compensées doivent être confirmées ou compensées avant que le parent complète l'annulation, la confirmation ou la compensation.</span><span class="sxs-lookup"><span data-stu-id="121d8-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="121d8-198">Si cela n'est pas modélisé explicitement, le <xref:System.Activities.Statements.CompensableActivity> parent compensera implicitement les activités compensables enfants si le parent a reçu le signal d'annulation ou de compensation.</span><span class="sxs-lookup"><span data-stu-id="121d8-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="121d8-199">Si le parent a reçu le signal de confirmation, il confirme implicitement les activités compensables enfants.</span><span class="sxs-lookup"><span data-stu-id="121d8-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="121d8-200">Si la logique pour gérer l'annulation, la confirmation ou la compensation est explicitement modélisée dans le gestionnaire du <xref:System.Activities.Statements.CompensableActivity>parent, les enfants qui ne sont pas gérés explicitement seront confirmés implicitement.</span><span class="sxs-lookup"><span data-stu-id="121d8-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="121d8-201">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="121d8-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
