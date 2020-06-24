---
title: 'Points de terminaison : adresses, liaisons et contrats'
description: Découvrez comment toute communication avec un service WCF se produit via les points de terminaison de service, qui permettent aux clients d’accéder aux fonctionnalités offertes par le service.
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: ce0874bfed716716b6fd1801b35a4266095cd752
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247310"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="d17c8-103">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="d17c8-103">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="d17c8-104">Toutes les communications avec un service Windows Communication Foundation (WCF) se produisent via les *points de terminaison* du service.</span><span class="sxs-lookup"><span data-stu-id="d17c8-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="d17c8-105">Les points de terminaison fournissent aux clients l’accès aux fonctionnalités offertes par un service WCF.</span><span class="sxs-lookup"><span data-stu-id="d17c8-105">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="d17c8-106">Chaque point de terminaison se compose de quatre propriétés :</span><span class="sxs-lookup"><span data-stu-id="d17c8-106">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="d17c8-107">Une adresse qui indique où rechercher le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d17c8-107">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="d17c8-108">Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d17c8-108">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="d17c8-109">Un contrat qui identifie les opérations disponibles.</span><span class="sxs-lookup"><span data-stu-id="d17c8-109">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="d17c8-110">L'ensemble des comportements qui spécifient les détails d'implémentation locaux du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d17c8-110">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="d17c8-111">Cette rubrique traite de cette structure de point de terminaison et explique comment elle est représentée dans le modèle d’objet WCF.</span><span class="sxs-lookup"><span data-stu-id="d17c8-111">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="d17c8-112">Structure d'un point de terminaison</span><span class="sxs-lookup"><span data-stu-id="d17c8-112">The Structure of an Endpoint</span></span>

