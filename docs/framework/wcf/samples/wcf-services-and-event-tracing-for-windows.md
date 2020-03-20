---
title: WCF Services et suivi d'événements Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183213"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="177b2-102">WCF Services et suivi d'événements Windows</span><span class="sxs-lookup"><span data-stu-id="177b2-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="177b2-103">Cet exemple montre comment utiliser le tracé analytique dans Windows Communication Foundation (WCF) pour émettre des événements dans Event Tracing for Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="177b2-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="177b2-104">Les traces analytiques sont des événements émis à des points clés de la pile WCF qui permettent le dépannage des services WCF dans l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="177b2-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="177b2-105">La trace analytique dans les services WCF est le traçage qui peut être activé dans un environnement de production avec un impact minimal sur les performances.</span><span class="sxs-lookup"><span data-stu-id="177b2-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="177b2-106">Ces traces sont émises en tant qu'événements dans une session de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="177b2-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="177b2-107">Cet exemple comprend un service WCF de base dans lequel les événements sont émis du service au journal de l’événement, qui peut être consulté à l’aide de Event Viewer.</span><span class="sxs-lookup"><span data-stu-id="177b2-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="177b2-108">Il est également possible de commencer une session ETW dédiée qui écoute les événements du service WCF.</span><span class="sxs-lookup"><span data-stu-id="177b2-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="177b2-109">L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="177b2-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="177b2-110">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="177b2-110">To use this sample</span></span>

1. <span data-ttu-id="177b2-111">À l’aide de Visual Studio 2012, ouvrez le fichier de solution EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="177b2-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="177b2-112">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="177b2-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="177b2-113">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="177b2-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="177b2-114">Dans le navigateur Web, cliquez sur **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="177b2-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="177b2-115">L'URI du document WSDL du service doit s'afficher dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="177b2-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="177b2-116">Copiez cet URI.</span><span class="sxs-lookup"><span data-stu-id="177b2-116">Copy that URI.</span></span>

     <span data-ttu-id="177b2-117">Par défaut, le service commence à écouter les `http://localhost:1378/Calculator.svc`demandes sur le port 1378 .</span><span class="sxs-lookup"><span data-stu-id="177b2-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="177b2-118">Exécuter le client de test WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="177b2-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="177b2-119">Le client de test WCF (WcfTestClient.exe) est situé à `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="177b2-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="177b2-120">Le par défaut Visual Studio 2012 installer dir est `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="177b2-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="177b2-121">Au sein du client de test WCF, ajoutez le service en sélectionnant **Le fichier,** puis **ajoutez le service**.</span><span class="sxs-lookup"><span data-stu-id="177b2-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="177b2-122">Ajoutez l'adresse du point de terminaison dans la zone d'entrée.</span><span class="sxs-lookup"><span data-stu-id="177b2-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="177b2-123">Par défaut, il s’agit de `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="177b2-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="177b2-124">Ouvrez l'application Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="177b2-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="177b2-125">Avant d’invoquer le service, commencez Event Viewer et assurez-vous que le journal de l’événement est à l’écoute des événements de suivi émis par le service WCF.</span><span class="sxs-lookup"><span data-stu-id="177b2-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="177b2-126">Du menu **Démarrer,** sélectionnez **des outils administratifs,** puis **Event Viewer**.</span><span class="sxs-lookup"><span data-stu-id="177b2-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="177b2-127">Activez les journaux **Analytic** et **Debug.**</span><span class="sxs-lookup"><span data-stu-id="177b2-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="177b2-128">Dans la vue d’arbre dans Event Viewer, naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="177b2-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="177b2-129">Application à clic droit **Server-Applications**, sélectionnez **View**, puis **Afficher les journaux Analytiques et Debug**.</span><span class="sxs-lookup"><span data-stu-id="177b2-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="177b2-130">Assurez-vous que l’option **Afficher l’analyse et les journaux Debug** est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="177b2-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="177b2-131">Activez le journal **Analytic.**</span><span class="sxs-lookup"><span data-stu-id="177b2-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="177b2-132">Dans la vue d’arbre dans Event Viewer, naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="177b2-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="177b2-133">Cliquez à droite **Analytic** et **sélectionnez Active Log**.</span><span class="sxs-lookup"><span data-stu-id="177b2-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="177b2-134">Pour tester le service</span><span class="sxs-lookup"><span data-stu-id="177b2-134">To test the service</span></span>

1. <span data-ttu-id="177b2-135">Revenez au client de test `Divide` WCF et double-clic et conservez les valeurs par défaut, qui spécifient un dénominateur de 0.</span><span class="sxs-lookup"><span data-stu-id="177b2-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="177b2-136">Si le dénominateur est 0, le service génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="177b2-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="177b2-137">Observez les événements émis par le service.</span><span class="sxs-lookup"><span data-stu-id="177b2-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="177b2-138">Retournez à Event Viewer et naviguez vers **Event Viewer**, Applications and **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="177b2-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="177b2-139">Cliquez à droite **Analytic** et **sélectionnez Refresh**.</span><span class="sxs-lookup"><span data-stu-id="177b2-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="177b2-140">Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="177b2-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="177b2-141">Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="177b2-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="177b2-142">Répétez les étapes 1 et 2, mais avec des entrées valides.</span><span class="sxs-lookup"><span data-stu-id="177b2-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="177b2-143">La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.</span><span class="sxs-lookup"><span data-stu-id="177b2-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="177b2-144">Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.</span><span class="sxs-lookup"><span data-stu-id="177b2-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="177b2-145">L'exemple montre les événements de trace analytique émis par un service WCF.</span><span class="sxs-lookup"><span data-stu-id="177b2-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="177b2-146">Pour effectuer un nettoyage (facultatif)</span><span class="sxs-lookup"><span data-stu-id="177b2-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="177b2-147">Ouvrez l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="177b2-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="177b2-148">Naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application-Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="177b2-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="177b2-149">Cliquez à droite **Analytic** et sélectionnez **Disable Log**.</span><span class="sxs-lookup"><span data-stu-id="177b2-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="177b2-150">Naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application-Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="177b2-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="177b2-151">Cliquez à droite **Analytic** et sélectionnez **Clear Log**.</span><span class="sxs-lookup"><span data-stu-id="177b2-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="177b2-152">Choisissez l’option **Clear** pour effacer les événements.</span><span class="sxs-lookup"><span data-stu-id="177b2-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="177b2-153">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="177b2-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="177b2-154">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="177b2-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="177b2-155">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="177b2-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="177b2-156">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="177b2-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="177b2-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="177b2-157">See also</span></span>

- <span data-ttu-id="177b2-158">[Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="177b2-158">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
