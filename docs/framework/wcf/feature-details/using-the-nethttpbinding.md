---
title: Utilisation de NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: ac6fc658731d032051f2dfd4058397f9b9a55828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585634"
---
# <a name="using-the-nethttpbinding"></a>Utilisation de NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding> est une liaison conçue pour consommer des services HTTP ou WebSocket et utilise l'encodage binaire par défaut. <xref:System.ServiceModel.NetHttpBinding> détecte si elle est utilisée avec un contrat demande-réponse ou un contrat duplex et modifie son comportement pour le faire correspondre - elle utilise HTTP pour les contrats de demande-réponse et WebSockets pour les contrats duplex. Vous pouvez substituer ce comportement au moyen du paramètre <xref:System.ServiceModel.Channels.WebSocketTransportUsage> :  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>: Force l’utilisation de WebSockets même pour les contrats demande-réponse.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>: Empêche l’utilisation de WebSocket. Toute tentative d'utiliser un contrat duplex avec ce paramètre entraîne une exception.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>-Il s’agit de la valeur par défaut et se comporte comme décrit ci-dessus.  
  
 <xref:System.ServiceModel.NetHttpBinding> prend en charge les sessions fiables en mode HTTP et en mode WebSocket. Les sessions en mode WebSocket sont fournies par le transport.  
  
> [!WARNING]
> Si vous utilisez <xref:System.ServiceModel.NetHttpBinding> et le TransferMode de la liaison a la valeur TransferMode.Streamed, les grands flux peuvent provoquer un interblocage et le dépassement du délai d'attente de l'appel. Pour contourner ce problème, envoyez de plus petits messages ou utilisez TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Configuration d'un service de façon à utiliser NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> peut être configuré de la même façon que toute autre liaison. L'extrait de code suivant de configuration montre comment configurer un service WCF avec <xref:System.ServiceModel.NetHttpBinding>.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 L'extrait de code suivant montre comment ajouter <xref:System.ServiceModel.NetHttpBinding> dans le code.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a>Voir aussi

- [Configuration de liaisons pour les services](../configuring-bindings-for-wcf-services.md)
- [Liaisons](bindings.md)
- [Liaisons fournies par le système](../system-provided-bindings.md)
- [Services duplex](duplex-services.md)
