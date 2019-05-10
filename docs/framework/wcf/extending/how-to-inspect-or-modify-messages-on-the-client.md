---
title: 'Procédure : inspecter ou modifier des messages sur le client'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 3bf349a5b41c56d5dc3a79107b3fc86968033d54
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606296"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Procédure : inspecter ou modifier des messages sur le client
Vous pouvez inspecter ou modifier les messages entrants ou sortants sur un client WCF en implémentant un <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> et leur insertion dans l’exécution du client. Pour plus d’informations, consultez [Clients extension](../../../../docs/framework/wcf/extending/extending-clients.md). La fonctionnalité équivalente sur le service est <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Pour obtenir un exemple de code complet, consultez la [inspecteurs de Message](../../../../docs/framework/wcf/samples/message-inspectors.md) exemple.  
  
### <a name="to-inspect-or-modify-messages"></a>Pour inspecter ou modifier des messages  
  
1. Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2. Implémentez <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> en fonction de la portée à laquelle vous souhaitez insérer facilement l'inspecteur de message client. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> vous permet de modifier le comportement au niveau du point de terminaison. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> permet de modifier le comportement au niveau du contrat.  
  
3. Insérez le comportement avant d'appeler la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Pour plus d’informations, consultez [configuration et extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemple  
 Les exemples de code suivants affichent, dans l'ordre :  
  
- Une implémentation d'inspecteur client.  
  
- Un comportement de point de terminaison qui insère l'inspecteur.  
  
- Classe <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> dérivée qui vous permet d'ajouter le comportement dans un fichier de configuration.  
  
- Un fichier de configuration qui ajoute le comportement de point de terminaison pour insérer l'inspecteur de message client dans le runtime client.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Configuration et extension de l’exécution à l’aide de comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
