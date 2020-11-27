---
title: Corrélation duplex durable
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: eb879c583b4454cd0062396d86e157a90db4652f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254231"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="b8630-102">Corrélation duplex durable</span><span class="sxs-lookup"><span data-stu-id="b8630-102">Durable Duplex Correlation</span></span>

<span data-ttu-id="b8630-103">La corrélation duplex durable, également appelée corrélation de rappel, est utile lorsqu’un service de workflow a besoin d’envoyer un rappel à l’appelant initial.</span><span class="sxs-lookup"><span data-stu-id="b8630-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="b8630-104">Contrairement au duplex WCF, le rappel peut arriver à n’importe quel moment du futur et n’est pas lié au même canal ni à la durée de vie du canal ; la seule exigence est que l’appelant ait un point de terminaison actif qui écoute le message de rappel.</span><span class="sxs-lookup"><span data-stu-id="b8630-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="b8630-105">Cela permet à deux services de workflow de communiquer dans une conversation de longue durée.</span><span class="sxs-lookup"><span data-stu-id="b8630-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="b8630-106">Cette rubrique présente une vue d'ensemble de la corrélation duplex durable.</span><span class="sxs-lookup"><span data-stu-id="b8630-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="b8630-107">Utilisation de la corrélation duplex durable</span><span class="sxs-lookup"><span data-stu-id="b8630-107">Using Durable Duplex Correlation</span></span>  

 <span data-ttu-id="b8630-108">Pour utiliser la corrélation duplex durable, les deux services doivent utiliser une liaison contextuelle qui prend en charge les opérations bidirectionnelles, telle que <xref:System.ServiceModel.NetTcpContextBinding> ou <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="b8630-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="b8630-109">Le service d’appel enregistre une propriété <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> avec la liaison souhaitée sur son <xref:System.ServiceModel.Endpoint> client.</span><span class="sxs-lookup"><span data-stu-id="b8630-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="b8630-110">Le service de réception reçoit ces données dans l'appel initial, puis les utilise sur son propre <xref:System.ServiceModel.Endpoint> dans l'activité <xref:System.ServiceModel.Activities.Send> qui effectue le rappel vers le service d'appel.</span><span class="sxs-lookup"><span data-stu-id="b8630-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="b8630-111">Dans cet exemple, deux services communiquent entre eux.</span><span class="sxs-lookup"><span data-stu-id="b8630-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="b8630-112">Le premier service appelle une méthode sur le deuxième service, puis attend une réponse.</span><span class="sxs-lookup"><span data-stu-id="b8630-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="b8630-113">Le deuxième service connait le nom de la méthode de rappel, mais le point de terminaison du service qui implémente cette méthode n'est pas connu au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="b8630-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8630-114">La corrélation duplex durable peut être utilisée uniquement lorsque le <xref:System.ServiceModel.Channels.AddressingVersion> du point de terminaison est configuré avec <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8630-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="b8630-115">Si ce n’est pas le cas, une <xref:System.InvalidOperationException> exception est levée avec le message suivant : «le message contient un en-tête de contexte de rappel avec une référence de point de terminaison pour [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="b8630-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="b8630-116">Le contexte de rappel peut être transmis uniquement lorsque AddressingVersion est configuré avec « WSAddressing10 ».</span><span class="sxs-lookup"><span data-stu-id="b8630-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="b8630-117">Dans l'exemple suivant, un service de workflow est hébergé, qui crée un <xref:System.ServiceModel.Endpoint> de rappel à l'aide de l'objet <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="b8630-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="b8630-118">Le workflow qui implémente ce service de workflow initialise la corrélation de rappel avec son activité <xref:System.ServiceModel.Activities.Send> et référence ce point de terminaison de rappel à partir de l'activité <xref:System.ServiceModel.Activities.Receive> en corrélation avec l'activité <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="b8630-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="b8630-119">L'exemple suivant représente le workflow retourné par la méthode `GetWF1`.</span><span class="sxs-lookup"><span data-stu-id="b8630-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="b8630-120">Le deuxième service de workflow est hébergé à l’aide d’une liaison basée sur un contexte, fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="b8630-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="b8630-121">Le workflow qui implémente ce service de workflow commence par une activité <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="b8630-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="b8630-122">Cette activité de réception initialise la corrélation de rappel pour ce service, attend un certain temps pour simuler un travail de longue durée, puis rappelle dans le premier service à l'aide du contexte de rappel qui a été transmis lors du premier appel dans le service.</span><span class="sxs-lookup"><span data-stu-id="b8630-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="b8630-123">L'exemple suivant représente le workflow retourné par un appel à la méthode `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="b8630-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="b8630-124">Notez que l'activité <xref:System.ServiceModel.Activities.Send> a une adresse d'espace réservé, `http://www.contoso.com` ; l'adresse réelle utilisée au moment de l'exécution est l'adresse de rappel fournie.</span><span class="sxs-lookup"><span data-stu-id="b8630-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="b8630-125">Lorsque la méthode `StartOrder` est appelée sur le premier workflow, la sortie suivante s'affiche, qui indique le flux d'exécution entre les deux workflows.</span><span class="sxs-lookup"><span data-stu-id="b8630-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="b8630-126">Dans cet exemple, les deux workflows gèrent explicitement la corrélation à l'aide d'un objet <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="b8630-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="b8630-127">Étant donné qu'il n'y avait qu'une seule corrélation dans ces exemples de workflows, la gestion <xref:System.ServiceModel.Activities.CorrelationHandle> par défaut aurait suffi.</span><span class="sxs-lookup"><span data-stu-id="b8630-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
