---
title: 'Points de terminaison : Adresses, liaisons et contrats'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3d345cfa3169e22e7c5e85cd1c7d11c2feef4f5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665958"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="eed0c-102">Points de terminaison : Adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="eed0c-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="eed0c-103">Toutes les communications avec un service Windows Communication Foundation (WCF) s’effectue via le *points de terminaison* du service.</span><span class="sxs-lookup"><span data-stu-id="eed0c-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="eed0c-104">Points de terminaison fournissent les clients l’accès à la fonctionnalité offerte par un service WCF.</span><span class="sxs-lookup"><span data-stu-id="eed0c-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="eed0c-105">Chaque point de terminaison se compose de quatre propriétés :</span><span class="sxs-lookup"><span data-stu-id="eed0c-105">Each endpoint consists of four properties:</span></span>  
  
- <span data-ttu-id="eed0c-106">Une adresse qui indique où rechercher le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eed0c-106">An address that indicates where the endpoint can be found.</span></span>  
  
- <span data-ttu-id="eed0c-107">Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eed0c-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="eed0c-108">Un contrat qui identifie les opérations disponibles.</span><span class="sxs-lookup"><span data-stu-id="eed0c-108">A contract that identifies the operations available.</span></span>  
  
- <span data-ttu-id="eed0c-109">L'ensemble des comportements qui spécifient les détails d'implémentation locaux du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eed0c-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="eed0c-110">Cette rubrique traite de cette structure de point de terminaison et explique comment elle est représentée dans le modèle d’objet WCF.</span><span class="sxs-lookup"><span data-stu-id="eed0c-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="eed0c-111">Structure d'un point de terminaison</span><span class="sxs-lookup"><span data-stu-id="eed0c-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="eed0c-112">Chaque point de terminaison comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="eed0c-112">Each endpoint consists of the following:</span></span>  
  
