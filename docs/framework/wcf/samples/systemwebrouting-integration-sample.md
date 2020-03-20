---
title: Exemple SystemWebRouting Integration
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143952"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="1a65b-102">Exemple SystemWebRouting Integration</span><span class="sxs-lookup"><span data-stu-id="1a65b-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="1a65b-103">Cet exemple illustre l'intégration de la couche d'hébergement avec les classes de l'espace de noms <xref:System.Web.Routing>.</span><span class="sxs-lookup"><span data-stu-id="1a65b-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="1a65b-104">Les classes de l'espace de noms <xref:System.Web.Routing> permettent à une application d'utiliser des URL qui ne correspondent pas directement à une ressource physique.</span><span class="sxs-lookup"><span data-stu-id="1a65b-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="1a65b-105">L’utilisation du routage Web permet au développeur de créer des adresses virtuelles pour HTTP qui sont ensuite cartographiées vers les services WCF réels.</span><span class="sxs-lookup"><span data-stu-id="1a65b-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="1a65b-106">Cela peut être utile lorsqu'un service WCF doit être hébergé sans requérir de fichier ou ressource physique, ou lorsque des services doivent être accessibles via des URL qui ne contiennent pas de fichiers tels que .html ou .aspx.</span><span class="sxs-lookup"><span data-stu-id="1a65b-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="1a65b-107">Cet exemple montre comment utiliser la classe <xref:System.Web.Routing.RouteTable> pour créer des URI virtuels qui mappent aux services en cours d'exécution définis dans global.asax.</span><span class="sxs-lookup"><span data-stu-id="1a65b-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="1a65b-108">Les classes de l'espace de noms <xref:System.Web.Routing> ne fonctionnent que pour des services hébergés sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a65b-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="1a65b-109">Cet exemple utilise WCF pour créer deux `movies` flux RSS : un flux et un `channels` flux.</span><span class="sxs-lookup"><span data-stu-id="1a65b-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="1a65b-110">Les URL pour activer les services ne contiennent pas `Application_Start` d’extension et sont enregistrées dans la méthode de la `Global` classe dérivée de la <xref:System.Web.HttpApplication> classe.</span><span class="sxs-lookup"><span data-stu-id="1a65b-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a65b-111">Cet échantillon ne fonctionne que dans les services d’information Internet (IIS) 7.0 et plus tard, car IIS 6.0 utilise une méthode différente pour soutenir les URL sans extension.</span><span class="sxs-lookup"><span data-stu-id="1a65b-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="1a65b-112">Pour télécharger cet exemple</span><span class="sxs-lookup"><span data-stu-id="1a65b-112">To download this sample</span></span>
  
<span data-ttu-id="1a65b-113">Cet échantillon peut déjà être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1a65b-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="1a65b-114">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1a65b-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="1a65b-115">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="1a65b-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a65b-116">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1a65b-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1a65b-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="1a65b-117">To use this sample</span></span>  
  
1. <span data-ttu-id="1a65b-118">À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="1a65b-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="1a65b-119">Pour exécuter la solution et démarrer le serveur de développement Web, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="1a65b-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="1a65b-120">Une liste des répertoires de l'exemple s'affiche.</span><span class="sxs-lookup"><span data-stu-id="1a65b-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="1a65b-121">Notez l'absence de fichiers ayant l'extension .svc.</span><span class="sxs-lookup"><span data-stu-id="1a65b-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="1a65b-122">Dans la barre `movies` d’adresse, ajoutez à `http://localhost:[port]/movies` l’URL, de sorte qu’elle se lit et appuyez sur ENTER.</span><span class="sxs-lookup"><span data-stu-id="1a65b-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="1a65b-123">Le flux movies s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="1a65b-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="1a65b-124">Dans la barre `channels` d’adresse, ajouter à `http://localhost:[port]/channels` l’URL, de sorte que se lit et appuyez sur ENTER.</span><span class="sxs-lookup"><span data-stu-id="1a65b-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="1a65b-125">Le flux channels s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="1a65b-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="1a65b-126">Fermez le navigateur Web en appuyant sur ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="1a65b-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="1a65b-127">Si le serveur de développement n’est pas sorti, cliquez à droite sur l’icône de la zone de notification et **sélectionnez Stop**.</span><span class="sxs-lookup"><span data-stu-id="1a65b-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="1a65b-128">Pour utiliser cet exemple avec hébergement dans IIS</span><span class="sxs-lookup"><span data-stu-id="1a65b-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="1a65b-129">À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="1a65b-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="1a65b-130">Générez le projet en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="1a65b-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="1a65b-131">Créez une application Web dans le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="1a65b-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="1a65b-132">Dans IIS Manager, cliquez à droite sur le **site Web par défaut** et sélectionnez Ajouter une **application**.</span><span class="sxs-lookup"><span data-stu-id="1a65b-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="1a65b-133">Pour le **pseudonyme**, tapez dans `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="1a65b-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="1a65b-134">Pour le **chemin physique**, sélectionnez le dossier Service à l’intérieur du projet.</span><span class="sxs-lookup"><span data-stu-id="1a65b-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="1a65b-135">Appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a65b-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="1a65b-136">Démarrez l’application, en cliquant à droite sur l’application Web et en sélectionnant **Manage Application,** puis **parcourez.**</span><span class="sxs-lookup"><span data-stu-id="1a65b-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="1a65b-137">Dans la barre `movies` d’adresse, ajouter à `http://localhost:[port]/movies` l’URL, de sorte que se lit et appuyez sur ENTER.</span><span class="sxs-lookup"><span data-stu-id="1a65b-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="1a65b-138">Le flux movies s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="1a65b-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="1a65b-139">Dans la barre `channels` d’adresse, ajouter à `http://localhost:[port]/channels` l’URL, de sorte que se lit et appuyez sur ENTER.</span><span class="sxs-lookup"><span data-stu-id="1a65b-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="1a65b-140">Le flux channels s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="1a65b-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="1a65b-141">Fermez le navigateur Web en appuyant sur ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="1a65b-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="1a65b-142">Cet exemple montre que la couche d'hébergement est capable de composer avec les classes de l'espace de noms <xref:System.Web.Routing> pour router les requêtes de services hébergés sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a65b-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a65b-143">Vous devez mettre à jour la version de pool d’applications par défaut à .NET Framework 4 si elle est configurée à la version 2.</span><span class="sxs-lookup"><span data-stu-id="1a65b-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a65b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a65b-144">See also</span></span>

- <span data-ttu-id="1a65b-145">[Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1a65b-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
