---
title: "Comment : échanger des messages en file d'attente avec des points de terminaison WCF"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 7da7ba1b680bae2b29eeff8fe669e097ea8eda32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595373"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="3a188-102">Comment : échanger des messages en file d'attente avec des points de terminaison WCF</span><span class="sxs-lookup"><span data-stu-id="3a188-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="3a188-103">Les files d’attente garantissent que la messagerie fiable peut se produire entre un client et un service de Windows Communication Foundation (WCF), même si le service n’est pas disponible au moment de la communication.</span><span class="sxs-lookup"><span data-stu-id="3a188-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="3a188-104">Les procédures suivantes montrent comment garantir une communication durable entre un client et un service à l’aide de la liaison mise en file d’attente standard lors de l’implémentation du service WCF.</span><span class="sxs-lookup"><span data-stu-id="3a188-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="3a188-105">Cette section explique comment utiliser pour la communication mise en <xref:System.ServiceModel.NetMsmqBinding> file d’attente entre un client WCF et un service WCF.</span><span class="sxs-lookup"><span data-stu-id="3a188-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="3a188-106">Pour utiliser la mise en file d'attente dans un service WCF</span><span class="sxs-lookup"><span data-stu-id="3a188-106">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="3a188-107">Définissez un contrat de service utilisant une interface marquée avec <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3a188-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="3a188-108">Marquez les opérations dans l'interface qui font partie du contrat de service avec <xref:System.ServiceModel.OperationContractAttribute> et définissez-les comme unidirectionnelles car aucune réponse n'est retournée à la méthode.</span><span class="sxs-lookup"><span data-stu-id="3a188-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="3a188-109">Le code ci-dessous fournit un exemple de contrat de service et sa définition d'opération.</span><span class="sxs-lookup"><span data-stu-id="3a188-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="3a188-110">Lorsque le contrat de service passe des types définis par l'utilisateur, vous devez définir des contrats de données pour ces types.</span><span class="sxs-lookup"><span data-stu-id="3a188-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="3a188-111">Le code suivant présente deux contrats de données, `PurchaseOrder` et `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="3a188-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="3a188-112">Ces deux types définissent les données qui sont envoyées au service.</span><span class="sxs-lookup"><span data-stu-id="3a188-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="3a188-113">(Notez que les classes qui définissent ce contrat de données définissent également plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="3a188-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="3a188-114">Ces méthodes ne sont pas considérées comme des parties intégrantes du contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3a188-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="3a188-115">Seuls les membres déclarés avec l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> font partie du contrat de données.)</span><span class="sxs-lookup"><span data-stu-id="3a188-115">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="3a188-116">Implémentez dans une classe les méthodes du contrat de service définies dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="3a188-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="3a188-117">Notez <xref:System.ServiceModel.OperationBehaviorAttribute> qui est placé sur la méthode `SubmitPurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="3a188-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="3a188-118">Cela indique que cette opération doit être appelée au sein d'une transaction et que la transaction se termine automatiquement à la fin de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3a188-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="3a188-119">Créez une file d'attente transactionnelle en utilisant <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="3a188-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="3a188-120">Vous pouvez éventuellement décider de créer la file d'attente à l'aide de la console MMC (Microsoft Management Console) MSMQ (Microsoft Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="3a188-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="3a188-121">Dans ce cas, assurez-vous de créer une file d’attente transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="3a188-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="3a188-122">Définissez un <xref:System.ServiceModel.Description.ServiceEndpoint> dans la configuration qui spécifie l’adresse de service et utilise la liaison <xref:System.ServiceModel.NetMsmqBinding> standard.</span><span class="sxs-lookup"><span data-stu-id="3a188-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="3a188-123">Pour plus d’informations sur l’utilisation de la configuration WCF, consultez [Configuration des services WCF](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="3a188-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="3a188-124">Créez un hôte pour le service `OrderProcessing` à l'aide de <xref:System.ServiceModel.ServiceHost> qui lit les messages de la file d'attente et les traite.</span><span class="sxs-lookup"><span data-stu-id="3a188-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="3a188-125">Ouvrez l'hôte de service pour rendre le service disponible.</span><span class="sxs-lookup"><span data-stu-id="3a188-125">Open the service host to make the service available.</span></span> <span data-ttu-id="3a188-126">Affichez un message qui indique à l'utilisateur d'appuyer sur une touche quelconque pour terminer le service.</span><span class="sxs-lookup"><span data-stu-id="3a188-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="3a188-127">Appelez `ReadLine` pour attendre l'appui sur la touche, puis fermez le service.</span><span class="sxs-lookup"><span data-stu-id="3a188-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="3a188-128">Pour créer un client pour le service mis en file d'attente</span><span class="sxs-lookup"><span data-stu-id="3a188-128">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="3a188-129">L’exemple suivant montre comment exécuter l’application d’hébergement et utiliser l’outil Svcutil. exe pour créer le client WCF.</span><span class="sxs-lookup"><span data-stu-id="3a188-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="3a188-130">Définissez un <xref:System.ServiceModel.Description.ServiceEndpoint> dans la configuration qui spécifie l’adresse et utilise la liaison <xref:System.ServiceModel.NetMsmqBinding> standard, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3a188-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="3a188-131">Créez une étendue de transaction pour écrire dans la file d’attente transactionnelle, appelez l' `SubmitPurchaseOrder` opération et fermez le client WCF, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3a188-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="3a188-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a188-132">Example</span></span>  
 <span data-ttu-id="3a188-133">Les exemples suivants montrent le code de service, l'application d'hébergement, le fichier App.config et le code client inclus pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="3a188-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="3a188-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a188-134">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="3a188-135">Transacted MSMQ Binding</span><span class="sxs-lookup"><span data-stu-id="3a188-135">Transacted MSMQ Binding</span></span>](../samples/transacted-msmq-binding.md)
- [<span data-ttu-id="3a188-136">Mise en file d'attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="3a188-136">Queuing in WCF</span></span>](queuing-in-wcf.md)
- [<span data-ttu-id="3a188-137">Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing</span><span class="sxs-lookup"><span data-stu-id="3a188-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="3a188-138">Windows Communication Foundation to Message Queuing</span><span class="sxs-lookup"><span data-stu-id="3a188-138">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="3a188-139">Installation de Message Queuing (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="3a188-139">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="3a188-140">Message Queuing to Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3a188-140">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="3a188-141">Message Security over Message Queuing</span><span class="sxs-lookup"><span data-stu-id="3a188-141">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
