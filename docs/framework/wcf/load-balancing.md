---
title: Équilibrage de charge
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: c9a1e889ab5adcb8f0eb5ea851c81a4f9ee56e95
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138548"
---
# <a name="load-balancing"></a>Équilibrage de charge
Une façon d’augmenter la capacité des applications Windows Communication Foundation (WCF) consiste à les mettre à l’échelle en les déployant dans une batterie de serveurs à charge équilibrée. Les applications WCF peuvent être équilibrées en charge à l’aide de techniques d’équilibrage de charge standard, notamment des équilibreurs de charge logiciels tels que l’équilibrage de charge réseau Windows, ainsi que des appliances d’équilibrage de charge basées sur le matériel.  
  
 Les sections suivantes traitent des considérations relatives à l’équilibrage de charge des applications WCF générées à l’aide de différentes liaisons fournies par le système.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Équilibrage de charge avec la liaison HTTP de base  
 Du point de vue de l’équilibrage de charge, les applications WCF qui communiquent à l’aide de la <xref:System.ServiceModel.BasicHttpBinding> ne sont pas différentes des autres types courants de trafic réseau HTTP (contenu HTML statique, pages ASP.NET ou services Web ASMX). Les canaux WCF qui utilisent cette liaison sont fondamentalement sans État et terminent leurs connexions lorsque le canal se ferme. C'est la raison pour laquelle <xref:System.ServiceModel.BasicHttpBinding> fonctionne bien avec les techniques d'équilibrage de charge HTTP existantes.  
  
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
  
- Désactivez l'établissement du contexte de sécurité : pour ce faire, affectez <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> a la propriété <xref:System.ServiceModel.WSHttpBinding> de `false`. En guise d’alternative, si des sessions de sécurité sont requises, il est possible d’utiliser des sessions de sécurité avec état comme décrit dans la rubrique [sessions sécurisées](./feature-details/secure-sessions.md) . Les sessions de sécurité avec état permettent au service de rester sans état car l’ensemble de l’état de la session de sécurité est transmis avec chaque demande dans le cadre du jeton de sécurité de protection. Notez que pour activer une session de sécurité avec état, il est nécessaire d’utiliser <xref:System.ServiceModel.Channels.CustomBinding> ou <xref:System.ServiceModel.Channels.Binding> défini par l’utilisateur car les paramètres de configuration requis ne sont pas exposés sur <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.WSDualHttpBinding> qui sont fournis par le système.  
  
- N'utilisez pas de session fiable. Cette fonctionnalité est désactivée par défaut.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Équilibrage de charge avec la liaison Net.TCP  
 <xref:System.ServiceModel.NetTcpBinding> peut faire l'objet d'un équilibrage de charge à l'aide des techniques d'équilibrage de charge au niveau de la couche IP. Cependant, <xref:System.ServiceModel.NetTcpBinding> regroupe les connexions TCP par défaut afin de réduire la latence de la connexion. Il s'agit d'une optimisation qui interfère avec le mécanisme de base d'équilibrage de charge. La valeur de configuration principale permettant d'optimiser <xref:System.ServiceModel.NetTcpBinding> est le délai de bail, qui fait partie des paramètres de pool de connexions. Le regroupement de connexions provoque l'association des connexions clientes à des serveurs spécifiques dans la batterie. Au fur et à mesure que la durée de vie de ces connexions augmente (facteur contrôlé par le paramètre de délai de bail), la distribution de la charge sur les divers serveurs dans la batterie est déséquilibrée. En conséquence, le temps d'appel moyen augmente. Donc lorsque vous utilisez <xref:System.ServiceModel.NetTcpBinding> dans les scénarios à charge équilibrée, réduisez le délai de bail par défaut utilisé par la liaison. Un délai de bail de 30 secondes est un point de départ raisonnable pour les scénarios à charge équilibrée, bien que la valeur optimale dépende de l'application. Pour plus d’informations sur le délai d’expiration du bail de canal et d’autres quotas de transport, consultez [quotas de transport](./feature-details/transport-quotas.md).  
  
 Pour de meilleures performances dans les scénarios à charge équilibrée, utilisez <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Voir aussi

- [Bonnes pratiques pour l’hébergement dans Internet Information Services](./feature-details/internet-information-services-hosting-best-practices.md)
