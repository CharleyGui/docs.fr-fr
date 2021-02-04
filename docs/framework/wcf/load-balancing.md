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
# <a name="load-balancing"></a><span data-ttu-id="efb49-102">Équilibrage de la charge.</span><span class="sxs-lookup"><span data-stu-id="efb49-102">Load Balancing</span></span>

<span data-ttu-id="efb49-103">Une façon d’augmenter la capacité des applications Windows Communication Foundation (WCF) consiste à les mettre à l’échelle en les déployant dans une batterie de serveurs à charge équilibrée.</span><span class="sxs-lookup"><span data-stu-id="efb49-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="efb49-104">Les applications WCF peuvent être équilibrées en charge à l’aide de techniques d’équilibrage de charge standard, notamment des équilibreurs de charge logiciels tels que l’équilibrage de charge réseau Windows, ainsi que des appliances d’équilibrage de charge basées sur le matériel.</span><span class="sxs-lookup"><span data-stu-id="efb49-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="efb49-105">Les sections suivantes traitent des considérations relatives à l’équilibrage de charge des applications WCF générées à l’aide de différentes liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="efb49-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="efb49-106">Équilibrage de charge avec la liaison HTTP de base</span><span class="sxs-lookup"><span data-stu-id="efb49-106">Load Balancing with the Basic HTTP Binding</span></span>  

 <span data-ttu-id="efb49-107">Du point de vue de l’équilibrage de charge, les applications WCF qui communiquent à l’aide de <xref:System.ServiceModel.BasicHttpBinding> ne sont pas différentes des autres types courants de trafic réseau http (contenu HTML statique, pages ASP.net ou services Web ASMX).</span><span class="sxs-lookup"><span data-stu-id="efb49-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="efb49-108">Les canaux WCF qui utilisent cette liaison sont fondamentalement sans État et terminent leurs connexions lorsque le canal se ferme.</span><span class="sxs-lookup"><span data-stu-id="efb49-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="efb49-109">C'est la raison pour laquelle <xref:System.ServiceModel.BasicHttpBinding> fonctionne bien avec les techniques d'équilibrage de charge HTTP existantes.</span><span class="sxs-lookup"><span data-stu-id="efb49-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="efb49-110">Par défaut, <xref:System.ServiceModel.BasicHttpBinding> envoie un en-tête HTTP de connexion dans les messages contenant une valeur `Keep-Alive`, ce qui permet aux clients d'établir des connexions persistantes aux services qui les prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="efb49-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="efb49-111">Cette configuration offre un débit supérieur car les connexions précédemment établies peuvent être réutilisées pour envoyer les messages suivants au même serveur.</span><span class="sxs-lookup"><span data-stu-id="efb49-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="efb49-112">Toutefois, la réutilisation des connexions peut provoquer une forte association des clients à un serveur spécifique dans la batterie à charge équilibrée, ce qui réduit l'efficacité de l'équilibrage de charge tourniquet.</span><span class="sxs-lookup"><span data-stu-id="efb49-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="efb49-113">Si vous ne souhaitez pas ce type de comportement, `Keep-Alive` HTTP peut être désactivé sur le serveur à l'aide de la propriété <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> avec <xref:System.ServiceModel.Channels.CustomBinding> ou <xref:System.ServiceModel.Channels.Binding> défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="efb49-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="efb49-114">L'exemple suivant montre comment procéder à l'aide de la configuration :</span><span class="sxs-lookup"><span data-stu-id="efb49-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="efb49-115">À l’aide de la configuration simplifiée introduite dans .NET Framework 4, le même comportement peut être obtenu à l’aide de la configuration simplifiée suivante.</span><span class="sxs-lookup"><span data-stu-id="efb49-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="efb49-116">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](simplified-configuration.md) et [Configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="efb49-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="efb49-117">Équilibrage de charge avec les liaisons WSHttp et WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="efb49-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  

 <span data-ttu-id="efb49-118"><xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.WSDualHttpBinding> peuvent tous deux faire l’objet d’un équilibrage de charge à l’aide des techniques d’équilibrage de charge HTTP sous réserve que plusieurs modifications soient apportées à la configuration de liaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="efb49-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="efb49-119">Désactivez l’établissement du contexte de sécurité ou utilisez des sessions de sécurité avec état.</span><span class="sxs-lookup"><span data-stu-id="efb49-119">Turn off Security Context Establishment or use stateful security sessions.</span></span> <span data-ttu-id="efb49-120">L’établissement du contexte de sécurité peut être désactivé en affectant <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> à la propriété de la <xref:System.ServiceModel.WSHttpBinding> valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="efb49-120">Security Context Establishment can be turned off by setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="efb49-121">Si vous utilisez ou si vous avez <xref:System.ServiceModel.WSDualHttpBinding> besoin de sessions de sécurité, il est possible d’utiliser des sessions de sécurité avec état comme décrit dans [sessions sécurisées](./feature-details/secure-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="efb49-121">If you are using <xref:System.ServiceModel.WSDualHttpBinding> or security sessions are required, it is possible to use stateful security sessions as described in [Secure Sessions](./feature-details/secure-sessions.md).</span></span> <span data-ttu-id="efb49-122">Les sessions de sécurité avec état permettent au service de rester sans État, car l’ensemble de l’état de la session de sécurité est transmis avec chaque demande dans le cadre du jeton de sécurité de protection.</span><span class="sxs-lookup"><span data-stu-id="efb49-122">Stateful security sessions enable the service to remain stateless, as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="efb49-123">Pour activer une session de sécurité avec état, vous devez utiliser un <xref:System.ServiceModel.Channels.CustomBinding> ou un défini par <xref:System.ServiceModel.Channels.Binding> l’utilisateur, car les paramètres de configuration nécessaires ne sont pas exposés sur le fourni par le système <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.WSDualHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="efb49-123">To enable a stateful security session, you must use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>, as the necessary configuration settings are not exposed on the system-provided <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding>.</span></span>

