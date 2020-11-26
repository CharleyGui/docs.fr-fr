---
title: Traitement ordonné des messages en mode de concurrence simple
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: d70087a6dc1501f9a7f7ed057eae3dad181761ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248017"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="3bf3f-102">Traitement ordonné des messages en mode de concurrence simple</span><span class="sxs-lookup"><span data-stu-id="3bf3f-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>

<span data-ttu-id="3bf3f-103">WCF ne fournit aucune garantie quant à l’ordre dans lequel les messages sont traités, à moins que le canal sous-jacent soit de session.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="3bf3f-104">Par exemple, un service WCF qui utilise MsmqInputChannel, qui n’est pas un canal de session, ne parviendra pas à traiter les messages dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="3bf3f-105">Dans certains cas, un développeur peut souhaiter le comportement de traitement de l’ordre, mais ne souhaite pas utiliser les sessions.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="3bf3f-106">Cette rubrique décrit comment configurer ce comportement lorsqu'un service s'exécute en mode de concurrence simple.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="3bf3f-107">Traitement des messages dans l'ordre</span><span class="sxs-lookup"><span data-stu-id="3bf3f-107">In-order Message Processing</span></span>  

 <span data-ttu-id="3bf3f-108">Un nouvel attribut nommé <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a été ajouté à la classe <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="3bf3f-109">Lorsque <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a la valeur true et <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a la valeur <xref:System.ServiceModel.ConcurrencyMode.Single> les messages envoyés au service sont traités dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="3bf3f-110">L'extrait de code suivant illustre comment définir ces attributs.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="3bf3f-111">Si une autre valeur est affectée à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, une exception <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="3bf3f-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf3f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bf3f-112">See also</span></span>

- [<span data-ttu-id="3bf3f-113">Sessions, instanciation et accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="3bf3f-113">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="3bf3f-114">Concurrency</span><span class="sxs-lookup"><span data-stu-id="3bf3f-114">Concurrency</span></span>](../samples/concurrency.md)
