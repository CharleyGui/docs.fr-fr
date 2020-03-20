---
title: Corrélation duplex durable
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: bb73cef5190a0b146e713ef1adae24219dc2eed8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185173"
---
# <a name="durable-duplex-correlation"></a>Corrélation duplex durable
La corrélation duplex durable, également appelée corrélation de rappel, est utile lorsqu’un service de workflow a besoin d’envoyer un rappel à l’appelant initial. Contrairement au duplex WCF, le rappel peut arriver à n’importe quel moment du futur et n’est pas lié au même canal ni à la durée de vie du canal ; la seule exigence est que l’appelant ait un point de terminaison actif qui écoute le message de rappel. Cela permet à deux services de workflow de communiquer dans une conversation de longue durée. Cette rubrique présente une vue d'ensemble de la corrélation duplex durable.  
  
## <a name="using-durable-duplex-correlation"></a>Utilisation de la corrélation duplex durable  
 Pour utiliser la corrélation duplex durable, les deux services doivent utiliser une liaison contextuelle qui prend en charge les opérations bidirectionnelles, telle que <xref:System.ServiceModel.NetTcpContextBinding> ou <xref:System.ServiceModel.WSHttpContextBinding>. Le service d’appel enregistre une propriété <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> avec la liaison souhaitée sur son <xref:System.ServiceModel.Endpoint> client. Le service de réception reçoit ces données dans l'appel initial, puis les utilise sur son propre <xref:System.ServiceModel.Endpoint> dans l'activité <xref:System.ServiceModel.Activities.Send> qui effectue le rappel vers le service d'appel. Dans cet exemple, deux services communiquent entre eux. Le premier service appelle une méthode sur le deuxième service, puis attend une réponse. Le deuxième service connait le nom de la méthode de rappel, mais le point de terminaison du service qui implémente cette méthode n'est pas connu au moment de la conception.  
  
> [!NOTE]
> La corrélation duplex durable peut être utilisée uniquement lorsque le <xref:System.ServiceModel.Channels.AddressingVersion> du point de terminaison est configuré avec <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Si ce n’est <xref:System.InvalidOperationException> pas le cas, une exception est lancée avec le message suivant : « Le message contient un en-tête de contexte de rappel avec une référence de point de terminaison pour [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Le contexte de rappel ne peut être transmis que lorsque l’Adresse est configuré avec 'WSAddressing10'.
  
 Dans l'exemple suivant, un service de workflow est hébergé, qui crée un <xref:System.ServiceModel.Endpoint> de rappel à l'aide de l'objet <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Le workflow qui implémente ce service de workflow initialise la corrélation de rappel avec son activité <xref:System.ServiceModel.Activities.Send> et référence ce point de terminaison de rappel à partir de l'activité <xref:System.ServiceModel.Activities.Receive> en corrélation avec l'activité <xref:System.ServiceModel.Activities.Send>. L'exemple suivant représente le workflow retourné par la méthode `GetWF1`.  
  
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
  
 Le deuxième service de workflow est hébergé à l’aide d’une liaison basée sur un contexte, fournie par le système.  
  
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
  
 Le workflow qui implémente ce service de workflow commence par une activité <xref:System.ServiceModel.Activities.Receive>. Cette activité de réception initialise la corrélation de rappel pour ce service, attend un certain temps pour simuler un travail de longue durée, puis rappelle dans le premier service à l'aide du contexte de rappel qui a été transmis lors du premier appel dans le service. L'exemple suivant représente le workflow retourné par un appel à la méthode `GetWF2`. Notez que l'activité <xref:System.ServiceModel.Activities.Send> a une adresse d'espace réservé, `http://www.contoso.com` ; l'adresse réelle utilisée au moment de l'exécution est l'adresse de rappel fournie.  
  
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
  
 Lorsque la méthode `StartOrder` est appelée sur le premier workflow, la sortie suivante s'affiche, qui indique le flux d'exécution entre les deux workflows.  
  
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
  
 Dans cet exemple, les deux workflows gèrent explicitement la corrélation à l'aide d'un objet <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Étant donné qu'il n'y avait qu'une seule corrélation dans ces exemples de workflows, la gestion <xref:System.ServiceModel.Activities.CorrelationHandle> par défaut aurait suffi.
