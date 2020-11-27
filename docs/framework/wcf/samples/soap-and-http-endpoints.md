---
title: Points de terminaison SOAP et HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 9e7ce32a0f5a2f37294db57659e2b30b364bef24
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268259"
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="791e5-102">Points de terminaison SOAP et HTTP</span><span class="sxs-lookup"><span data-stu-id="791e5-102">SOAP and HTTP Endpoints</span></span>

<span data-ttu-id="791e5-103">Cet exemple montre comment implémenter un service basé sur RPC et l’exposer au format SOAP et au format POX (Plain Old XML) à l’aide du modèle de programmation Web WCF.</span><span class="sxs-lookup"><span data-stu-id="791e5-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the WCF Web Programming model.</span></span> <span data-ttu-id="791e5-104">Pour plus d’informations sur la liaison HTTP pour le service, consultez l’exemple de [service http de base](basic-http-service.md) .</span><span class="sxs-lookup"><span data-stu-id="791e5-104">See the [Basic HTTP Service](basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="791e5-105">Cet exemple se concentre sur les détails ayant trait à l’exposition du même service sur SOAP et HTTP au moyen de différentes liaisons.</span><span class="sxs-lookup"><span data-stu-id="791e5-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="791e5-106">Illustre le</span><span class="sxs-lookup"><span data-stu-id="791e5-106">Demonstrates</span></span>  

 <span data-ttu-id="791e5-107">Exposition d’un service RPC sur SOAP et HTTP à l’aide de WCF.</span><span class="sxs-lookup"><span data-stu-id="791e5-107">Exposing an RPC service over SOAP and HTTP using WCF.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="791e5-108">Discussions</span><span class="sxs-lookup"><span data-stu-id="791e5-108">Discussion</span></span>  

 <span data-ttu-id="791e5-109">Cet exemple se compose de deux composants : un projet d’application Web (service) qui contient un service WCF et une application console (client) qui appelle des opérations de service à l’aide de liaisons SOAP et HTTP.</span><span class="sxs-lookup"><span data-stu-id="791e5-109">This sample consists of two components: a Web Application project (Service) that contains a WCF service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="791e5-110">Le service WCF expose 2 opérations, `GetData` et, `PutData` qui répercutent la chaîne passée comme entrée.</span><span class="sxs-lookup"><span data-stu-id="791e5-110">The WCF service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="791e5-111">Les opérations de service sont annotées avec <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="791e5-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="791e5-112">Ces attributs contrôlent la projection HTTP de ces opérations.</span><span class="sxs-lookup"><span data-stu-id="791e5-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="791e5-113">Elles sont aussi annotées avec <xref:System.ServiceModel.OperationContractAttribute>, ce qui permet leur exposition sur des liaisons SOAP.</span><span class="sxs-lookup"><span data-stu-id="791e5-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="791e5-114">La méthode `PutData` du service lève un <xref:System.ServiceModel.Web.WebFaultException>, qui est renvoyé sur HTTP avec le code d'état HTTP et sur SOAP en tant qu'erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="791e5-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="791e5-115">Le fichier Web.config configure le service WCF avec 3 points de terminaison :</span><span class="sxs-lookup"><span data-stu-id="791e5-115">The Web.config file configures the WCF service with 3 endpoints:</span></span>  
  
- <span data-ttu-id="791e5-116">le point de terminaison ~/service.svc/mex qui expose les métadonnées du service pour l'accès des clients SOAP ;</span><span class="sxs-lookup"><span data-stu-id="791e5-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
- <span data-ttu-id="791e5-117">le point de terminaison ~/service.svc/http qui permet aux clients d’accéder au service en utilisant la liaison HTTP ;</span><span class="sxs-lookup"><span data-stu-id="791e5-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
- <span data-ttu-id="791e5-118">le point de terminaison ~/service.svc/soap qui permet aux clients d’accéder au service en utilisant la liaison SOAP sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="791e5-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="791e5-119">Le point de terminaison HTTP est configuré avec un <`webHttp`> point de terminaison standard qui a la `helpEnabled` valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="791e5-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="791e5-120">Par conséquent, le service expose sous ~/service.svc/http/help une page d'aide XHTML que les clients HTTP peuvent utiliser pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="791e5-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="791e5-121">Le projet client illustre l’accès au service à l’aide d’un proxy SOAP (généré via **Ajouter une référence de service**) et l’accès au service à l’aide de <xref:System.Net.WebClient> .</span><span class="sxs-lookup"><span data-stu-id="791e5-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="791e5-122">L'exemple se compose d'un service hébergé sur le Web et d'une application console.</span><span class="sxs-lookup"><span data-stu-id="791e5-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="791e5-123">Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="791e5-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="791e5-124">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="791e5-124">To run the sample</span></span>  
  
1. <span data-ttu-id="791e5-125">Ouvrez la solution de l'exemple des points de terminaison SOAP et HTTP.</span><span class="sxs-lookup"><span data-stu-id="791e5-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2. <span data-ttu-id="791e5-126">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="791e5-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="791e5-127">S’il n’est pas déjà ouvert, appuyez sur CTRL + W, S pour ouvrir la fenêtre **Explorateur de solutions** .</span><span class="sxs-lookup"><span data-stu-id="791e5-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4. <span data-ttu-id="791e5-128">Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le projet de **service** et placez le curseur sur l’option de menu contextuel **débogage** pour afficher le menu contextuel **Démarrer une nouvelle instance** .</span><span class="sxs-lookup"><span data-stu-id="791e5-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="791e5-129">Cliquez sur **Démarrer une nouvelle instance**.</span><span class="sxs-lookup"><span data-stu-id="791e5-129">Click **Start New Instance**.</span></span> <span data-ttu-id="791e5-130">Cette opération lance le serveur de développement ASP.NET, qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="791e5-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5. <span data-ttu-id="791e5-131">Dans le Explorateur de solutions Windows, cliquez avec le bouton droit sur le projet client et placez le curseur sur l’option de menu contextuel **débogage** pour afficher le menu contextuel **Démarrer une nouvelle instance** .</span><span class="sxs-lookup"><span data-stu-id="791e5-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="791e5-132">Cliquez sur **Démarrer une nouvelle instance**.</span><span class="sxs-lookup"><span data-stu-id="791e5-132">Click **Start New Instance**.</span></span>  
  
6. <span data-ttu-id="791e5-133">La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.</span><span class="sxs-lookup"><span data-stu-id="791e5-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="791e5-134">Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="791e5-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7. <span data-ttu-id="791e5-135">Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.</span><span class="sxs-lookup"><span data-stu-id="791e5-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8. <span data-ttu-id="791e5-136">Appuyez sur une touche quelconque pour arrêter l'application console Client.</span><span class="sxs-lookup"><span data-stu-id="791e5-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="791e5-137">Appuyez sur MAJ+F5 pour arrêter le débogage du service.</span><span class="sxs-lookup"><span data-stu-id="791e5-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="791e5-138">Dans la zone de notification Windows, cliquez avec le bouton droit sur l’icône du serveur de développement ASP.NET et sélectionnez **arrêter** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="791e5-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="791e5-139">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="791e5-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="791e5-140">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="791e5-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="791e5-141">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="791e5-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="791e5-142">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="791e5-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
