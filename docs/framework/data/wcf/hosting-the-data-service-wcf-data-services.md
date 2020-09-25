---
title: Hébergement du service de données (services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 5dfa1d9f02f660b55ecf6598ef5012174a1ba853
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172591"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="d82af-102">Hébergement du service de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="d82af-102">Hosting the Data Service (WCF Data Services)</span></span>

<span data-ttu-id="d82af-103">À l’aide de WCF Data Services, vous pouvez créer un service qui expose les données sous forme de flux OData (Open Data Protocol).</span><span class="sxs-lookup"><span data-stu-id="d82af-103">By using WCF Data Services, you can create a service that exposes data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="d82af-104">Ce service de données est défini comme une classe qui hérite de <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="d82af-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="d82af-105">Cette classe fournit les fonctionnalités requises pour traiter les messages de demande, effectuer des mises à jour sur la source de données et générer des messages de réponse, comme requis par OData.</span><span class="sxs-lookup"><span data-stu-id="d82af-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="d82af-106">Toutefois, un service de données ne peut pas se lier à un socket de réseau et écouter les requêtes HTTP entrantes.</span><span class="sxs-lookup"><span data-stu-id="d82af-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="d82af-107">Pour ces fonctionnalités requises, le service de données s'appuie sur un composant d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="d82af-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="d82af-108">L’hôte du service de données effectue les tâches suivantes pour le compte du service de données :</span><span class="sxs-lookup"><span data-stu-id="d82af-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="d82af-109">Écoute les demandes et les transmet au service de données.</span><span class="sxs-lookup"><span data-stu-id="d82af-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="d82af-110">Crée une instance du service de données pour chaque demande.</span><span class="sxs-lookup"><span data-stu-id="d82af-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="d82af-111">Demande au service de données de traiter la requête entrante.</span><span class="sxs-lookup"><span data-stu-id="d82af-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="d82af-112">Envoie la réponse de la part du service de données.</span><span class="sxs-lookup"><span data-stu-id="d82af-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="d82af-113">Pour simplifier l’hébergement d’un service de données, WCF Data Services est conçu pour s’intégrer à Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d82af-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d82af-114">Le service de données fournit une implémentation WCF par défaut qui sert d’hôte de service de données dans une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d82af-114">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="d82af-115">Vous pouvez donc héberger un service de données de l'une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="d82af-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="d82af-116">Dans une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d82af-116">In an ASP.NET application.</span></span>

- <span data-ttu-id="d82af-117">Dans une application managée qui prend en charge des services WCF auto-hébergés.</span><span class="sxs-lookup"><span data-stu-id="d82af-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="d82af-118">Dans un autre hôte de service de données personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d82af-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="d82af-119">Hébergement de services de données dans une application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d82af-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="d82af-120">Quand vous utilisez la boîte de dialogue **Ajouter un nouvel élément** dans Visual Studio 2015 pour définir un service de données dans une application ASP.net, l’outil génère deux nouveaux fichiers dans le projet.</span><span class="sxs-lookup"><span data-stu-id="d82af-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="d82af-121">Le premier fichier a une extension `.svc` et indique à l’exécution WCF comment instancier le service de données.</span><span class="sxs-lookup"><span data-stu-id="d82af-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="d82af-122">Voici un exemple de ce fichier pour l’exemple de service de données Northwind créé lorsque vous terminez le [démarrage rapide](quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="d82af-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="d82af-123">Cette directive dit à l'application de créer l'hôte de service pour la classe de service de données nommée en utilisant la classe <xref:System.Data.Services.DataServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="d82af-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="d82af-124">La page code-behind du fichier `.svc` contient la classe constituant l'implémentation du service de données lui-même, défini comme suit dans le cas de l'exemple de service de données Northwind :</span><span class="sxs-lookup"><span data-stu-id="d82af-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="d82af-125">Comme un service de données se comporte comme un service WCF, le service de données s’intègre à ASP.NET et suit le modèle de programmation Web WCF.</span><span class="sxs-lookup"><span data-stu-id="d82af-125">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="d82af-126">Pour plus d’informations, consultez [services WCF et ASP.net](../../wcf/feature-details/wcf-services-and-aspnet.md) et [modèle de programmation http Web WCF](../../wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="d82af-126">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="d82af-127">Services WCF auto-hébergés</span><span class="sxs-lookup"><span data-stu-id="d82af-127">Self-Hosted WCF Services</span></span>

 <span data-ttu-id="d82af-128">Étant donné qu’il intègre une implémentation WCF, WCF Data Services prendre en charge l’auto-hébergement d’un service de données en tant que service WCF.</span><span class="sxs-lookup"><span data-stu-id="d82af-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="d82af-129">Un service peut être auto-hébergé dans n’importe quelle application .NET Framework, telle qu’une application console.</span><span class="sxs-lookup"><span data-stu-id="d82af-129">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="d82af-130">La classe <xref:System.Data.Services.DataServiceHost>, qui hérite de <xref:System.ServiceModel.Web.WebServiceHost>, est utilisée pour instancier le service de données à une adresse spécifique.</span><span class="sxs-lookup"><span data-stu-id="d82af-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="d82af-131">L'auto-hébergement peut être utilisé pour le développement et les tests parce qu'elle permet de simplifier le déploiement et le dépannage du service.</span><span class="sxs-lookup"><span data-stu-id="d82af-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="d82af-132">Toutefois, ce type d’hébergement ne fournit pas les fonctionnalités d’hébergement et de gestion avancées fournies par ASP.NET ou par Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d82af-132">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="d82af-133">Pour plus d’informations, consultez [hébergement dans une application managée](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="d82af-133">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="d82af-134">Définition d'un hôte de service de données personnalisé</span><span class="sxs-lookup"><span data-stu-id="d82af-134">Defining a Custom Data Service Host</span></span>

 <span data-ttu-id="d82af-135">Dans les cas où l'implémentation hôte de WCF est trop restrictive, vous pouvez également définir un hôte personnalisé pour un service de données.</span><span class="sxs-lookup"><span data-stu-id="d82af-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="d82af-136">Toute classe qui implémente l'interface <xref:System.Data.Services.IDataServiceHost> peut être utilisée comme hôte de réseau pour un service de données.</span><span class="sxs-lookup"><span data-stu-id="d82af-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="d82af-137">Un hôte personnalisé doit implémenter l'interface <xref:System.Data.Services.IDataServiceHost> et pouvoir gérer les responsabilités de base suivantes de l'hôte de service de données :</span><span class="sxs-lookup"><span data-stu-id="d82af-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="d82af-138">Fournir le service de données avec le chemin d’accès racine du service.</span><span class="sxs-lookup"><span data-stu-id="d82af-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="d82af-139">Traiter les informations d'en-tête de demande et de réponse à l'implémentation appropriée du membre <xref:System.Data.Services.IDataServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d82af-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="d82af-140">Gérer les exceptions déclenchées par le service de données.</span><span class="sxs-lookup"><span data-stu-id="d82af-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="d82af-141">Valider les paramètres de la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="d82af-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="d82af-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d82af-142">See also</span></span>

- [<span data-ttu-id="d82af-143">Définition des services de données WCF</span><span class="sxs-lookup"><span data-stu-id="d82af-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="d82af-144">Exposition de vos données comme service</span><span class="sxs-lookup"><span data-stu-id="d82af-144">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="d82af-145">Configuration du service de données</span><span class="sxs-lookup"><span data-stu-id="d82af-145">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