<span data-ttu-id="d17c8-113">Chaque point de terminaison comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d17c8-113">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="d17c8-114">Adresse : l'adresse identifie le point de terminaison de manière unique et indique aux consommateurs potentiels l'emplacement du service.</span><span class="sxs-lookup"><span data-stu-id="d17c8-114">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="d17c8-115">Elle est représentée dans le modèle d’objet WCF par la <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="d17c8-115">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="d17c8-116">Une classe <xref:System.ServiceModel.EndpointAddress> contient :</span><span class="sxs-lookup"><span data-stu-id="d17c8-116">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="d17c8-117">Une propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A>, qui représente l'adresse du service.</span><span class="sxs-lookup"><span data-stu-id="d17c8-117">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="d17c8-118">Une propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> qui représente l’identité de sécurité du service et une collection d’en-tête de message facultatifs.</span><span class="sxs-lookup"><span data-stu-id="d17c8-118">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="d17c8-119">Les en-têtes de message facultatifs sont utilisés pour fournir des informations d'adressage supplémentaires et plus détaillées afin d'identifier le point de terminaison ou d'interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="d17c8-119">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="d17c8-120">Pour plus d’informations, consultez [spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-120">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="d17c8-121">Liaison : la liaison spécifie le mode de communication avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d17c8-121">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="d17c8-122">notamment :</span><span class="sxs-lookup"><span data-stu-id="d17c8-122">This includes:</span></span>

  - <span data-ttu-id="d17c8-123">Le protocole de transport à utiliser (par exemple, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="d17c8-123">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="d17c8-124">L'encodage à utiliser pour les messages (par exemple, texte ou binaire).</span><span class="sxs-lookup"><span data-stu-id="d17c8-124">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="d17c8-125">Les exigences de sécurité nécessaires (par exemple, SSL ou la sécurité des messages SOAP).</span><span class="sxs-lookup"><span data-stu-id="d17c8-125">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="d17c8-126">Pour plus d’informations, consultez [vue d’ensemble des liaisons WCF](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-126">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="d17c8-127">Une liaison est représentée dans le modèle objet WCF par la classe de base abstraite <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="d17c8-127">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="d17c8-128">Pour la plupart des scénarios, les utilisateurs peuvent utiliser l'une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="d17c8-128">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="d17c8-129">Pour plus d’informations, consultez [liaisons fournies par le système](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-129">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="d17c8-130">Contrats : le contrat de service définit les fonctionnalités que le point de terminaison expose au client.</span><span class="sxs-lookup"><span data-stu-id="d17c8-130">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="d17c8-131">Un contrat spécifie :</span><span class="sxs-lookup"><span data-stu-id="d17c8-131">A contract specifies:</span></span>

  - <span data-ttu-id="d17c8-132">Quelles opérations peuvent être appelées par un client.</span><span class="sxs-lookup"><span data-stu-id="d17c8-132">What operations can be called by a client.</span></span>

  - <span data-ttu-id="d17c8-133">Le format du message.</span><span class="sxs-lookup"><span data-stu-id="d17c8-133">The form of the message.</span></span>

  - <span data-ttu-id="d17c8-134">Le type de paramètres d'entrée ou les données requis pour appeler l'opération.</span><span class="sxs-lookup"><span data-stu-id="d17c8-134">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="d17c8-135">Le type de traitement ou le message de réponse que le client peut attendre.</span><span class="sxs-lookup"><span data-stu-id="d17c8-135">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="d17c8-136">Pour plus d’informations sur la définition d’un contrat, consultez [conception de contrats de service](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-136">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="d17c8-137">Comportements : vous pouvez utiliser des comportements de point de terminaison pour personnaliser le comportement local du point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="d17c8-137">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="d17c8-138">Pour y parvenir, les comportements de point de terminaison participent au processus de création d’un Runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="d17c8-138">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="d17c8-139">Un exemple de comportement de point de terminaison est la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> qui vous permet de spécifier une adresse d'écoute différente de l'adresse SOAP ou WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="d17c8-139">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="d17c8-140">Pour plus d’informations, consultez [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-140">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="d17c8-141">Définition des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="d17c8-141">Defining Endpoints</span></span>

<span data-ttu-id="d17c8-142">L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration.</span><span class="sxs-lookup"><span data-stu-id="d17c8-142">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="d17c8-143">Pour plus d’informations, consultez [Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md) et [Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-143">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d17c8-144">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d17c8-144">In This Section</span></span>

<span data-ttu-id="d17c8-145">Cette section explique à quoi servent les liaisons, les points de terminaison et les adresses, indique comment configurer une liaison et un point de terminaison et montre comment utiliser le comportement `ClientVia` et la propriété `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="d17c8-145">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="d17c8-146">[Résoudre](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="d17c8-146">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="d17c8-147">Décrit comment les points de terminaison sont traités dans WCF.</span><span class="sxs-lookup"><span data-stu-id="d17c8-147">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="d17c8-148">[Liaisons](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d17c8-148">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="d17c8-149">Décrit comment les liaisons sont utilisées pour spécifier le transport, l’encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="d17c8-149">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="d17c8-150">[Contrats](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="d17c8-150">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="d17c8-151">Décrit comment les contrats définissent les méthodes d'un service.</span><span class="sxs-lookup"><span data-stu-id="d17c8-151">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="d17c8-152">[Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="d17c8-152">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="d17c8-153">Décrit comment créer un point de terminaison de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d17c8-153">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="d17c8-154">[Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="d17c8-154">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="d17c8-155">Décrit comment créer un point de terminaison de service dans le code.</span><span class="sxs-lookup"><span data-stu-id="d17c8-155">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="d17c8-156">[Comment : utiliser Svcutil.exe pour valider le code de service compilé](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="d17c8-156">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="d17c8-157">Décrit comment détecter les erreurs dans les implémentations et les configurations de service sans héberger le service à l’aide de l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d17c8-157">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d17c8-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d17c8-158">See also</span></span>

- [<span data-ttu-id="d17c8-159">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="d17c8-159">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="d17c8-160">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="d17c8-160">Extending Bindings</span></span>](../extending/extending-bindings.md)
