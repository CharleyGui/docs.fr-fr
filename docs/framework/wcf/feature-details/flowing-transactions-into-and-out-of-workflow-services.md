---
title: Flux de transactions vers et depuis des services de workflow
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: db1a1ef6bcf3f048584b39450c90fac3ff35646b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893374"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="55e69-102">Flux de transactions vers et depuis des services de workflow</span><span class="sxs-lookup"><span data-stu-id="55e69-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="55e69-103">Les services et clients de workflow peuvent participer aux transactions.</span><span class="sxs-lookup"><span data-stu-id="55e69-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="55e69-104">Pour qu'une opération de service fasse partie d'une transaction ambiante, placez une activité <xref:System.ServiceModel.Activities.Receive> dans une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="55e69-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="55e69-105">Tous les appels effectués par une activité <xref:System.ServiceModel.Activities.Send> ou <xref:System.ServiceModel.Activities.SendReply> au sein de l’activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> seront également effectués dans la transaction ambiante.</span><span class="sxs-lookup"><span data-stu-id="55e69-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="55e69-106">Une application cliente de workflow peut créer une transaction ambiante en utilisant l’activité <xref:System.Activities.Statements.TransactionScope> et appeler des opérations de service à l’aide de la transaction ambiante.</span><span class="sxs-lookup"><span data-stu-id="55e69-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="55e69-107">Cette rubrique vous guide dans la création d’un service de workflow et d’un client de workflow qui participent à des transactions.</span><span class="sxs-lookup"><span data-stu-id="55e69-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="55e69-108">Si une instance de service de workflow est chargée dans une transaction et que le <xref:System.Activities.Statements.Persist> Workflow contient une activité, l’instance de workflow est bloquée jusqu’à ce que la transaction expire.</span><span class="sxs-lookup"><span data-stu-id="55e69-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="55e69-109">Lorsque vous utilisez une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>, il est recommandé de placer toutes les réceptions dans le workflow dans les activités <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="55e69-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="55e69-110">Lorsque vous utilisez <xref:System.ServiceModel.Activities.TransactedReceiveScope> et les messages arrivent dans le mauvais ordre incorrect, le workflow est abandonné lorsque vous tentez de livrer le premier message dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="55e69-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="55e69-111">Vous devez vous assurer que votre workflow est toujours à un point d'arrêt cohérent lorsqu'il est inactif.</span><span class="sxs-lookup"><span data-stu-id="55e69-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="55e69-112">Cela vous permet de redémarrer le workflow à partir d'un point de persistance précédent s'il est abandonné.</span><span class="sxs-lookup"><span data-stu-id="55e69-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="55e69-113">Créer une bibliothèque partagée</span><span class="sxs-lookup"><span data-stu-id="55e69-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="55e69-114">Créez une solution Visual Studio vide.</span><span class="sxs-lookup"><span data-stu-id="55e69-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="55e69-115">Ajoutez un nouveau projet de bibliothèque de classes nommé `Common`.</span><span class="sxs-lookup"><span data-stu-id="55e69-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="55e69-116">Ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="55e69-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="55e69-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="55e69-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="55e69-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="55e69-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="55e69-121">Ajoutez une nouvelle classe nommée `PrintTransactionInfo` au projet `Common`.</span><span class="sxs-lookup"><span data-stu-id="55e69-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="55e69-122">Cette classe est dérivée de <xref:System.Activities.NativeActivity> et surcharge la méthode <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="55e69-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="55e69-123">Il s’agit d’une activité native qui affiche des informations sur la transaction ambiante et est utilisée dans les workflows du service et du client utilisés dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="55e69-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="55e69-124">Générez la solution pour rendre cette activité disponible dans la section **commune** de la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="55e69-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="55e69-125">Implémenter le service de workflow</span><span class="sxs-lookup"><span data-stu-id="55e69-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="55e69-126">Ajoutez un nouveau service de flux de travail `WorkflowService` WCF, `Common` appelé au projet.</span><span class="sxs-lookup"><span data-stu-id="55e69-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="55e69-127">Pour ce faire, cliquez avec `Common` le bouton droit sur le projet, sélectionnez **Ajouter**, **nouvel élément...** , sélectionnez **Workflow** sous **modèles installés** , puis sélectionnez **service de flux de travail WCF**.</span><span class="sxs-lookup"><span data-stu-id="55e69-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Ajout d'un service de flux de travail](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="55e69-129">Supprimez les activités par défaut `ReceiveRequest` et `SendResponse`.</span><span class="sxs-lookup"><span data-stu-id="55e69-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="55e69-130">Faites glisser et déposez une activité <xref:System.Activities.Statements.WriteLine> dans l’activité `Sequential Service`.</span><span class="sxs-lookup"><span data-stu-id="55e69-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="55e69-131">Affectez à la propriété Text la valeur `"Workflow Service starting ..."`, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="55e69-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="55e69-132">! [Ajout d’une activité WriteLine à l’activité de service séquentielle (./Media/Flowing-transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="55e69-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="55e69-133">Faites glisser et déposez une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> après l’activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="55e69-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="55e69-134">L' <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité se trouve dans la section **messagerie** de la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="55e69-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="55e69-135">L' <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité est composée de deux sections **Request** et **Body**.</span><span class="sxs-lookup"><span data-stu-id="55e69-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="55e69-136">La section de la requête <xref:System.ServiceModel.Activities.Receive> contient l’activité.</span><span class="sxs-lookup"><span data-stu-id="55e69-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="55e69-137">La section **Body** contient les activités à exécuter dans une transaction après réception d’un message.</span><span class="sxs-lookup"><span data-stu-id="55e69-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Ajout d'une activité TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="55e69-139">Sélectionnez l' <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité et cliquez sur le bouton **variables** .</span><span class="sxs-lookup"><span data-stu-id="55e69-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="55e69-140">Ajoutez les variables suivantes.</span><span class="sxs-lookup"><span data-stu-id="55e69-140">Add the following variables.</span></span>  
  
     ![Ajout de variables à TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="55e69-142">Vous pouvez supprimer la variable de données proposée à cet endroit par défaut.</span><span class="sxs-lookup"><span data-stu-id="55e69-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="55e69-143">Vous pouvez également utiliser la variable de handle existante.</span><span class="sxs-lookup"><span data-stu-id="55e69-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="55e69-144">Faites glisser et déposez une <xref:System.ServiceModel.Activities.Receive> activité dans la section <xref:System.ServiceModel.Activities.TransactedReceiveScope> **requête** de l’activité.</span><span class="sxs-lookup"><span data-stu-id="55e69-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="55e69-145">Définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="55e69-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="55e69-146">Propriété</span><span class="sxs-lookup"><span data-stu-id="55e69-146">Property</span></span>|<span data-ttu-id="55e69-147">Valeur</span><span class="sxs-lookup"><span data-stu-id="55e69-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55e69-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="55e69-148">CanCreateInstance</span></span>|<span data-ttu-id="55e69-149">True (activez la case à cocher)</span><span class="sxs-lookup"><span data-stu-id="55e69-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="55e69-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="55e69-150">OperationName</span></span>|<span data-ttu-id="55e69-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="55e69-151">StartSample</span></span>|  
    |<span data-ttu-id="55e69-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="55e69-152">ServiceContractName</span></span>|<span data-ttu-id="55e69-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="55e69-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="55e69-154">Le workflow doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-154">The workflow should look like this:</span></span>  
  
     ![Ajout d'une activité Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="55e69-156">Cliquez sur le lien **définir...** dans <xref:System.ServiceModel.Activities.Receive> l’activité et définissez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="55e69-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Définition des paramètres de message pour l’activité Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="55e69-158">Faites glisser et déposez une activité <xref:System.Activities.Statements.Sequence> dans la section de corps du <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="55e69-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="55e69-159">Dans l’activité <xref:System.Activities.Statements.Sequence>, faites glisser et déposez deux activités <xref:System.Activities.Statements.WriteLine> et définissez les propriétés <xref:System.Activities.Statements.WriteLine.Text%2A> conformément aux indications du tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="55e69-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="55e69-160">Activité</span><span class="sxs-lookup"><span data-stu-id="55e69-160">Activity</span></span>|<span data-ttu-id="55e69-161">Valeur</span><span class="sxs-lookup"><span data-stu-id="55e69-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55e69-162">1re WriteLine</span><span class="sxs-lookup"><span data-stu-id="55e69-162">1st WriteLine</span></span>|<span data-ttu-id="55e69-163">Services Réception terminée»</span><span class="sxs-lookup"><span data-stu-id="55e69-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="55e69-164">2e WriteLine</span><span class="sxs-lookup"><span data-stu-id="55e69-164">2nd WriteLine</span></span>|<span data-ttu-id="55e69-165">Services Received = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="55e69-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="55e69-166">Le workflow doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-166">The workflow should now look like this:</span></span>  
  
     ![Séquence après l’ajout d’activités WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="55e69-168">Faites glisser et déposez l' `PrintTransactionInfo` activité après la deuxième <xref:System.ServiceModel.Activities.TransactedReceiveScope> <xref:System.Activities.Statements.WriteLine> activité dans le corps de l’activité.</span><span class="sxs-lookup"><span data-stu-id="55e69-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Séquence après l’ajout de PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="55e69-170">Faites glisser et déposez une activité <xref:System.Activities.Statements.Assign> après l’activité `PrintTransactionInfo` et définissez ses propriétés conformément aux indications du tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="55e69-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="55e69-171">Propriété</span><span class="sxs-lookup"><span data-stu-id="55e69-171">Property</span></span>|<span data-ttu-id="55e69-172">Valeur</span><span class="sxs-lookup"><span data-stu-id="55e69-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55e69-173">À</span><span class="sxs-lookup"><span data-stu-id="55e69-173">To</span></span>|<span data-ttu-id="55e69-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="55e69-174">replyMessage</span></span>|  
    |<span data-ttu-id="55e69-175">Valeur</span><span class="sxs-lookup"><span data-stu-id="55e69-175">Value</span></span>|<span data-ttu-id="55e69-176">Services Envoi de la réponse».</span><span class="sxs-lookup"><span data-stu-id="55e69-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="55e69-177">Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité après l’activité <xref:System.Activities.Statements.WriteLine.Text%2A> et affectez à sa propriété la <xref:System.Activities.Statements.Assign> valeur «service : BEGIN reply».</span><span class="sxs-lookup"><span data-stu-id="55e69-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="55e69-178">Le workflow doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-178">The workflow should now look like this:</span></span>  
  
     ![Après l'ajout de Assign et de WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="55e69-180">Cliquez avec le <xref:System.ServiceModel.Activities.Receive> bouton droit sur l’activité, puis sélectionnez **Create SendReply** et collez-la après la dernière <xref:System.Activities.Statements.WriteLine> activité.</span><span class="sxs-lookup"><span data-stu-id="55e69-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="55e69-181">Cliquez sur le lien **définir...** dans `SendReplyToReceive` l’activité et définissez les paramètres suivants.</span><span class="sxs-lookup"><span data-stu-id="55e69-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Paramètres des messages Reply](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="55e69-183">Faites glisser et déposez <xref:System.Activities.Statements.WriteLine> une `SendReplyToReceive` activité après l' <xref:System.Activities.Statements.WriteLine.Text%2A> activité et affectez à sa propriété la valeur "service : Réponse envoyée».</span><span class="sxs-lookup"><span data-stu-id="55e69-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="55e69-184">Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité en bas du workflow et affectez à sa <xref:System.Activities.Statements.WriteLine.Text%2A> propriété la valeur «service : Le flux de travail se termine, appuyez sur entrée pour quitter.»</span><span class="sxs-lookup"><span data-stu-id="55e69-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="55e69-185">Le workflow de service terminé doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-185">The completed service workflow should look like this:</span></span>  
  
     ![Flux de travail du service complet](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="55e69-187">Implémenter le client de workflow</span><span class="sxs-lookup"><span data-stu-id="55e69-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="55e69-188">Ajoutez une nouvelle application de workflow WCF nommée `WorkflowClient` au projet `Common`.</span><span class="sxs-lookup"><span data-stu-id="55e69-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="55e69-189">Pour ce faire, cliquez avec `Common` le bouton droit sur le projet, sélectionnez **Ajouter**, **nouvel élément...** , sélectionnez **Workflow** sous **modèles installés** , puis sélectionnez **activité**.</span><span class="sxs-lookup"><span data-stu-id="55e69-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Ajouter un projet d'activité](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="55e69-191">Faites glisser et déposez une activité <xref:System.Activities.Statements.Sequence> sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="55e69-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="55e69-192">Dans l’activité <xref:System.Activities.Statements.Sequence>, faites glisser et déposez une activité <xref:System.Activities.Statements.WriteLine> et affectez à sa propriété <xref:System.Activities.Statements.WriteLine.Text%2A> la valeur `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="55e69-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="55e69-193">Le workflow doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-193">The workflow should now look like this:</span></span>  
  
     ![Ajouter une activité WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="55e69-195">Faites glisser une activité <xref:System.Activities.Statements.TransactionScope> après l'activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="55e69-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="55e69-196">Sélectionnez l'activité <xref:System.Activities.Statements.TransactionScope>, cliquez sur le bouton Variables et ajoutez les variables suivantes.</span><span class="sxs-lookup"><span data-stu-id="55e69-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Ajouter des variables à TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="55e69-198">Faites glisser et déposez une activité <xref:System.Activities.Statements.Sequence> dans le corps de l’activité <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="55e69-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="55e69-199">Faites glisser une activité `PrintTransactionInfo` dans <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="55e69-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="55e69-200">Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité après l’activité <xref:System.Activities.Statements.WriteLine.Text%2A> et affectez à sa propriété la `PrintTransactionInfo` valeur «client : Début de l’envoi».</span><span class="sxs-lookup"><span data-stu-id="55e69-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="55e69-201">Le workflow doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-201">The workflow should now look like this:</span></span>  
  
     ![Ajout du client : Début des activités d’envoi](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="55e69-203">Faites glisser une activité <xref:System.ServiceModel.Activities.Send> après l'activité <xref:System.Activities.Statements.Assign> et définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="55e69-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="55e69-204">Propriété</span><span class="sxs-lookup"><span data-stu-id="55e69-204">Property</span></span>|<span data-ttu-id="55e69-205">Valeur</span><span class="sxs-lookup"><span data-stu-id="55e69-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55e69-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="55e69-206">EndpointConfigurationName</span></span>|<span data-ttu-id="55e69-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="55e69-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="55e69-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="55e69-208">OperationName</span></span>|<span data-ttu-id="55e69-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="55e69-209">StartSample</span></span>|  
    |<span data-ttu-id="55e69-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="55e69-210">ServiceContractName</span></span>|<span data-ttu-id="55e69-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="55e69-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="55e69-212">Le workflow doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="55e69-212">The workflow should now look like this:</span></span>  
  
     ![Définition des propriétés de l'activité Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="55e69-214">Cliquez sur le lien **définir...** et définissez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="55e69-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Paramètres des messages de l'activité Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="55e69-216">Cliquez avec le <xref:System.ServiceModel.Activities.Send> bouton droit sur l’activité, puis sélectionnez **créer ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="55e69-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="55e69-217">L'activité <xref:System.ServiceModel.Activities.ReceiveReply> sera automatiquement placée après l'activité <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="55e69-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="55e69-218">Cliquez sur le lien Définir de l'activité ReceiveReplyForSend et effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="55e69-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Définition des paramètres de message ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="55e69-220">Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité <xref:System.ServiceModel.Activities.ReceiveReply> entre les activités et <xref:System.Activities.Statements.WriteLine.Text%2A> et affectez à sa propriété la <xref:System.ServiceModel.Activities.Send> valeur «client : Envoi terminé».</span><span class="sxs-lookup"><span data-stu-id="55e69-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="55e69-221">Faites glisser et déposez <xref:System.Activities.Statements.WriteLine> une <xref:System.ServiceModel.Activities.ReceiveReply> activité après l’activité <xref:System.Activities.Statements.WriteLine.Text%2A> et définissez sa propriété sur «côté client : Reply received = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="55e69-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="55e69-222">Faites glisser une activité `PrintTransactionInfo` après l'activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="55e69-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="55e69-223">Faites glisser une activité <xref:System.Activities.Statements.WriteLine> à la fin du workflow et affectez à sa propriété <xref:System.Activities.Statements.WriteLine.Text%2A> la valeur "Client workflow ends."</span><span class="sxs-lookup"><span data-stu-id="55e69-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="55e69-224">Le workflow du client terminé doit ressembler au diagramme suivant.</span><span class="sxs-lookup"><span data-stu-id="55e69-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Workflow client terminé](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="55e69-226">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="55e69-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="55e69-227">Créer l'application Service</span><span class="sxs-lookup"><span data-stu-id="55e69-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="55e69-228">Ajoutez à la solution un nouveau projet d'application console nommé `Service`.</span><span class="sxs-lookup"><span data-stu-id="55e69-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="55e69-229">Ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="55e69-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="55e69-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="55e69-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="55e69-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="55e69-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="55e69-233">Ouvrez le fichier Program.cs généré et le code suivant :</span><span class="sxs-lookup"><span data-stu-id="55e69-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3. <span data-ttu-id="55e69-234">Ajoutez le fichier app.config suivant au projet.</span><span class="sxs-lookup"><span data-stu-id="55e69-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="55e69-235">Créer l'application Client</span><span class="sxs-lookup"><span data-stu-id="55e69-235">Create the client application</span></span>  
  
1. <span data-ttu-id="55e69-236">Ajoutez à la solution un nouveau projet d'application console nommé `Client`.</span><span class="sxs-lookup"><span data-stu-id="55e69-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="55e69-237">Ajoutez une référence à System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="55e69-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="55e69-238">Ouvrez le fichier program.cs et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="55e69-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
        class Program  
        {  
  
            private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
            static void Main(string[] args)  
            {  
                //Build client  
                Console.WriteLine("Building the client.");  
                WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
                client.Completed = Program.Completed;  
                client.Aborted = Program.Aborted;  
                client.OnUnhandledException = Program.OnUnhandledException;  
  
                //Wait for service to start  
                Console.WriteLine("Press ENTER once service is started.");  
                Console.ReadLine();  
  
                //Start the client              
                Console.WriteLine("Starting the client.");  
                client.Run();  
                syncEvent.WaitOne();  
  
                //Sample complete  
                Console.WriteLine();  
                Console.WriteLine("Client complete. Press ENTER to exit.");  
                Console.ReadLine();  
            }  
  
            private static void Completed(WorkflowApplicationCompletedEventArgs e)  
            {  
                Program.syncEvent.Set();  
            }  
  
            private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
            {  
                Console.WriteLine("Client Aborted: {0}", e.Reason);  
                Program.syncEvent.Set();  
            }  
  
            private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
            {  
                Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
                return UnhandledExceptionAction.Cancel;  
            }  
        }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="55e69-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55e69-239">See also</span></span>

- [<span data-ttu-id="55e69-240">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="55e69-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="55e69-241">Vue d’ensemble des transactions Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="55e69-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
