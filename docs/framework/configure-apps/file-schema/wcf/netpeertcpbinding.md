---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: fc1930889235805d68d88aa8080f8f9fb3235612
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933042"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="350aa-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="350aa-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="350aa-102">Définit une liaison pour la messagerie TCP spécifique au canal homologue.</span><span class="sxs-lookup"><span data-stu-id="350aa-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="350aa-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="350aa-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="350aa-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="350aa-104">\<bindings></span></span>  
<span data-ttu-id="350aa-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="350aa-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="350aa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="350aa-106">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="350aa-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="350aa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="350aa-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="350aa-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="350aa-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="350aa-109">Attributes</span></span>  
  
|<span data-ttu-id="350aa-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="350aa-110">Attribute</span></span>|<span data-ttu-id="350aa-111">Description</span><span class="sxs-lookup"><span data-stu-id="350aa-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="350aa-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="350aa-112">closeTimeout</span></span>|<span data-ttu-id="350aa-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="350aa-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="350aa-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="350aa-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="350aa-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="350aa-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="350aa-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="350aa-116">listenIPAddress</span></span>|<span data-ttu-id="350aa-117">Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.</span><span class="sxs-lookup"><span data-stu-id="350aa-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="350aa-118">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="350aa-118">The default is `null`.</span></span>|  
|<span data-ttu-id="350aa-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="350aa-119">maxBufferPoolSize</span></span>|<span data-ttu-id="350aa-120">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="350aa-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="350aa-121">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="350aa-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="350aa-122">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="350aa-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="350aa-123">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="350aa-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="350aa-124">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="350aa-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="350aa-125">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="350aa-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="350aa-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="350aa-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="350aa-127">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="350aa-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="350aa-128">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="350aa-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="350aa-129">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="350aa-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="350aa-130">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="350aa-130">The default is 65536.</span></span>|  
|<span data-ttu-id="350aa-131">name</span><span class="sxs-lookup"><span data-stu-id="350aa-131">name</span></span>|<span data-ttu-id="350aa-132">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="350aa-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="350aa-133">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="350aa-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="350aa-134">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="350aa-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="350aa-135">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="350aa-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="350aa-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="350aa-136">openTimeout</span></span>|<span data-ttu-id="350aa-137"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="350aa-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="350aa-138">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="350aa-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="350aa-139">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="350aa-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="350aa-140">port</span><span class="sxs-lookup"><span data-stu-id="350aa-140">port</span></span>|<span data-ttu-id="350aa-141">Entier indiquant le port d’interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.</span><span class="sxs-lookup"><span data-stu-id="350aa-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="350aa-142">Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="350aa-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="350aa-143">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="350aa-143">The default is 0.</span></span>|  
|<span data-ttu-id="350aa-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="350aa-144">receiveTimeout</span></span>|<span data-ttu-id="350aa-145"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="350aa-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="350aa-146">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="350aa-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="350aa-147">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="350aa-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="350aa-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="350aa-148">sendTimeout</span></span>|<span data-ttu-id="350aa-149"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="350aa-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="350aa-150">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="350aa-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="350aa-151">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="350aa-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="350aa-152">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="350aa-152">Child Elements</span></span>  
  
|<span data-ttu-id="350aa-153">Élément</span><span class="sxs-lookup"><span data-stu-id="350aa-153">Element</span></span>|<span data-ttu-id="350aa-154">Description</span><span class="sxs-lookup"><span data-stu-id="350aa-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="350aa-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="350aa-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="350aa-156">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="350aa-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="350aa-157">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="350aa-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="350aa-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="350aa-158">\<resolver></span></span>](resolver.md)|<span data-ttu-id="350aa-159">Spécifie un programme de résolution d’homologue utilisé par cette liaison pour résoudre un ID de maille d’homologues en adresses IP de point de terminaison de nœuds dans la maille d’homologues.</span><span class="sxs-lookup"><span data-stu-id="350aa-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="350aa-160">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="350aa-160">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="350aa-161">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="350aa-161">Defines the security settings for the message.</span></span> <span data-ttu-id="350aa-162">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="350aa-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="350aa-163">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="350aa-163">Parent Elements</span></span>  
  
|<span data-ttu-id="350aa-164">Élément</span><span class="sxs-lookup"><span data-stu-id="350aa-164">Element</span></span>|<span data-ttu-id="350aa-165">Description</span><span class="sxs-lookup"><span data-stu-id="350aa-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="350aa-166">\<bindings></span><span class="sxs-lookup"><span data-stu-id="350aa-166">\<bindings></span></span>](bindings.md)|<span data-ttu-id="350aa-167">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="350aa-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="350aa-168">Notes</span><span class="sxs-lookup"><span data-stu-id="350aa-168">Remarks</span></span>  
 <span data-ttu-id="350aa-169">Cette liaison assure la prise en charge de la création d'applications d'égal à égal ou entre plusieurs parties utilisant le transport d'homologue sur TCP.</span><span class="sxs-lookup"><span data-stu-id="350aa-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="350aa-170">Chaque nœud homologue peut héberger plusieurs canaux homologues définis avec ce type de liaison.</span><span class="sxs-lookup"><span data-stu-id="350aa-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="350aa-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="350aa-171">Example</span></span>  
 <span data-ttu-id="350aa-172">L’exemple suivant montre l’utilisation de la liaison NetPeerTcpBinding, qui fournit la communication pluripartite à l’aide d’un canal homologue.</span><span class="sxs-lookup"><span data-stu-id="350aa-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="350aa-173">Pour obtenir un scénario détaillé de l’utilisation de cette liaison, consultez [net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="350aa-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="350aa-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="350aa-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="350aa-175">Liaisons</span><span class="sxs-lookup"><span data-stu-id="350aa-175">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="350aa-176">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="350aa-176">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="350aa-177">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="350aa-177">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="350aa-178">\<binding></span><span class="sxs-lookup"><span data-stu-id="350aa-178">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="350aa-179">[TCP d’homologue net](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="350aa-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="350aa-180">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="350aa-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
