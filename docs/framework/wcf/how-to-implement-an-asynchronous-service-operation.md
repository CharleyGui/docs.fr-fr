---
title: 'Comment : implémenter une opération de service asynchrone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320955"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="09472-102">Comment : implémenter une opération de service asynchrone</span><span class="sxs-lookup"><span data-stu-id="09472-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="09472-103">Dans les applications Windows Communication Foundation (WCF), une opération de service peut être implémentée de façon asynchrone ou synchrone sans dicter au client comment l’appeler.</span><span class="sxs-lookup"><span data-stu-id="09472-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="09472-104">Par exemple, les opérations de service asynchrones peuvent être appelées de façon synchrone, et les opérations de service synchrones peuvent être appelées de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="09472-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="09472-105">Pour obtenir un exemple qui montre comment appeler une opération de façon asynchrone dans une application cliente, consultez [Comment : appeler des opérations de service de façon asynchrone](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="09472-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="09472-106">Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [conception de contrats de service](designing-service-contracts.md) et [opérations synchrones et asynchrones](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="09472-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="09472-107">Cette rubrique décrit la structure de base d'une opération de service asynchrone, le code n'est pas complet.</span><span class="sxs-lookup"><span data-stu-id="09472-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="09472-108">Pour obtenir un exemple complet du côté du service et du client, consultez [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="09472-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="09472-109">Implémenter une opération de service de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="09472-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="09472-110">Dans votre contrat de service, déclarez une paire de méthodes asynchrones conformément aux règles de design asynchrone .NET.</span><span class="sxs-lookup"><span data-stu-id="09472-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="09472-111">La méthode `Begin` prend un paramètre, un objet de rappel et un objet d'état, puis retourne <xref:System.IAsyncResult?displayProperty=nameWithType> et une méthode `End` correspondante qui prend <xref:System.IAsyncResult?displayProperty=nameWithType> et retourne la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="09472-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="09472-112">Pour plus d’informations sur les appels asynchrones, consultez [modèles de conception de programmation asynchrone](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="09472-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="09472-113">Marquez la méthode `Begin` de la paire de méthodes asynchrones avec l'attribut <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> et affectez <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="09472-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="09472-114">Par exemple, le code suivant exécute les étapes 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="09472-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="09472-115">Implémentez la paire de méthodes `Begin/End` dans votre classe de service conformément aux règles de design asynchrone.</span><span class="sxs-lookup"><span data-stu-id="09472-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="09472-116">Par exemple, l'exemple de code suivant présente une implémentation dans laquelle une chaîne est écrite dans la console, à la fois dans les parties `Begin` et `End` de l'opération de service asynchrone, et la valeur de retour de l'opération `End` est retournée au client.</span><span class="sxs-lookup"><span data-stu-id="09472-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="09472-117">Pour obtenir un exemple de code complet, consultez la section Exemple.</span><span class="sxs-lookup"><span data-stu-id="09472-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="09472-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="09472-118">Example</span></span>  
 <span data-ttu-id="09472-119">Les exemples de code suivants présentent :</span><span class="sxs-lookup"><span data-stu-id="09472-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="09472-120">Une interface de contrat de service avec :</span><span class="sxs-lookup"><span data-stu-id="09472-120">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="09472-121">Une opération `SampleMethod` synchrone.</span><span class="sxs-lookup"><span data-stu-id="09472-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="09472-122">Une opération `BeginSampleMethod` asynchrone.</span><span class="sxs-lookup"><span data-stu-id="09472-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="09472-123">Paire d’opérations asynchrones `BeginServiceAsyncMethod` @ no__t-1 @ no__t-2.</span><span class="sxs-lookup"><span data-stu-id="09472-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="09472-124">Une implémentation de service utilisant un objet <xref:System.IAsyncResult?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09472-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="09472-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09472-125">See also</span></span>

- [<span data-ttu-id="09472-126">Conception de contrats de service</span><span class="sxs-lookup"><span data-stu-id="09472-126">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="09472-127">Opérations synchrones et asynchrones</span><span class="sxs-lookup"><span data-stu-id="09472-127">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