- <span data-ttu-id="eed0c-113">Adresse : L’adresse identifie le point de terminaison et indique le potentiel de manière unique les consommateurs du service dans lequel il se trouve.</span><span class="sxs-lookup"><span data-stu-id="eed0c-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="eed0c-114">Elle est représentée dans le modèle d’objet WCF par le <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="eed0c-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="eed0c-115">Une classe <xref:System.ServiceModel.EndpointAddress> contient :</span><span class="sxs-lookup"><span data-stu-id="eed0c-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    - <span data-ttu-id="eed0c-116">Une propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A>, qui représente l'adresse du service.</span><span class="sxs-lookup"><span data-stu-id="eed0c-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    - <span data-ttu-id="eed0c-117">Une propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> qui représente l’identité de sécurité du service et une collection d’en-tête de message facultatifs.</span><span class="sxs-lookup"><span data-stu-id="eed0c-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="eed0c-118">Les en-têtes de message facultatifs sont utilisés pour fournir des informations d'adressage supplémentaires et plus détaillées afin d'identifier le point de terminaison ou d'interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="eed0c-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="eed0c-119">Pour plus d’informations, consultez [spécification d’une adresse de point de terminaison](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
- <span data-ttu-id="eed0c-120">Liaison : La liaison spécifie le mode de communication avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eed0c-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="eed0c-121">Cela concerne :</span><span class="sxs-lookup"><span data-stu-id="eed0c-121">This includes:</span></span>  
  
    - <span data-ttu-id="eed0c-122">Le protocole de transport à utiliser (par exemple, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="eed0c-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    - <span data-ttu-id="eed0c-123">L'encodage à utiliser pour les messages (par exemple, texte ou binaire).</span><span class="sxs-lookup"><span data-stu-id="eed0c-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    - <span data-ttu-id="eed0c-124">Les exigences de sécurité nécessaires (par exemple, SSL ou la sécurité des messages SOAP).</span><span class="sxs-lookup"><span data-stu-id="eed0c-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="eed0c-125">Pour plus d’informations, consultez [vue d’ensemble des liaisons WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="eed0c-126">Une liaison est représentée dans le modèle objet WCF par la classe de base abstraite <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="eed0c-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="eed0c-127">Pour la plupart des scénarios, les utilisateurs peuvent utiliser l'une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="eed0c-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="eed0c-128">Pour plus d’informations, consultez [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
- <span data-ttu-id="eed0c-129">Contrats : Le contrat définit les fonctionnalités que le point de terminaison expose au client.</span><span class="sxs-lookup"><span data-stu-id="eed0c-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="eed0c-130">Un contrat spécifie :</span><span class="sxs-lookup"><span data-stu-id="eed0c-130">A contract specifies:</span></span>  
  
    - <span data-ttu-id="eed0c-131">Quelles opérations peuvent être appelées par un client.</span><span class="sxs-lookup"><span data-stu-id="eed0c-131">What operations can be called by a client.</span></span>  
  
    - <span data-ttu-id="eed0c-132">Le format du message.</span><span class="sxs-lookup"><span data-stu-id="eed0c-132">The form of the message.</span></span>  
  
    - <span data-ttu-id="eed0c-133">Le type de paramètres d'entrée ou les données requis pour appeler l'opération.</span><span class="sxs-lookup"><span data-stu-id="eed0c-133">The type of input parameters or data required to call the operation.</span></span>  
  
    - <span data-ttu-id="eed0c-134">Le type de traitement ou le message de réponse que le client peut attendre.</span><span class="sxs-lookup"><span data-stu-id="eed0c-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="eed0c-135">Pour plus d’informations sur la définition d’un contrat, consultez [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
- <span data-ttu-id="eed0c-136">Comportements : Vous pouvez utiliser des comportements de point de terminaison pour personnaliser le comportement du point de terminaison de service local.</span><span class="sxs-lookup"><span data-stu-id="eed0c-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="eed0c-137">Pour cela, les comportements de point de terminaison participant au processus de création d’un WCFruntime.</span><span class="sxs-lookup"><span data-stu-id="eed0c-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="eed0c-138">Un exemple de comportement de point de terminaison est la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> qui vous permet de spécifier une adresse d'écoute différente de l'adresse SOAP ou WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="eed0c-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="eed0c-139">Pour plus d’informations, consultez [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="eed0c-140">Définition des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="eed0c-140">Defining Endpoints</span></span>  
 <span data-ttu-id="eed0c-141">L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration.</span><span class="sxs-lookup"><span data-stu-id="eed0c-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="eed0c-142">Pour plus d'informations, voir [Procédure : Créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) et [Comment : Créer un point de terminaison de Service dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eed0c-143">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eed0c-143">In This Section</span></span>  
 <span data-ttu-id="eed0c-144">Cette section explique à quoi servent les liaisons, les points de terminaison et les adresses, indique comment configurer une liaison et un point de terminaison et montre comment utiliser le comportement `ClientVia` et la propriété `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="eed0c-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="eed0c-145">Adresses</span><span class="sxs-lookup"><span data-stu-id="eed0c-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="eed0c-146">Décrit la façon dont les points de terminaison sont adressés dans WCF.</span><span class="sxs-lookup"><span data-stu-id="eed0c-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="eed0c-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="eed0c-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="eed0c-148">Décrit comment les liaisons sont utilisées pour spécifier le transport, l’encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="eed0c-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="eed0c-149">Contrats</span><span class="sxs-lookup"><span data-stu-id="eed0c-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="eed0c-150">Décrit comment les contrats définissent les méthodes d'un service.</span><span class="sxs-lookup"><span data-stu-id="eed0c-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="eed0c-151">Guide pratique pour Créer un point de terminaison de Service dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="eed0c-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="eed0c-152">Décrit comment créer un point de terminaison de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="eed0c-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="eed0c-153">Guide pratique pour Créer un point de terminaison de Service dans le Code</span><span class="sxs-lookup"><span data-stu-id="eed0c-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="eed0c-154">Décrit comment créer un point de terminaison de service dans le code.</span><span class="sxs-lookup"><span data-stu-id="eed0c-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="eed0c-155">Guide pratique pour Utiliser Svcutil.exe pour valider le Code de Service compilé</span><span class="sxs-lookup"><span data-stu-id="eed0c-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="eed0c-156">Décrit comment détecter les erreurs dans les configurations et les implémentations de service sans héberger le service en utilisant le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="eed0c-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed0c-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eed0c-157">See also</span></span>

- [<span data-ttu-id="eed0c-158">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="eed0c-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="eed0c-159">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="eed0c-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
