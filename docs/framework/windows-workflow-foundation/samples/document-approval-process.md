---
title: Processus d'approbation des documents
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 20167cd1c06c2ae57dfe48fd07ab3a0e2adf9927
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038224"
---
# <a name="document-approval-process"></a><span data-ttu-id="dd9a5-102">Processus d'approbation des documents</span><span class="sxs-lookup"><span data-stu-id="dd9a5-102">Document Approval Process</span></span>

<span data-ttu-id="dd9a5-103">Cet exemple illustre l’utilisation conjointe de nombreuses fonctionnalités de Windows Workflow Foundation (WF) et Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dd9a5-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="dd9a5-104">Ensemble, elles implémentent un scénario de processus d'approbation des documents.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="dd9a5-105">Une application cliente peut soumettre des documents pour approbation et approuver des documents.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="dd9a5-106">Une application du responsable des approbations existe pour faciliter les communications entre les clients et mettre en vigueur les règles du processus d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="dd9a5-107">Le processus d'approbation est un workflow qui peut exécuter plusieurs types d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="dd9a5-108">Il existe des activités pour obtenir une approbation unique, une approbation de quorum (pourcentage de l'ensemble d'approbateurs) et un processus d'approbation complexe qui se compose d'une approbation unique et de quorum dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd9a5-109">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dd9a5-110">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-110">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="dd9a5-111">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dd9a5-112">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-112">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="dd9a5-113">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="dd9a5-113">Sample Details</span></span>

<span data-ttu-id="dd9a5-114">L’illustration suivante montre le flux de travail du processus d’approbation des documents:</span><span class="sxs-lookup"><span data-stu-id="dd9a5-114">The following graphic demonstrates the document approval process workflow:</span></span>

