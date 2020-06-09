---
title: ASP.NET Caching Integration
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: c541f3caad8a500b9fdb33d00b58706bac876e37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594749"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="17ee3-102">ASP.NET Caching Integration</span><span class="sxs-lookup"><span data-stu-id="17ee3-102">ASP.NET Caching Integration</span></span>

<span data-ttu-id="17ee3-103">Cet exemple montre comment utiliser le cache de sortie ASP.NET avec le modèle de programmation HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="17ee3-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="17ee3-104">Cette rubrique met l’accent sur la fonctionnalité d’intégration du cache de sortie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="17ee3-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="17ee3-105">Illustre</span><span class="sxs-lookup"><span data-stu-id="17ee3-105">Demonstrates</span></span>

<span data-ttu-id="17ee3-106">Intégration au cache de sortie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="17ee3-106">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17ee3-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17ee3-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="17ee3-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="17ee3-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="17ee3-109">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="17ee3-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17ee3-110">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="17ee3-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="17ee3-111">Discussions</span><span class="sxs-lookup"><span data-stu-id="17ee3-111">Discussion</span></span>

<span data-ttu-id="17ee3-112">L’exemple utilise le <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pour utiliser la mise en cache de sortie ASP.net avec le service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="17ee3-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="17ee3-113">L'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est appliqué aux opérations de service et fournit le nom d'un profil de cache dans un fichier de configuration qui doit être appliqué aux réponses de l'opération donnée.</span><span class="sxs-lookup"><span data-stu-id="17ee3-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="17ee3-114">Dans le fichier Service.cs de l’exemple de projet de service, `GetCustomer` les `GetCustomers` opérations et sont marquées avec le <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , qui fournit le nom de profil de cache « CacheFor60Seconds ».</span><span class="sxs-lookup"><span data-stu-id="17ee3-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="17ee3-115">Dans le fichier Web. config du projet de service, le profil de cache « CacheFor60Seconds » est fourni sous l' `caching` élément < > de < `system.web` >.</span><span class="sxs-lookup"><span data-stu-id="17ee3-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="17ee3-116">Pour ce profil de cache, la valeur de l' `duration` attribut est « 60 », donc les réponses associées à ce profil sont mises en cache dans le cache de sortie ASP.net pendant 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="17ee3-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="17ee3-117">En outre, pour ce profil de cache, l' `varmByParam` attribut est défini sur « format », de sorte que les réponses des demandes avec des valeurs différentes pour le `format` paramètre de chaîne de requête sont mises en cache séparément.</span><span class="sxs-lookup"><span data-stu-id="17ee3-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="17ee3-118">Enfin, l’attribut du profil de cache `varyByHeader` est défini sur « accepter », de sorte que les réponses des demandes avec des valeurs d’en-tête Accept différentes sont mises en cache séparément.</span><span class="sxs-lookup"><span data-stu-id="17ee3-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="17ee3-119">Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="17ee3-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="17ee3-120">Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service WCF.</span><span class="sxs-lookup"><span data-stu-id="17ee3-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="17ee3-121">Il est également possible d’accéder au service à l’aide d’autres classes de .NET Framework telles que la fabrique de canal WCF et <xref:System.Net.WebClient> .</span><span class="sxs-lookup"><span data-stu-id="17ee3-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="17ee3-122">D’autres exemples du kit de développement logiciel (SDK), tels que l’exemple de [service http de base](basic-http-service.md) , montrent comment utiliser ces classes pour communiquer avec un service WCF.</span><span class="sxs-lookup"><span data-stu-id="17ee3-122">Other samples in the SDK (such as the [Basic HTTP Service](basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="17ee3-123">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="17ee3-123">To run the sample</span></span>

<span data-ttu-id="17ee3-124">Cet exemple est composé de trois projets :</span><span class="sxs-lookup"><span data-stu-id="17ee3-124">The sample consists of three projects:</span></span>

- <span data-ttu-id="17ee3-125">**Service**: projet d’application Web qui comprend un service HTTP WCF hébergé dans ASP.net.</span><span class="sxs-lookup"><span data-stu-id="17ee3-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="17ee3-126">**Client**: un projet d’application console qui effectue des appels au service.</span><span class="sxs-lookup"><span data-stu-id="17ee3-126">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="17ee3-127">**Commun**: bibliothèque partagée qui contient le type de client utilisé par le client et le service.</span><span class="sxs-lookup"><span data-stu-id="17ee3-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="17ee3-128">Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="17ee3-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="17ee3-129">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="17ee3-129">To run the sample</span></span>

1. <span data-ttu-id="17ee3-130">Ouvrez la solution de l'exemple ASP.NET Caching Integration.</span><span class="sxs-lookup"><span data-stu-id="17ee3-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="17ee3-131">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="17ee3-131">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="17ee3-132">Si la fenêtre de **Explorateur de solutions** n’est pas déjà ouverte, appuyez sur CTRL + W + S.</span><span class="sxs-lookup"><span data-stu-id="17ee3-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="17ee3-133">Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le projet de **service** , puis sélectionnez **Démarrer une nouvelle instance**.</span><span class="sxs-lookup"><span data-stu-id="17ee3-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="17ee3-134">Cette opération lance le serveur de développement ASP.NET, qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="17ee3-134">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="17ee3-135">Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le projet **client** , puis sélectionnez **Démarrer une nouvelle instance**.</span><span class="sxs-lookup"><span data-stu-id="17ee3-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="17ee3-136">La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.</span><span class="sxs-lookup"><span data-stu-id="17ee3-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="17ee3-137">Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="17ee3-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="17ee3-138">Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.</span><span class="sxs-lookup"><span data-stu-id="17ee3-138">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="17ee3-139">Appuyez sur une touche quelconque pour arrêter l'application console Client.</span><span class="sxs-lookup"><span data-stu-id="17ee3-139">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="17ee3-140">Appuyez sur MAJ+F5 pour arrêter le débogage du service.</span><span class="sxs-lookup"><span data-stu-id="17ee3-140">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="17ee3-141">Dans la zone de notification Windows, cliquez avec le bouton droit sur l’icône du serveur de développement ASP.NET et sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="17ee3-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
