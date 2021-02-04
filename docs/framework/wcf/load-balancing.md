---
title: Équilibrage de la charge.
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: ccb915c33be217d2a8d00a54c5bd57384286140f
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548095"
---
# <a name="load-balancing"></a>Équilibrage de la charge.

Une façon d’augmenter la capacité des applications Windows Communication Foundation (WCF) consiste à les mettre à l’échelle en les déployant dans une batterie de serveurs à charge équilibrée. Les applications WCF peuvent être équilibrées en charge à l’aide de techniques d’équilibrage de charge standard, notamment des équilibreurs de charge logiciels tels que l’équilibrage de charge réseau Windows, ainsi que des appliances d’équilibrage de charge basées sur le matériel.  
  
 Les sections suivantes traitent des considérations relatives à l’équilibrage de charge des applications WCF générées à l’aide de différentes liaisons fournies par le système.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Équilibrage de charge avec la liaison HTTP de base  

 Du point de vue de l’équilibrage de charge, les applications WCF qui communiquent à l’aide de <xref:System.ServiceModel.BasicHttpBinding> ne sont pas différentes des autres types courants de trafic réseau http (contenu HTML statique, pages ASP.net ou services Web ASMX). Les canaux WCF qui utilisent cette liaison sont fondamentalement sans État et terminent leurs connexions lorsque le canal se ferme. C'est la raison pour laquelle <xref:System.ServiceModel.BasicHttpBinding> fonctionne bien avec les techniques d'équilibrage de charge HTTP existantes.  
  
 Par défaut, <xref:System.ServiceModel.BasicHttpBinding> envoie un en-tête HTTP de connexion dans les messages contenant une valeur `Keep-Alive`, ce qui permet aux clients d'établir des connexions persistantes aux services qui les prennent en charge. Cette configuration offre un débit supérieur car les connexions précédemment établies peuvent être réutilisées pour envoyer les messages suivants au même serveur. Toutefois, la réutilisation des connexions peut provoquer une forte association des clients à un serveur spécifique dans la batterie à charge équilibrée, ce qui réduit l'efficacité de l'équilibrage de charge tourniquet. Si vous ne souhaitez pas ce type de comportement, `Keep-Alive` HTTP peut être désactivé sur le serveur à l'aide de la propriété <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> avec <xref:System.ServiceModel.Channels.CustomBinding> ou <xref:System.ServiceModel.Channels.Binding> défini par l'utilisateur. L'exemple suivant montre comment procéder à l'aide de la configuration :  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 À l’aide de la configuration simplifiée introduite dans .NET Framework 4, le même comportement peut être obtenu à l’aide de la configuration simplifiée suivante.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](simplified-configuration.md) et [Configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Équilibrage de charge avec les liaisons WSHttp et WSDualHttp  

 <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.WSDualHttpBinding> peuvent tous deux faire l’objet d’un équilibrage de charge à l’aide des techniques d’équilibrage de charge HTTP sous réserve que plusieurs modifications soient apportées à la configuration de liaison par défaut.  
  
- Désactivez l’établissement du contexte de sécurité ou utilisez des sessions de sécurité avec état. L’établissement du contexte de sécurité peut être désactivé en affectant <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> à la propriété de la <xref:System.ServiceModel.WSHttpBinding> valeur `false` . Si vous utilisez ou si vous avez <xref:System.ServiceModel.WSDualHttpBinding> besoin de sessions de sécurité, il est possible d’utiliser des sessions de sécurité avec état comme décrit dans [sessions sécurisées](./feature-details/secure-sessions.md). Les sessions de sécurité avec état permettent au service de rester sans État, car l’ensemble de l’état de la session de sécurité est transmis avec chaque demande dans le cadre du jeton de sécurité de protection. Pour activer une session de sécurité avec état, vous devez utiliser un <xref:System.ServiceModel.Channels.CustomBinding> ou un défini par <xref:System.ServiceModel.Channels.Binding> l’utilisateur, car les paramètres de configuration nécessaires ne sont pas exposés sur le fourni par le système <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.WSDualHttpBinding> .

- Si vous désactivez l’établissement du contexte de sécurité, vous devez également désactiver la négociation des informations d’identification du service. Pour la désactiver, affectez la valeur <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> à la propriété de <xref:System.ServiceModel.WSHttpBinding> `false` . Pour désactiver la négociation des informations d’identification du service, vous devrez peut-être spécifier explicitement l’identité du point de terminaison sur le client.
  
- N'utilisez pas de session fiable. Cette fonctionnalité est désactivée par défaut.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Équilibrage de charge avec la liaison Net.TCP  

 <xref:System.ServiceModel.NetTcpBinding> peut faire l'objet d'un équilibrage de charge à l'aide des techniques d'équilibrage de charge au niveau de la couche IP. Cependant, <xref:System.ServiceModel.NetTcpBinding> regroupe les connexions TCP par défaut afin de réduire la latence de la connexion. Il s'agit d'une optimisation qui interfère avec le mécanisme de base d'équilibrage de charge. La valeur de configuration principale permettant d'optimiser <xref:System.ServiceModel.NetTcpBinding> est le délai de bail, qui fait partie des paramètres de pool de connexions. Le regroupement de connexions provoque l'association des connexions clientes à des serveurs spécifiques dans la batterie. Au fur et à mesure que la durée de vie de ces connexions augmente (facteur contrôlé par le paramètre de délai de bail), la distribution de la charge sur les divers serveurs dans la batterie est déséquilibrée. En conséquence, le temps d'appel moyen augmente. Donc lorsque vous utilisez <xref:System.ServiceModel.NetTcpBinding> dans les scénarios à charge équilibrée, réduisez le délai de bail par défaut utilisé par la liaison. Un délai de bail de 30 secondes est un point de départ raisonnable pour les scénarios à charge équilibrée, bien que la valeur optimale dépende de l'application. Pour plus d’informations sur le délai d’expiration du bail de canal et d’autres quotas de transport, consultez [quotas de transport](./feature-details/transport-quotas.md).  
  
 Pour de meilleures performances dans les scénarios à charge équilibrée, utilisez <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Voir aussi

- [Meilleures pratiques pour l'hébergement dans Internet Information Services](./feature-details/internet-information-services-hosting-best-practices.md)
