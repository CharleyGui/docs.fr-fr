---
title: WCF Services et suivi d'événements Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: e1ee7154e2ad5b22ff0debcdd15d5809fc55df13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044518"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="7d7ad-102">WCF Services et suivi d'événements Windows</span><span class="sxs-lookup"><span data-stu-id="7d7ad-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="7d7ad-103">Cet exemple montre comment utiliser le traçage analytique dans Windows Communication Foundation (WCF) pour émettre des événements dans Suivi d’v nements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="7d7ad-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="7d7ad-104">Les traces analytiques sont des événements émis à des points clés dans la pile WCF qui permettent de résoudre les problèmes des services WCF dans l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="7d7ad-105">Le suivi analytique dans les services WCF est le suivi qui peut être activé dans un environnement de production avec un impact minimal sur les performances.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="7d7ad-106">Ces traces sont émises en tant qu'événements dans une session de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="7d7ad-107">Cet exemple comprend un service WCF de base dans lequel les événements sont émis à partir du service dans le journal des événements, qui peut être affiché à l’aide de observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="7d7ad-108">Il est également possible de démarrer une session ETW dédiée qui écoute les événements du service WCF.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="7d7ad-109">L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="7d7ad-110">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="7d7ad-110">To use this sample</span></span>

1. <span data-ttu-id="7d7ad-111">À l’aide de Visual Studio 2012, ouvrez le fichier solution EtwAnalyticTraceSample. sln.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="7d7ad-112">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="7d7ad-113">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="7d7ad-114">Dans le navigateur Web, cliquez sur **Calculator. svc**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="7d7ad-115">L'URI du document WSDL du service doit s'afficher dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="7d7ad-116">Copiez cet URI.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-116">Copy that URI.</span></span>

     <span data-ttu-id="7d7ad-117">Par défaut, le service commence à écouter les demandes sur le `http://localhost:1378/Calculator.svc`port 1378.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="7d7ad-118">Exécutez le client test WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="7d7ad-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="7d7ad-119">Le client test WCF (WcfTestClient. exe) se trouve à `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="7d7ad-120">Le répertoire d’installation par défaut de Visual `C:\Program Files\Microsoft Visual Studio 10.0`Studio 2012 est.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="7d7ad-121">Dans le client test WCF, ajoutez le service en sélectionnant **fichier**, puis **Ajouter un service**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="7d7ad-122">Ajoutez l'adresse du point de terminaison dans la zone d'entrée.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="7d7ad-123">Par défaut, il s’agit de `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="7d7ad-124">Ouvrez l'application Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="7d7ad-125">Avant d’appeler le service, démarrez observateur d’événements et assurez-vous que le journal des événements écoute les événements de suivi émis à partir du service WCF.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="7d7ad-126">Dans le menu **Démarrer** , sélectionnez **Outils d’administration**, puis **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="7d7ad-127">Activez les journaux d' **analyse** et de débogage.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="7d7ad-128">Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="7d7ad-129">Cliquez avec le bouton droit sur **serveur d’applications-applications**, sélectionnez **affichage**, puis affichez les **journaux d’analyse et de débogage**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="7d7ad-130">Assurez-vous que l’option **afficher les journaux d’analyse et de débogage** est activée.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="7d7ad-131">Activez le journal d' **analyse** .</span><span class="sxs-lookup"><span data-stu-id="7d7ad-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="7d7ad-132">Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="7d7ad-133">Cliquez avec le bouton droit sur **analyse** et sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="7d7ad-134">Pour tester le service</span><span class="sxs-lookup"><span data-stu-id="7d7ad-134">To test the service</span></span>

1. <span data-ttu-id="7d7ad-135">Revenez au client test WCF, double-cliquez `Divide` sur et conservez les valeurs par défaut, qui spécifient un dénominateur de 0.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="7d7ad-136">Si le dénominateur est 0, le service génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="7d7ad-137">Observez les événements émis par le service.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="7d7ad-138">Revenez à observateur d’événements et accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="7d7ad-139">Cliquez avec le bouton droit sur **analyse** , puis sélectionnez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="7d7ad-140">Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="7d7ad-141">Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="7d7ad-142">Répétez les étapes 1 et 2, mais avec des entrées valides.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="7d7ad-143">La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="7d7ad-144">Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="7d7ad-145">L'exemple montre les événements de trace analytique émis par un service WCF.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="7d7ad-146">Pour effectuer un nettoyage (facultatif)</span><span class="sxs-lookup"><span data-stu-id="7d7ad-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="7d7ad-147">Ouvrez l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="7d7ad-148">Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis **application-serveur-applications**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="7d7ad-149">Cliquez avec le bouton droit sur **analyse** et sélectionnez **désactiver le journal**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="7d7ad-150">Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis **application-serveur-applications**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="7d7ad-151">Cliquez avec le bouton droit sur **analyse** et sélectionnez **effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="7d7ad-152">Choisissez l’option **Effacer** pour effacer les événements.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d7ad-153">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7d7ad-154">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-154">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7d7ad-155">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d7ad-156">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="7d7ad-156">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="7d7ad-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d7ad-157">See also</span></span>

- [<span data-ttu-id="7d7ad-158">Exemples de surveillance AppFabric</span><span class="sxs-lookup"><span data-stu-id="7d7ad-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
