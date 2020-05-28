---
title: "Comment : publier les métadonnées d'un service à l'aide de code"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: db6bca8728789879f9bfea40904bfc80352d1dbe
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144914"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="3c7b3-102">Comment : publier les métadonnées d'un service à l'aide de code</span><span class="sxs-lookup"><span data-stu-id="3c7b3-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="3c7b3-103">Il s’agit de l’une des deux rubriques de procédures qui traitent de la publication de métadonnées pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3c7b3-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="3c7b3-104">Il y a deux façons de spécifier comment un service doit publier des métadonnées : à l'aide d'un fichier de configuration et à l'aide du code.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="3c7b3-105">Cette rubrique montre comment publier les métadonnées d'un service à l'aide d'un code.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3c7b3-106">Cette rubrique indique comment publier des métadonnées de manière non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="3c7b3-107">Tout client peut récupérer les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="3c7b3-108">Si votre service doit publier les métadonnées de manière sécurisée.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="3c7b3-109">consultez [point de terminaison de métadonnées sécurisées personnalisé](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="3c7b3-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="3c7b3-110">Pour plus d’informations sur la publication de métadonnées dans un fichier de configuration, consultez [Comment : publier des métadonnées pour un service à l’aide d’un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="3c7b3-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="3c7b3-111">La publication des métadonnées permet aux clients de récupérer les métadonnées via une requête WS-Transfer GET ou une requête HTTP/GET à l'aide de la chaîne de requête `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="3c7b3-112">Pour être sûr que le code fonctionne, vous devez créer un service WCF de base.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="3c7b3-113">Un service auto-hébergé de base est fourni dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="3c7b3-114">Pour publier les métadonnées dans le code</span><span class="sxs-lookup"><span data-stu-id="3c7b3-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="3c7b3-115">Dans la méthode principale d'une application console, instanciez un objet <xref:System.ServiceModel.ServiceHost> en passant le type de service et l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="3c7b3-116">Créez immédiatement un bloc try sous le code pour l'étape 1, celui-ci intercepte toutes les exceptions levées pendant l'exécution du service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="3c7b3-117">Vérifiez si l'hôte de service contient déjà un <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, si ce n'est pas le cas, créez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="3c7b3-118">Affectez à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> la valeur `true.`</span><span class="sxs-lookup"><span data-stu-id="3c7b3-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="3c7b3-119">Le <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contient une <xref:System.ServiceModel.Description.MetadataExporter>.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="3c7b3-120">Le <xref:System.ServiceModel.Description.MetadataExporter> contient une <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="3c7b3-121">Affectez à la propriété <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="3c7b3-122">Vous pouvez affecter à la propriété <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="3c7b3-123">Lorsqu’il a <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> la valeur, l’exportateur de métadonnées génère les informations de stratégie avec les métadonnées qui sont conformes à WS-policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="3c7b3-124">Lorsqu'il a la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>, l'exportateur de métadonnées génère les informations de stratégie qui se conforment à WS-Policy 1.2.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="3c7b3-125">Ajoutez l'instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior> à la collection de comportements de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="3c7b3-126">Ajoutez le point de terminaison d'échange des métadonnées à l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="3c7b3-127">Ajoutez un point de terminaison d'application à l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="3c7b3-128">Si vous n'ajoutez pas de points de terminaison au service, le runtime ajoute les points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="3c7b3-129">Dans cet exemple, étant donné que le service a un <xref:System.ServiceModel.Description.ServiceMetadataBehavior> défini sur la valeur `true`, la publication des métadonnées est activée pour le service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="3c7b3-130">Pour plus d’informations sur les points de terminaison par défaut, consultez [configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c7b3-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="3c7b3-131">Ouvrez l'hôte de service et attendez les appels entrants.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="3c7b3-132">Lorsque l'utilisateur appuie sur ENTRÉE, fermez l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="3c7b3-133">Créez et exécutez l’application console.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="3c7b3-134">Utilisez Internet Explorer pour accéder à l’adresse de base du service ( `http://localhost:8001/MetadataSample` dans cet exemple) et vérifiez que la publication des métadonnées est activée.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-134">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="3c7b3-135">Vous devriez voir s’afficher une page web qui indique "Service simple" en haut et plus bas "Vous a créé un service".</span><span class="sxs-lookup"><span data-stu-id="3c7b3-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="3c7b3-136">Dans la négative, un message s'affiche en haut de la page résultante : "La publication des métadonnées pour ce service est actuellement désactivée".</span><span class="sxs-lookup"><span data-stu-id="3c7b3-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c7b3-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c7b3-137">Example</span></span>  
 <span data-ttu-id="3c7b3-138">L’exemple de code suivant montre l’implémentation d’un service WCF de base qui publie des métadonnées pour le service dans le code.</span><span class="sxs-lookup"><span data-stu-id="3c7b3-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3c7b3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c7b3-139">See also</span></span>

- [<span data-ttu-id="3c7b3-140">Comment : héberger un service WCF dans une application managée</span><span class="sxs-lookup"><span data-stu-id="3c7b3-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="3c7b3-141">Auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="3c7b3-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="3c7b3-142">Vue d'ensemble de l'architecture de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3c7b3-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="3c7b3-143">Utilisation des métadonnées</span><span class="sxs-lookup"><span data-stu-id="3c7b3-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="3c7b3-144">Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="3c7b3-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
