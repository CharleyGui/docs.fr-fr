---
title: Exemple SystemWebRouting Integration
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: a9f9dc871b92b8cd689234c79b09c98e38a2848d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650999"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="f3a86-102">Exemple SystemWebRouting Integration</span><span class="sxs-lookup"><span data-stu-id="f3a86-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="f3a86-103">Cet exemple illustre l'intégration de la couche d'hébergement avec les classes de l'espace de noms <xref:System.Web.Routing>.</span><span class="sxs-lookup"><span data-stu-id="f3a86-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="f3a86-104">Les classes de l'espace de noms <xref:System.Web.Routing> permettent à une application d'utiliser des URL qui ne correspondent pas directement à une ressource physique.</span><span class="sxs-lookup"><span data-stu-id="f3a86-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="f3a86-105">L’utilisation du routage Web permet au développeur de créer des adresses virtuelles pour le protocole HTTP qui sont ensuite remappées aux véritables services WCF.</span><span class="sxs-lookup"><span data-stu-id="f3a86-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="f3a86-106">Cela peut être utile lorsqu'un service WCF doit être hébergé sans requérir de fichier ou ressource physique, ou lorsque des services doivent être accessibles via des URL qui ne contiennent pas de fichiers tels que .html ou .aspx.</span><span class="sxs-lookup"><span data-stu-id="f3a86-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="f3a86-107">Cet exemple montre comment utiliser la classe <xref:System.Web.Routing.RouteTable> pour créer des URI virtuels qui mappent aux services en cours d'exécution définis dans global.asax.</span><span class="sxs-lookup"><span data-stu-id="f3a86-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
>  <span data-ttu-id="f3a86-108">Les classes de l'espace de noms <xref:System.Web.Routing> ne fonctionnent que pour des services hébergés sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3a86-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="f3a86-109">Cet exemple utilise WCF pour créer deux flux RSS : un `movies` d’alimentation et un `channels` flux.</span><span class="sxs-lookup"><span data-stu-id="f3a86-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="f3a86-110">Les URL pour activer les services ne contiennent pas une extension et sont inscrites dans le `Application_Start` méthode de la `Global` classe dérivée de la <xref:System.Web.HttpApplication> classe.</span><span class="sxs-lookup"><span data-stu-id="f3a86-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a86-111">Cet exemple fonctionne uniquement dans les Services Internet (IIS) 7.0 et versions ultérieures, IIS 6.0 utilise une autre méthode pour prendre en charge des URL sans extension.</span><span class="sxs-lookup"><span data-stu-id="f3a86-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="f3a86-112">Pour télécharger cet exemple</span><span class="sxs-lookup"><span data-stu-id="f3a86-112">To download this sample</span></span>
  
<span data-ttu-id="f3a86-113">Cet exemple peut déjà être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f3a86-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="f3a86-114">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f3a86-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="f3a86-115">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="f3a86-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f3a86-116">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f3a86-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f3a86-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="f3a86-117">To use this sample</span></span>  
  
1. <span data-ttu-id="f3a86-118">À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="f3a86-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="f3a86-119">Pour exécuter la solution et démarrer le serveur de développement Web, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="f3a86-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="f3a86-120">Une liste des répertoires de l'exemple s'affiche.</span><span class="sxs-lookup"><span data-stu-id="f3a86-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="f3a86-121">Notez l'absence de fichiers ayant l'extension .svc.</span><span class="sxs-lookup"><span data-stu-id="f3a86-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="f3a86-122">Dans la barre d’adresses, ajoutez `movies` à l’URL, par conséquent, qu’il lit `http://localhost:[port]/movies` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="f3a86-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="f3a86-123">Le flux movies s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="f3a86-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="f3a86-124">Dans la barre d’adresses, ajoutez `channels` à l’URL, c’est donc lectures `http://localhost:[port]/channels` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="f3a86-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="f3a86-125">Le flux channels s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="f3a86-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="f3a86-126">Fermez le navigateur Web en appuyant sur ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="f3a86-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="f3a86-127">Si le serveur de développement ne se n'est pas arrêté, cliquez sur l’icône de zone de notification et sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="f3a86-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="f3a86-128">Pour utiliser cet exemple avec hébergement dans IIS</span><span class="sxs-lookup"><span data-stu-id="f3a86-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="f3a86-129">À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="f3a86-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="f3a86-130">Générez le projet en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="f3a86-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="f3a86-131">Créez une application Web dans le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="f3a86-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="f3a86-132">Dans le Gestionnaire des services Internet, cliquez avec le bouton droit sur le **Site Web par défaut** et sélectionnez **ajouter une Application**.</span><span class="sxs-lookup"><span data-stu-id="f3a86-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="f3a86-133">Pour le **alias**, tapez `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="f3a86-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="f3a86-134">Pour le **chemin d’accès physique**, sélectionnez le dossier de Service à l’intérieur du projet.</span><span class="sxs-lookup"><span data-stu-id="f3a86-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="f3a86-135">Appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3a86-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="f3a86-136">Démarrer l’application, en double-cliquant sur l’application Web et en sélectionnant **gérer l’Application** , puis **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="f3a86-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="f3a86-137">Dans la barre d’adresses, ajoutez `movies` à l’URL, c’est donc lectures `http://localhost:[port]/movies` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="f3a86-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="f3a86-138">Le flux movies s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="f3a86-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="f3a86-139">Dans la barre d’adresses, ajoutez `channels` à l’URL, c’est donc lectures `http://localhost:[port]/channels` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="f3a86-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="f3a86-140">Le flux channels s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="f3a86-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="f3a86-141">Fermez le navigateur Web en appuyant sur ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="f3a86-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="f3a86-142">Cet exemple montre que la couche d'hébergement est capable de composer avec les classes de l'espace de noms <xref:System.Web.Routing> pour router les requêtes de services hébergés sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3a86-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a86-143">Vous devez mettre à jour la version de pool d’application par défaut à [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] si elle est définie à la version 2.</span><span class="sxs-lookup"><span data-stu-id="f3a86-143">You must update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a86-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3a86-144">See also</span></span>

- [<span data-ttu-id="f3a86-145">Hébergement AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="f3a86-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
