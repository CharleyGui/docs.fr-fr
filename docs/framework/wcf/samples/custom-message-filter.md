---
title: Custom Message Filter
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183890"
---
# <a name="custom-message-filter"></a>Custom Message Filter
Cet exemple montre comment remplacer les filtres de message que Windows Communication Foundation (WCF) utilise pour envoyer des messages aux points de terminaison.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Lorsque le premier message sur un canal arrive au niveau du serveur, ce dernier doit déterminer le point de terminaison (le cas échéant) associé à cet URI qui doit recevoir le message. Ce processus est contrôlé par les objets <xref:System.ServiceModel.Dispatcher.MessageFilter> joints à <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Chaque point de terminaison d'un service a un <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> unique. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> possède à la fois <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> et <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. L'association de ces deux filtres forme le filtre de messages utilisé pour ce point de terminaison.  
  
 Par défaut, le <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> d'un point de terminaison correspond aux messages envoyés à une adresse qui correspond au <xref:System.ServiceModel.EndpointAddress> du point de terminaison de service. Par défaut, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> le point de terminaison inspecte l’action du message entrant et associe tout message à une action `IsInitiating` = `true` qui correspond à l’une des actions des opérations du contrat de fin de service (seules les actions sont prises en considération). Par défaut, le filtre d'un point de terminaison correspond donc uniquement si l'en-tête To du message est le <xref:System.ServiceModel.EndpointAddress> du point de terminaison et que l'action du message correspond à l'une des actions de l'opération de point de terminaison.  
  
 Ces filtres peuvent être modifiés à l'aide d'un comportement. Dans l'exemple, le service crée un <xref:System.ServiceModel.Description.IEndpointBehavior> qui remplace <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> et <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> sur <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 Deux filtres d'adresse sont définis :  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 `FilteringEndpointBehavior` est rendu configurable et accepte deux variantes différentes.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 La variante 1 correspond uniquement aux adresses qui contiennent un 'e' (mais qui comportent des actions), tandis que la variante 2 correspond uniquement aux adresses sans 'e' :  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 Dans le fichier de configuration, le service enregistre le nouveau comportement :  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 Il crée ensuite des configurations `endpointBehavior` pour chaque variante :  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 Enfin, le point de terminaison du service référence l'un des `behaviorConfigurations` :  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 L'implémentation de l'application cliente est simple : elle crée deux canaux à l'URI du service (en passant cette valeur comme deuxième paramètre (`via`) à <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29>) et envoie un message unique sur chaque canal, mais utilise des adresses de point de terminaison différentes pour chacun d'entre eux. Par conséquent, les messages sortants provenant du client ont des désignations To différentes, et le serveur réagit en conséquence, tel qu'indiqué par la sortie du client :  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Le passage d’une variante à une autre dans le fichier de configuration du serveur provoque la permutation du filtre et l’activation du comportement opposé sur le client (le message à `urn:e` réussit, alors que le message à `urn:a` échoue).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Pour exécuter l’échantillon dans une configuration mono-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration multi-machine, suivez les instructions de [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) et modifiez la ligne suivante en Client.cs.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Remplacez localhost par le nom du serveur.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
