---
title: 'Comment : appeler des opérations de service WCF de façon asynchrone'
description: Découvrez comment créer un client WCF qui peut accéder de façon asynchrone à une opération de service à l’aide du modèle d’appel asynchrone piloté par les événements.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: aa31f64473111800f4cd01907a0446c94f368456
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247232"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="60d4f-103">Comment : appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="60d4f-103">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="60d4f-104">Cet article explique comment un client peut accéder de façon asynchrone à une opération de service.</span><span class="sxs-lookup"><span data-stu-id="60d4f-104">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="60d4f-105">Dans cet article, le service implémente l' `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="60d4f-105">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="60d4f-106">Le client peut appeler les opérations sur cette interface de manière asynchrone à l'aide du modèle d'appel asynchrone commandé par événement.</span><span class="sxs-lookup"><span data-stu-id="60d4f-106">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="60d4f-107">(Pour plus d’informations sur le modèle d’appel asynchrone basé sur les événements, consultez [programmation multithread avec le modèle asynchrone basé sur les événements](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="60d4f-107">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="60d4f-108">Pour obtenir un exemple qui montre comment implémenter une opération de façon asynchrone dans un service, consultez [Comment : implémenter une opération de service asynchrone](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="60d4f-108">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="60d4f-109">Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [opérations synchrones et asynchrones](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="60d4f-109">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60d4f-110">Le modèle d'appel asynchrone commandé par événement n'est pas pris en charge lorsqu'il utilise un <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="60d4f-110">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="60d4f-111">Pour plus d’informations sur l’exécution d’appels asynchrones à l’aide de <xref:System.ServiceModel.ChannelFactory%601> , consultez [Comment : appeler des opérations de façon asynchrone à l’aide d’une fabrique de canaux](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="60d4f-111">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="60d4f-112">Procédure</span><span class="sxs-lookup"><span data-stu-id="60d4f-112">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="60d4f-113">Pour appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="60d4f-113">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="60d4f-114">Exécutez l’outil [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) avec les `/async` options de `/tcv:Version35` commande et, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="60d4f-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="60d4f-115">Cela génère, en plus des opérations asynchrones synchrones et standard basées sur les délégués, une classe de client WCF qui contient :</span><span class="sxs-lookup"><span data-stu-id="60d4f-115">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="60d4f-116">Deux `operationName` > `Async` opérations de <pour une utilisation avec l’approche d’appel asynchrone basée sur les événements.</span><span class="sxs-lookup"><span data-stu-id="60d4f-116">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="60d4f-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60d4f-117">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="60d4f-118">Événements d’opération terminés de la forme <`operationName` > `Completed` pour une utilisation avec l’approche d’appel asynchrone basée sur les événements.</span><span class="sxs-lookup"><span data-stu-id="60d4f-118">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="60d4f-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60d4f-119">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="60d4f-120"><xref:System.EventArgs?displayProperty=nameWithType>types pour chaque opération (de la forme <`operationName` > `CompletedEventArgs` ) à utiliser avec l’approche de l’appel asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="60d4f-120"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="60d4f-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60d4f-121">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="60d4f-122">Dans l'application d'appel, créez une méthode de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="60d4f-122">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="60d4f-123">Avant d’appeler l’opération, utilisez un nouveau générique <xref:System.EventHandler%601?displayProperty=nameWithType> de type <`operationName` > `EventArgs` pour ajouter la méthode de gestionnaire (créée à l’étape précédente) à l' `operationName` > `Completed` événement <.</span><span class="sxs-lookup"><span data-stu-id="60d4f-123">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="60d4f-124">Appelez ensuite la `operationName` > `Async` méthode <.</span><span class="sxs-lookup"><span data-stu-id="60d4f-124">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="60d4f-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60d4f-125">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="60d4f-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="60d4f-126">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60d4f-127">Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="60d4f-127">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="60d4f-128">Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>. Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="60d4f-128">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="60d4f-129">Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="60d4f-129">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="60d4f-130">Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="60d4f-130">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="60d4f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60d4f-131">See also</span></span>

- [<span data-ttu-id="60d4f-132">Comment : implémenter une opération de service asynchrone</span><span class="sxs-lookup"><span data-stu-id="60d4f-132">How to: Implement an Asynchronous Service Operation</span></span>](../how-to-implement-an-asynchronous-service-operation.md)
