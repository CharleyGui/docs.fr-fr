---
title: Regroupement de messages mis en file d'attente dans une session
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185156"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="9018a-102">Regroupement de messages mis en file d'attente dans une session</span><span class="sxs-lookup"><span data-stu-id="9018a-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="9018a-103">Windows Communication Foundation (WCF) fournit une session qui vous permet de regrouper un ensemble de messages connexes pour le traitement par une seule application de réception.</span><span class="sxs-lookup"><span data-stu-id="9018a-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="9018a-104">Les messages qui font partie d’une session doivent faire partie de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="9018a-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="9018a-105">Étant donné que tous les messages font partie de la même transaction, si un message n’est pas traité, la session entière est restaurée.</span><span class="sxs-lookup"><span data-stu-id="9018a-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="9018a-106">Les sessions ont des comportements semblables en ce qui concerne les files d'attente de lettres mortes et les files d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="9018a-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="9018a-107">La propriété Durée de vie (Time to Live ou TTL) définie sur une liaison mise en file d'attente configurée pour les sessions est appliquée à la session dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="9018a-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="9018a-108">Si seulement quelques-uns des messages de la session sont envoyés avant l'expiration de la durée de vie, la session entière est placée dans la file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="9018a-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="9018a-109">De même, lorsque les messages d'une session ne parviennent pas à être envoyés à une application depuis la file d'attente de l'application, la session entière est placée dans la file d'attente de messages incohérents (si disponible).</span><span class="sxs-lookup"><span data-stu-id="9018a-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="9018a-110">Exemple de regroupement de messages</span><span class="sxs-lookup"><span data-stu-id="9018a-110">Message Grouping Example</span></span>  
 <span data-ttu-id="9018a-111">Un exemple où le regroupement des messages est utile est lors de la mise en œuvre d’une demande de traitement des commandes en tant que service WCF.</span><span class="sxs-lookup"><span data-stu-id="9018a-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="9018a-112">Par exemple, un client soumet à cette application une commande qui contient plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="9018a-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="9018a-113">Pour chaque élément, le client passe un appel au service, ce qui provoque l'envoi d'un message séparé.</span><span class="sxs-lookup"><span data-stu-id="9018a-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="9018a-114">Il est possible que le serveur A reçoive le premier élément et que le serveur B reçoive le deuxième élément.</span><span class="sxs-lookup"><span data-stu-id="9018a-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="9018a-115">Chaque fois qu'un élément est ajouté, le serveur qui traite cet élément doit rechercher la commande appropriée et lui ajouter l'élément, ce qui est peu efficace.</span><span class="sxs-lookup"><span data-stu-id="9018a-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="9018a-116">Vous rencontrez également de telles inefficacités avec un seul serveur gérant toutes les demandes, parce que le serveur doit faire le suivi de toutes les commandes en cours de traitement et déterminer à quelle commande le nouvel élément appartient.</span><span class="sxs-lookup"><span data-stu-id="9018a-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="9018a-117">Le regroupement de toutes les demandes pour une commande unique simplifie grandement l'implémentation d'une telle application.</span><span class="sxs-lookup"><span data-stu-id="9018a-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="9018a-118">L'application cliente envoie tous les éléments d'une commande unique dans une session, donc lorsque le service traite la commande, il traite la session entière en une fois.</span><span class="sxs-lookup"><span data-stu-id="9018a-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="9018a-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="9018a-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="9018a-120">Pour paramétrer un contrat de service pour qu'il utilise des sessions</span><span class="sxs-lookup"><span data-stu-id="9018a-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="9018a-121">Définissez un contrat de service qui requiert une session.</span><span class="sxs-lookup"><span data-stu-id="9018a-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="9018a-122">Faites-le <xref:System.ServiceModel.ServiceContractAttribute> avec l’attribut en spécifiant :</span><span class="sxs-lookup"><span data-stu-id="9018a-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="9018a-123">Marquez les opérations du contrat comme étant unidirectionnelles, parce que ces méthodes ne retournent rien.</span><span class="sxs-lookup"><span data-stu-id="9018a-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="9018a-124">Ceci est fait <xref:System.ServiceModel.OperationContractAttribute> avec l’attribut en spécifiant :</span><span class="sxs-lookup"><span data-stu-id="9018a-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="9018a-125">Implémentez le contrat de service et spécifiez un <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> de <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9018a-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9018a-126">Cela instancie le service une seule fois pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="9018a-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="9018a-127">Chaque opération de service requiert une transaction.</span><span class="sxs-lookup"><span data-stu-id="9018a-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="9018a-128">Spécifiez ceci avec l'attribut <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9018a-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="9018a-129">L’opération qui complète la transaction doit également affecter à <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="9018a-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. <span data-ttu-id="9018a-130">Configurez un point de terminaison qui utilise la liaison `NetMsmqBinding` fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="9018a-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="9018a-131">Créez une file d'attente transactionnelle en utilisant <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="9018a-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="9018a-132">Vous pouvez également créer la file d'attente en utilisant Message Queuing (MSMQ) ou MMC.</span><span class="sxs-lookup"><span data-stu-id="9018a-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="9018a-133">Dans ce cas, créez une file d’attente transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="9018a-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="9018a-134">Créez un hôte de service pour le service en utilisant <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9018a-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="9018a-135">Ouvrez l'hôte de service pour rendre le service disponible.</span><span class="sxs-lookup"><span data-stu-id="9018a-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="9018a-136">Fermez l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="9018a-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="9018a-137">Pour installer un client</span><span class="sxs-lookup"><span data-stu-id="9018a-137">To set up a client</span></span>  
  
1. <span data-ttu-id="9018a-138">Créez une étendue de transaction pour écrire dans la file d’attente transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="9018a-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="9018a-139">Créez le client WCF à l’aide de [l’outil utilitaire ServiceModel Metadata (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="9018a-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="9018a-140">Passez la commande.</span><span class="sxs-lookup"><span data-stu-id="9018a-140">Place the order.</span></span>  
  
4. <span data-ttu-id="9018a-141">Fermez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="9018a-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9018a-142"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9018a-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9018a-143">Description</span><span class="sxs-lookup"><span data-stu-id="9018a-143">Description</span></span>  
 <span data-ttu-id="9018a-144">L'exemple suivant fournit le code pour le service `IProcessOrder` et pour un client qui utilise ce service.</span><span class="sxs-lookup"><span data-stu-id="9018a-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="9018a-145">Il montre comment WCF utilise des sessions en file d’attente pour fournir le comportement de groupement.</span><span class="sxs-lookup"><span data-stu-id="9018a-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="9018a-146">Code du service</span><span class="sxs-lookup"><span data-stu-id="9018a-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="9018a-147">Code du client</span><span class="sxs-lookup"><span data-stu-id="9018a-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="9018a-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9018a-148">See also</span></span>

- [<span data-ttu-id="9018a-149">Sessions and Queues</span><span class="sxs-lookup"><span data-stu-id="9018a-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="9018a-150">Vue d'ensemble des files d'attente</span><span class="sxs-lookup"><span data-stu-id="9018a-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