![Flux de travail du processus d'approbation d'un document](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="dd9a5-116">Du point de vue du client, le processus d'approbation fonctionne comme suit :</span><span class="sxs-lookup"><span data-stu-id="dd9a5-116">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="dd9a5-117">Un client s'abonne pour être un utilisateur dans le système du processus d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-117">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="dd9a5-118">Un client WCF envoie à un service WCF hébergé par l’application du responsable des approbations.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="dd9a5-119">Un ID d'utilisateur unique est retourné au client.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="dd9a5-120">Le client peut maintenant participer aux processus d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-120">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="dd9a5-121">Une fois joint, un client peut envoyer un document pour approbation à l'aide de processus d'approbation unique, de quorum ou complexe.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="dd9a5-122">Un clic sur un bouton dans l'interface du client permet de démarrer une instance de workflow dans un hôte du service de workflow client.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="dd9a5-123">Le workflow envoie une demande d'approbation à l'application du responsable des approbations.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-123">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="dd9a5-124">Le gestionnaire de workflow démarre un workflow de son propre côté pour représenter un processus d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="dd9a5-125">Une fois le workflow d'approbation du responsable exécuté, les résultats sont renvoyés au client.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="dd9a5-126">Le client affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-126">The client displays the results.</span></span>

10. <span data-ttu-id="dd9a5-127">Un client peut recevoir une demande d'approbation et y répondre à tout moment.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-127">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="dd9a5-128">Un service WCF hébergé sur le client peut recevoir une demande d’approbation de l’application du responsable des approbations.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="dd9a5-129">Les informations concernant les documents sont présentées sur le client à des fins de revue.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-129">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="dd9a5-130">L'utilisateur peut approuver ou rejeter le document.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-130">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="dd9a5-131">Un client WCF est utilisé pour renvoyer une réponse d’approbation à l’application du responsable des approbations.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="dd9a5-132">Du point de vue de l'application du responsable des approbations, le processus d'approbation fonctionne comme suit :</span><span class="sxs-lookup"><span data-stu-id="dd9a5-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="dd9a5-133">Un client demande à participer au système du processus d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-133">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="dd9a5-134">Un service WCF sur le gestionnaire d’approbations reçoit une demande pour faire partie du système de processus d’approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="dd9a5-135">Un ID unique est généré pour le client.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="dd9a5-136">Les informations utilisateur sont stockées dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-136">The user information is stored in a database.</span></span>

4. <span data-ttu-id="dd9a5-137">L'ID unique est renvoyé à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-137">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="dd9a5-138">Une demande d'approbation est reçue.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-138">An approval request is receive.</span></span> <span data-ttu-id="dd9a5-139">Le responsable des approbations exécute un processus d'approbation.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-139">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="dd9a5-140">Une demande d'approbation est reçue par le responsable des approbations, ce qui démarre un nouveau workflow.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-140">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="dd9a5-141">Selon le type de demande (simple, quorum ou complexe), une activité différente est exécutée.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="dd9a5-142">Les activités Send et Receive avec corrélation sont utilisées pour envoyer la demande d’approbation au client à des fins de revue et pour recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="dd9a5-143">Le résultat du workflow de processus d'approbation est envoyé au client.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-143">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="dd9a5-144">Utilisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="dd9a5-144">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="dd9a5-145">Pour configurer la base de données</span><span class="sxs-lookup"><span data-stu-id="dd9a5-145">To set up the database</span></span>

1. <span data-ttu-id="dd9a5-146">À partir d’une invite de commandes de Visual Studio 2010 ouverte avec des privilèges d’administrateur, accédez à ce dossier DocumentApprovalProcess et exécutez Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="dd9a5-147">Pour configurer l'application</span><span class="sxs-lookup"><span data-stu-id="dd9a5-147">To set up the application</span></span>

1. <span data-ttu-id="dd9a5-148">À l’aide de Visual Studio 2010, ouvrez le fichier solution DocumentApprovalProcess. sln.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="dd9a5-149">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="dd9a5-150">Pour exécuter la solution, lancez l’application du responsable des approbations en cliquant avec le bouton droit sur le projet->ApprovalManager dans le **Explorateur de solutions** puis en cliquant sur déboguer**Démarrer** une nouvelle instance dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="dd9a5-151">Attendez que la sortie du responsable vous indique qu'il est prêt.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-151">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="dd9a5-152">Pour exécuter le scénario avec approbation unique</span><span class="sxs-lookup"><span data-stu-id="dd9a5-152">To run the single approval scenario</span></span>

1. <span data-ttu-id="dd9a5-153">Ouvrez une invite de commandes avec l'autorisation d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-153">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="dd9a5-154">Naviguez jusqu'au répertoire qui contient la solution.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-154">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="dd9a5-155">Naviguez jusqu’au dossier ApprovalClient\Bin\Debug et exécutez deux instances d’ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="dd9a5-156">Cliquez sur **découvrir**, attendez jusqu’à ce que le bouton **s’abonner** soit activé.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="dd9a5-157">Tapez un nom d’utilisateur et cliquez sur **s’abonner**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="dd9a5-158">Pour un client, utilisez `UserType1` et pour l'autre, tapez `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="dd9a5-159">Dans le client `UserType1`, sélectionnez le type d’approbation unique dans le menu déroulant et tapez un nom de document ainsi qu’un contenu.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="dd9a5-160">Cliquez sur **demander une approbation**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-160">Click **Request Approval**.</span></span>

7. <span data-ttu-id="dd9a5-161">Dans le client `UserType2`, un document en attente d'approbation apparaît.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="dd9a5-162">Sélectionnez-le et appuyez sur **approuver** ou **rejeter**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="dd9a5-163">Les résultats doivent s'afficher dans le client `UserType1`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-163">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="dd9a5-164">Pour exécuter le scénario avec approbation de quorum</span><span class="sxs-lookup"><span data-stu-id="dd9a5-164">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="dd9a5-165">Ouvrez une invite de commandes avec l'autorisation d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-165">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="dd9a5-166">Naviguez jusqu'au répertoire qui contient la solution.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-166">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="dd9a5-167">Naviguez jusqu’au dossier ApprovalClient\Bin\Debug et exécutez trois instances d’ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="dd9a5-168">Cliquez sur **découvrir**, attendez jusqu’à ce que le bouton **s’abonner** soit activé.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="dd9a5-169">Tapez un nom d’utilisateur et cliquez sur **s’abonner**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="dd9a5-170">Pour un client, utilisez `UserType1` et pour les deux autres, tapez `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="dd9a5-171">Dans le client `UserType1`, sélectionnez le type d’approbation de quorum dans le menu déroulant et tapez un nom de document ainsi qu’un contenu.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="dd9a5-172">Cliquez sur **demander une approbation**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-172">Click **Request Approval**.</span></span> <span data-ttu-id="dd9a5-173">Ceci nécessite que les deux clients `UserType2` approuvent ou rejettent le document.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="dd9a5-174">Alors que les deux clients `UserType2` doivent répondre, un seul client doit approuver le document pour qu'il le soit.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="dd9a5-175">Dans les clients `UserType2`, un document en attente d'approbation apparaît.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="dd9a5-176">Sélectionnez-le et appuyez sur **approuver** ou **rejeter**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="dd9a5-177">Les résultats doivent s'afficher dans le client `UserType1`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-177">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="dd9a5-178">Pour exécuter le scénario avec approbation complexe</span><span class="sxs-lookup"><span data-stu-id="dd9a5-178">To run the complex approval scenario</span></span>

1. <span data-ttu-id="dd9a5-179">Ouvrez une invite de commandes avec l'autorisation d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-179">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="dd9a5-180">Naviguez jusqu'au répertoire qui contient la solution.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-180">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="dd9a5-181">Naviguez jusqu'au dossier ApprovalClient\Bin\Debug et exécutez quatre instances d'ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="dd9a5-182">Cliquez sur **découvrir**, attendez jusqu’à ce que le bouton **s’abonner** soit activé.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="dd9a5-183">Tapez un nom d’utilisateur et cliquez sur **s’abonner**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="dd9a5-184">Pour un client, utilisez `UserType1`, pour deux utilisations, tapez `UserType2` et, pour le dernier, utilisez `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="dd9a5-185">Dans le client `UserType1`, sélectionnez le type d’approbation unique dans le menu déroulant et tapez un nom de document ainsi qu’un contenu.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="dd9a5-186">Cliquez sur **demander une approbation**.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-186">Click **Request Approval**.</span></span>

7. <span data-ttu-id="dd9a5-187">Dans les clients `UserType2`, un document en attente d'approbation apparaît.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="dd9a5-188">Sélectionnez-le et appuyez sur **approuver**, le document est transmis `UserType3` au client.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="dd9a5-189">Si le document est approuvé par le premier quorum `UserType2`, le document est passé au client `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="dd9a5-190">Approuvez ou rejetez le document du client `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="dd9a5-191">Les résultats doivent s'afficher dans le client `UserType1`.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-191">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="dd9a5-192">Pour nettoyer</span><span class="sxs-lookup"><span data-stu-id="dd9a5-192">To clean up</span></span>

1. <span data-ttu-id="dd9a5-193">À partir d’une invite de commandes Visual Studio 2010, accédez au dossier DocumentApprovalProcess et exécutez Cleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="dd9a5-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
