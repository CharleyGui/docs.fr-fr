---
title: 'Procédure : créer un contrat duplex'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: c603694bca82cfc5852c875946f18f9782209e48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638778"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="0fc78-102">Procédure : créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="0fc78-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="0fc78-103">Cette rubrique décrit les étapes de base pour créer des méthodes qui utilisent un contrat duplex (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="0fc78-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="0fc78-104">Un contrat duplex autorise les clients et les serveurs à communiquer entre eux indépendamment de sorte que l'un puisse initier des appels à l'autre.</span><span class="sxs-lookup"><span data-stu-id="0fc78-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="0fc78-105">Le contrat duplex est un des trois modèles de message disponibles aux services Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0fc78-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="0fc78-106">Les deux autres modèles de message sont unidirectionnels et demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="0fc78-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="0fc78-107">Un contrat duplex se compose de deux contrats unidirectionnels entre le client et le serveur et ne requiert pas que les appels de méthode soient corrélés.</span><span class="sxs-lookup"><span data-stu-id="0fc78-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="0fc78-108">Utilisez ce type de contrat lorsque votre service doit demander au client plus d'informations ou déclencher explicitement des événements sur le client.</span><span class="sxs-lookup"><span data-stu-id="0fc78-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="0fc78-109">Pour plus d’informations sur la création d’une application cliente pour un contrat duplex, consultez [Comment : Accéder aux Services avec un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="0fc78-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="0fc78-110">Pour obtenir un exemple fonctionnel, consultez le [Duplex](../../../../docs/framework/wcf/samples/duplex.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="0fc78-110">For a working sample, see the [Duplex](../../../../docs/framework/wcf/samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="0fc78-111">Pour créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="0fc78-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="0fc78-112">Créez l'interface constitutive du côté serveur du contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="0fc78-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="0fc78-113">Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.</span><span class="sxs-lookup"><span data-stu-id="0fc78-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="0fc78-114">Déclarez les signatures de méthode dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="0fc78-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="0fc78-115">Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque signature de méthode qui doit faire partie du contrat public.</span><span class="sxs-lookup"><span data-stu-id="0fc78-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="0fc78-116">Créez l'interface de rappel qui définit le jeu des opérations que le service peut appeler sur le client.</span><span class="sxs-lookup"><span data-stu-id="0fc78-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="0fc78-117">Déclarez les signatures de méthode dans l'interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="0fc78-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="0fc78-118">Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque signature de méthode qui doit faire partie du contrat public.</span><span class="sxs-lookup"><span data-stu-id="0fc78-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="0fc78-119">Liez les deux interfaces dans un contrat duplex en affectant à la propriété <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> dans l'interface primaire le type de l'interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="0fc78-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="0fc78-120">Pour appeler des méthodes sur le client</span><span class="sxs-lookup"><span data-stu-id="0fc78-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="0fc78-121">Dans l'implémentation de service du contrat principal, déclarez une variable pour l'interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="0fc78-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="0fc78-122">Affectez à la variable la référence d'objet retournée par la méthode <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> de la classe <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="0fc78-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="0fc78-123">Appelez les méthodes définies par l'interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="0fc78-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc78-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fc78-124">Example</span></span>  
 <span data-ttu-id="0fc78-125">L'exemple de code suivant illustre la communication duplex.</span><span class="sxs-lookup"><span data-stu-id="0fc78-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="0fc78-126">Le contrat du service contient des opérations de service pour avancer et reculer.</span><span class="sxs-lookup"><span data-stu-id="0fc78-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="0fc78-127">Le contrat du client contient une opération de service pour indiquer sa position.</span><span class="sxs-lookup"><span data-stu-id="0fc78-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="0fc78-128">Appliquer les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> permet la génération automatique de définitions de contrat de service dans WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="0fc78-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="0fc78-129">Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour récupérer le document WSDL et de code (facultatif) et de configuration pour un client.</span><span class="sxs-lookup"><span data-stu-id="0fc78-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="0fc78-130">Les points de terminaison qui exposent des services duplex doivent être sécurisés.</span><span class="sxs-lookup"><span data-stu-id="0fc78-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="0fc78-131">Lorsqu'un service reçoit un message duplex, il consulte l'élément ReplyTo dans ce message entrant afin de déterminer où envoyer la réponse.</span><span class="sxs-lookup"><span data-stu-id="0fc78-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="0fc78-132">Si le canal n'est pas sécurisé, un client non fiable peut envoyer un message malveillant avec le ReplyTo d'un ordinateur cible, ce qui peut entraîner à un déni de service de l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="0fc78-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="0fc78-133">Avec les messages de réponse/demande normaux, ce problème ne se pose pas, parce que le ReplyTo est ignoré et la réponse est envoyée sur le canal sur lequel le message d'origine est arrivé.</span><span class="sxs-lookup"><span data-stu-id="0fc78-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc78-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fc78-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="0fc78-135">Guide pratique pour Access Services avec un contrat Duplex</span><span class="sxs-lookup"><span data-stu-id="0fc78-135">How to: Access Services with a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="0fc78-136">Duplex</span><span class="sxs-lookup"><span data-stu-id="0fc78-136">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="0fc78-137">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="0fc78-137">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="0fc78-138">Guide pratique pour Définir un contrat de Service</span><span class="sxs-lookup"><span data-stu-id="0fc78-138">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="0fc78-139">Session</span><span class="sxs-lookup"><span data-stu-id="0fc78-139">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)
