---
title: 'Procédure : Appeler des opérations de service WCF de façon asynchrone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2d075bfebf7b5cbd2b2ce031a1c3855a925405a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964030"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="9dc0d-102">Procédure : Appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="9dc0d-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="9dc0d-103">Cette rubrique présente comment un client peut accéder de façon asynchrone à une opération de service.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="9dc0d-104">Le service dans cette rubrique implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="9dc0d-105">Le client peut appeler les opérations sur cette interface de manière asynchrone à l'aide du modèle d'appel asynchrone commandé par événement.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="9dc0d-106">(Pour plus d’informations sur le modèle d’appel asynchrone basé sur les événements, consultez [programmation multithread avec le modèle asynchrone basé sur les événements](https://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="9dc0d-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="9dc0d-107">Pour obtenir un exemple qui montre comment implémenter une opération de façon asynchrone dans un service [, consultez Procédure: Implémentez une opération](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)de service asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="9dc0d-108">Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [opérations synchrones et asynchrones](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9dc0d-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dc0d-109">Le modèle d'appel asynchrone commandé par événement n'est pas pris en charge lorsqu'il utilise un <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="9dc0d-110">Pour plus d’informations sur l’exécution d' <xref:System.ServiceModel.ChannelFactory%601>appels asynchrones à l’aide de, consultez [procédure: Appeler des opérations de façon asynchrone à l'](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)aide d’une fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="9dc0d-111">Procédure</span><span class="sxs-lookup"><span data-stu-id="9dc0d-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="9dc0d-112">Pour appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="9dc0d-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="9dc0d-113">Exécutez l’outil [ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec `/async` les options de `/tcv:Version35` commande et, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="9dc0d-114">Cela génère, en plus des opérations asynchrones synchrones et standard basées sur les délégués, une classe de client WCF qui contient:</span><span class="sxs-lookup"><span data-stu-id="9dc0d-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="9dc0d-115">Deux opérations`operationName` de <> `Async` pour une utilisation avec l’approche d’appel asynchrone basée sur les événements.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="9dc0d-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9dc0d-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="9dc0d-117">Événements d’opération terminés de la`operationName` forme <> `Completed` pour une utilisation avec l’approche d’appel asynchrone basée sur les événements.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="9dc0d-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9dc0d-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="9dc0d-119"><xref:System.EventArgs?displayProperty=nameWithType>types pour chaque opération (de la forme <`operationName`>`CompletedEventArgs`) à utiliser avec l’approche de l’appel asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="9dc0d-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9dc0d-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="9dc0d-121">Dans l'application d'appel, créez une méthode de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="9dc0d-122">Avant d’appeler l’opération, utilisez un nouveau générique <xref:System.EventHandler%601?displayProperty=nameWithType> de type <`operationName` `Completed` > `EventArgs` pour ajouter la méthode de gestionnaire (créée à l’étape précédente) à l'`operationName` événement <.></span><span class="sxs-lookup"><span data-stu-id="9dc0d-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="9dc0d-123">Appelez ensuite la méthode`operationName` <> `Async` .</span><span class="sxs-lookup"><span data-stu-id="9dc0d-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="9dc0d-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9dc0d-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="9dc0d-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="9dc0d-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dc0d-126">Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="9dc0d-127">Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>. Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="9dc0d-128">Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="9dc0d-129">Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="9dc0d-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9dc0d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dc0d-130">See also</span></span>

- [<span data-ttu-id="9dc0d-131">Guide pratique : Implémenter une opération de service asynchrone</span><span class="sxs-lookup"><span data-stu-id="9dc0d-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
