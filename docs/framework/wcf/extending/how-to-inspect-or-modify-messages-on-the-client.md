---
title: 'Comment : inspecter ou modifier des messages sur le client'
description: Découvrez comment inspecter ou modifier les messages entrants ou sortants sur un client ou un service WCF en implémentant l’interface appropriée.
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 6f6a3d20d7f3a9fb79de5cd3e29096e270d0f188
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247505"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="8d9e1-103">Comment : inspecter ou modifier des messages sur le client</span><span class="sxs-lookup"><span data-stu-id="8d9e1-103">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="8d9e1-104">Vous pouvez inspecter ou modifier les messages entrants ou sortants sur un client WCF en implémentant un <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> et en l’insérant dans le runtime client.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-104">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="8d9e1-105">Pour plus d’informations, consultez [extension de clients](extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8d9e1-105">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="8d9e1-106">La fonctionnalité équivalente sur le service est <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8d9e1-107">Pour obtenir un exemple de code complet, consultez l’exemple [message Inspectors](../samples/message-inspectors.md) .</span><span class="sxs-lookup"><span data-stu-id="8d9e1-107">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="8d9e1-108">Pour inspecter ou modifier des messages</span><span class="sxs-lookup"><span data-stu-id="8d9e1-108">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="8d9e1-109">Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-109">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="8d9e1-110">Implémentez <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> en fonction de la portée à laquelle vous souhaitez insérer facilement l'inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-110">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="8d9e1-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>vous permet de modifier le comportement au niveau du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="8d9e1-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>vous permet de modifier le comportement au niveau du contrat.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="8d9e1-113">Insérez le comportement avant d'appeler la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-113">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8d9e1-114">Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="8d9e1-114">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d9e1-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d9e1-115">Example</span></span>  
 <span data-ttu-id="8d9e1-116">Les exemples de code suivants affichent, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="8d9e1-116">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="8d9e1-117">Une implémentation d'inspecteur client.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-117">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="8d9e1-118">Un comportement de point de terminaison qui insère l'inspecteur.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-118">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="8d9e1-119">Classe <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> dérivée qui vous permet d'ajouter le comportement dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-119">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="8d9e1-120">Un fichier de configuration qui ajoute le comportement de point de terminaison pour insérer l'inspecteur de message client dans le runtime client.</span><span class="sxs-lookup"><span data-stu-id="8d9e1-120">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d9e1-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d9e1-121">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="8d9e1-122">Configuration et extension de l'exécution à l'aide de comportements</span><span class="sxs-lookup"><span data-stu-id="8d9e1-122">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
