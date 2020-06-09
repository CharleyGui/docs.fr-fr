---
title: 'Points de terminaison : adresses, liaisons et contrats'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593514"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="a85db-102">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="a85db-102">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="a85db-103">Toutes les communications avec un service Windows Communication Foundation (WCF) se produisent via les *points de terminaison* du service.</span><span class="sxs-lookup"><span data-stu-id="a85db-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="a85db-104">Les points de terminaison fournissent aux clients l’accès aux fonctionnalités offertes par un service WCF.</span><span class="sxs-lookup"><span data-stu-id="a85db-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="a85db-105">Chaque point de terminaison se compose de quatre propriétés :</span><span class="sxs-lookup"><span data-stu-id="a85db-105">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="a85db-106">Une adresse qui indique où rechercher le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a85db-106">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="a85db-107">Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a85db-107">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="a85db-108">Un contrat qui identifie les opérations disponibles.</span><span class="sxs-lookup"><span data-stu-id="a85db-108">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="a85db-109">L'ensemble des comportements qui spécifient les détails d'implémentation locaux du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a85db-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="a85db-110">Cette rubrique traite de cette structure de point de terminaison et explique comment elle est représentée dans le modèle d’objet WCF.</span><span class="sxs-lookup"><span data-stu-id="a85db-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="a85db-111">Structure d'un point de terminaison</span><span class="sxs-lookup"><span data-stu-id="a85db-111">The Structure of an Endpoint</span></span>

<span data-ttu-id="a85db-112">Chaque point de terminaison comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a85db-112">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="a85db-113">Adresse : l'adresse identifie le point de terminaison de manière unique et indique aux consommateurs potentiels l'emplacement du service.</span><span class="sxs-lookup"><span data-stu-id="a85db-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="a85db-114">Elle est représentée dans le modèle d’objet WCF par la <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="a85db-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="a85db-115">Une classe <xref:System.ServiceModel.EndpointAddress> contient :</span><span class="sxs-lookup"><span data-stu-id="a85db-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="a85db-116">Une propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A>, qui représente l'adresse du service.</span><span class="sxs-lookup"><span data-stu-id="a85db-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="a85db-117">Une propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> qui représente l’identité de sécurité du service et une collection d’en-tête de message facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a85db-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="a85db-118">Les en-têtes de message facultatifs sont utilisés pour fournir des informations d'adressage supplémentaires et plus détaillées afin d'identifier le point de terminaison ou d'interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="a85db-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="a85db-119">Pour plus d’informations, consultez [spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-119">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="a85db-120">Liaison : la liaison spécifie le mode de communication avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a85db-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="a85db-121">notamment :</span><span class="sxs-lookup"><span data-stu-id="a85db-121">This includes:</span></span>

  - <span data-ttu-id="a85db-122">Le protocole de transport à utiliser (par exemple, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="a85db-122">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="a85db-123">L'encodage à utiliser pour les messages (par exemple, texte ou binaire).</span><span class="sxs-lookup"><span data-stu-id="a85db-123">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="a85db-124">Les exigences de sécurité nécessaires (par exemple, SSL ou la sécurité des messages SOAP).</span><span class="sxs-lookup"><span data-stu-id="a85db-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="a85db-125">Pour plus d’informations, consultez [vue d’ensemble des liaisons WCF](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-125">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="a85db-126">Une liaison est représentée dans le modèle objet WCF par la classe de base abstraite <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="a85db-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="a85db-127">Pour la plupart des scénarios, les utilisateurs peuvent utiliser l'une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="a85db-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="a85db-128">Pour plus d’informations, consultez [liaisons fournies par le système](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-128">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="a85db-129">Contrats : le contrat de service définit les fonctionnalités que le point de terminaison expose au client.</span><span class="sxs-lookup"><span data-stu-id="a85db-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="a85db-130">Un contrat spécifie :</span><span class="sxs-lookup"><span data-stu-id="a85db-130">A contract specifies:</span></span>

  - <span data-ttu-id="a85db-131">Quelles opérations peuvent être appelées par un client.</span><span class="sxs-lookup"><span data-stu-id="a85db-131">What operations can be called by a client.</span></span>

  - <span data-ttu-id="a85db-132">Le format du message.</span><span class="sxs-lookup"><span data-stu-id="a85db-132">The form of the message.</span></span>

  - <span data-ttu-id="a85db-133">Le type de paramètres d'entrée ou les données requis pour appeler l'opération.</span><span class="sxs-lookup"><span data-stu-id="a85db-133">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="a85db-134">Le type de traitement ou le message de réponse que le client peut attendre.</span><span class="sxs-lookup"><span data-stu-id="a85db-134">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="a85db-135">Pour plus d’informations sur la définition d’un contrat, consultez [conception de contrats de service](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-135">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="a85db-136">Comportements : vous pouvez utiliser des comportements de point de terminaison pour personnaliser le comportement local du point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="a85db-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="a85db-137">Pour y parvenir, les comportements de point de terminaison participent au processus de création d’un Runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="a85db-137">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="a85db-138">Un exemple de comportement de point de terminaison est la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> qui vous permet de spécifier une adresse d'écoute différente de l'adresse SOAP ou WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="a85db-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="a85db-139">Pour plus d’informations, consultez [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-139">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="a85db-140">Définition des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="a85db-140">Defining Endpoints</span></span>

<span data-ttu-id="a85db-141">L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration.</span><span class="sxs-lookup"><span data-stu-id="a85db-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="a85db-142">Pour plus d’informations, consultez [Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md) et [Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-142">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a85db-143">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a85db-143">In This Section</span></span>

<span data-ttu-id="a85db-144">Cette section explique à quoi servent les liaisons, les points de terminaison et les adresses, indique comment configurer une liaison et un point de terminaison et montre comment utiliser le comportement `ClientVia` et la propriété `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="a85db-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="a85db-145">[Résoudre](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="a85db-145">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="a85db-146">Décrit comment les points de terminaison sont traités dans WCF.</span><span class="sxs-lookup"><span data-stu-id="a85db-146">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="a85db-147">[Liaisons](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a85db-147">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="a85db-148">Décrit comment les liaisons sont utilisées pour spécifier le transport, l’encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="a85db-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="a85db-149">[Contrats](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="a85db-149">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="a85db-150">Décrit comment les contrats définissent les méthodes d'un service.</span><span class="sxs-lookup"><span data-stu-id="a85db-150">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="a85db-151">[Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="a85db-151">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="a85db-152">Décrit comment créer un point de terminaison de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a85db-152">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="a85db-153">[Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="a85db-153">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="a85db-154">Décrit comment créer un point de terminaison de service dans le code.</span><span class="sxs-lookup"><span data-stu-id="a85db-154">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="a85db-155">[Comment : utiliser Svcutil. exe pour valider le code de service compilé](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="a85db-155">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="a85db-156">Décrit comment détecter les erreurs dans les implémentations et les configurations de service sans héberger le service à l’aide de l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a85db-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a85db-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a85db-157">See also</span></span>

- [<span data-ttu-id="a85db-158">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="a85db-158">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="a85db-159">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a85db-159">Extending Bindings</span></span>](../extending/extending-bindings.md)