- <span data-ttu-id="efb49-124">Si vous désactivez l’établissement du contexte de sécurité, vous devez également désactiver la négociation des informations d’identification du service.</span><span class="sxs-lookup"><span data-stu-id="efb49-124">If you turn off Security Context Establishment, you also need to turn off Service Credential Negotiation.</span></span> <span data-ttu-id="efb49-125">Pour la désactiver, affectez la valeur <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> à la propriété de <xref:System.ServiceModel.WSHttpBinding> `false` .</span><span class="sxs-lookup"><span data-stu-id="efb49-125">To turn it off, set the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="efb49-126">Pour désactiver la négociation des informations d’identification du service, vous devrez peut-être spécifier explicitement l’identité du point de terminaison sur le client.</span><span class="sxs-lookup"><span data-stu-id="efb49-126">To disable Service Credential Negotiation, you may need to explicitly specify the endpoint identity on the client.</span></span>
  
- <span data-ttu-id="efb49-127">N'utilisez pas de session fiable.</span><span class="sxs-lookup"><span data-stu-id="efb49-127">Do not use reliable sessions.</span></span> <span data-ttu-id="efb49-128">Cette fonctionnalité est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="efb49-128">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="efb49-129">Équilibrage de charge avec la liaison Net.TCP</span><span class="sxs-lookup"><span data-stu-id="efb49-129">Load Balancing the Net.TCP Binding</span></span>  

 <span data-ttu-id="efb49-130"><xref:System.ServiceModel.NetTcpBinding> peut faire l'objet d'un équilibrage de charge à l'aide des techniques d'équilibrage de charge au niveau de la couche IP.</span><span class="sxs-lookup"><span data-stu-id="efb49-130">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="efb49-131">Cependant, <xref:System.ServiceModel.NetTcpBinding> regroupe les connexions TCP par défaut afin de réduire la latence de la connexion.</span><span class="sxs-lookup"><span data-stu-id="efb49-131">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="efb49-132">Il s'agit d'une optimisation qui interfère avec le mécanisme de base d'équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="efb49-132">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="efb49-133">La valeur de configuration principale permettant d'optimiser <xref:System.ServiceModel.NetTcpBinding> est le délai de bail, qui fait partie des paramètres de pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="efb49-133">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="efb49-134">Le regroupement de connexions provoque l'association des connexions clientes à des serveurs spécifiques dans la batterie.</span><span class="sxs-lookup"><span data-stu-id="efb49-134">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="efb49-135">Au fur et à mesure que la durée de vie de ces connexions augmente (facteur contrôlé par le paramètre de délai de bail), la distribution de la charge sur les divers serveurs dans la batterie est déséquilibrée.</span><span class="sxs-lookup"><span data-stu-id="efb49-135">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="efb49-136">En conséquence, le temps d'appel moyen augmente.</span><span class="sxs-lookup"><span data-stu-id="efb49-136">As a result the average call time increases.</span></span> <span data-ttu-id="efb49-137">Donc lorsque vous utilisez <xref:System.ServiceModel.NetTcpBinding> dans les scénarios à charge équilibrée, réduisez le délai de bail par défaut utilisé par la liaison.</span><span class="sxs-lookup"><span data-stu-id="efb49-137">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="efb49-138">Un délai de bail de 30 secondes est un point de départ raisonnable pour les scénarios à charge équilibrée, bien que la valeur optimale dépende de l'application.</span><span class="sxs-lookup"><span data-stu-id="efb49-138">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="efb49-139">Pour plus d’informations sur le délai d’expiration du bail de canal et d’autres quotas de transport, consultez [quotas de transport](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="efb49-139">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="efb49-140">Pour de meilleures performances dans les scénarios à charge équilibrée, utilisez <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="efb49-140">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb49-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efb49-141">See also</span></span>

- [<span data-ttu-id="efb49-142">Meilleures pratiques pour l'hébergement dans Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="efb49-142">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
