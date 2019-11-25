---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140731"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="9a114-101">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="9a114-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="9a114-102">Définit une liaison pour la messagerie TCP spécifique au canal homologue.</span><span class="sxs-lookup"><span data-stu-id="9a114-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
<span data-ttu-id="9a114-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a114-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9a114-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9a114-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9a114-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="9a114-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="9a114-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**netPeerTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="9a114-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a114-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a114-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a114-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9a114-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9a114-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9a114-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a114-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9a114-110">Attributes</span></span>  
  
|<span data-ttu-id="9a114-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="9a114-111">Attribute</span></span>|<span data-ttu-id="9a114-112">Description</span><span class="sxs-lookup"><span data-stu-id="9a114-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a114-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="9a114-113">closeTimeout</span></span>|<span data-ttu-id="9a114-114"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="9a114-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9a114-115">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a114-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a114-116">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9a114-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9a114-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="9a114-117">listenIPAddress</span></span>|<span data-ttu-id="9a114-118">Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.</span><span class="sxs-lookup"><span data-stu-id="9a114-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="9a114-119">La valeur par défaut est `null`,</span><span class="sxs-lookup"><span data-stu-id="9a114-119">The default is `null`.</span></span>|  
|<span data-ttu-id="9a114-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9a114-120">maxBufferPoolSize</span></span>|<span data-ttu-id="9a114-121">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="9a114-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9a114-122">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="9a114-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="9a114-123">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="9a114-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9a114-124">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="9a114-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9a114-125">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="9a114-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9a114-126">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="9a114-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="9a114-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9a114-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="9a114-128">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="9a114-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9a114-129">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="9a114-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="9a114-130">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="9a114-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9a114-131">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="9a114-131">The default is 65536.</span></span>|  
|<span data-ttu-id="9a114-132">name</span><span class="sxs-lookup"><span data-stu-id="9a114-132">name</span></span>|<span data-ttu-id="9a114-133">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="9a114-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9a114-134">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="9a114-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9a114-135">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="9a114-135">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9a114-136">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9a114-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="9a114-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="9a114-137">openTimeout</span></span>|<span data-ttu-id="9a114-138"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="9a114-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9a114-139">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a114-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a114-140">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9a114-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9a114-141">port</span><span class="sxs-lookup"><span data-stu-id="9a114-141">port</span></span>|<span data-ttu-id="9a114-142">Entier indiquant le port d’interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.</span><span class="sxs-lookup"><span data-stu-id="9a114-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="9a114-143">Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="9a114-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="9a114-144">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="9a114-144">The default is 0.</span></span>|  
|<span data-ttu-id="9a114-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="9a114-145">receiveTimeout</span></span>|<span data-ttu-id="9a114-146"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="9a114-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9a114-147">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a114-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a114-148">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9a114-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="9a114-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="9a114-149">sendTimeout</span></span>|<span data-ttu-id="9a114-150"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9a114-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9a114-151">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a114-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a114-152">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9a114-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a114-153">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9a114-153">Child Elements</span></span>  
  
|<span data-ttu-id="9a114-154">Élément</span><span class="sxs-lookup"><span data-stu-id="9a114-154">Element</span></span>|<span data-ttu-id="9a114-155">Description</span><span class="sxs-lookup"><span data-stu-id="9a114-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a114-156">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a114-156">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="9a114-157">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="9a114-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9a114-158">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9a114-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="9a114-159">> de résolution de \<</span><span class="sxs-lookup"><span data-stu-id="9a114-159">\<resolver></span></span>](resolver.md)|<span data-ttu-id="9a114-160">Spécifie un programme de résolution d’homologue utilisé par cette liaison pour résoudre un ID de maille d’homologues en adresses IP de point de terminaison de nœuds dans la maille d’homologues.</span><span class="sxs-lookup"><span data-stu-id="9a114-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="9a114-161">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="9a114-161">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="9a114-162">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="9a114-162">Defines the security settings for the message.</span></span> <span data-ttu-id="9a114-163">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9a114-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a114-164">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9a114-164">Parent Elements</span></span>  
  
|<span data-ttu-id="9a114-165">Élément</span><span class="sxs-lookup"><span data-stu-id="9a114-165">Element</span></span>|<span data-ttu-id="9a114-166">Description</span><span class="sxs-lookup"><span data-stu-id="9a114-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a114-167">liaisons de\<</span><span class="sxs-lookup"><span data-stu-id="9a114-167">\<bindings></span></span>](bindings.md)|<span data-ttu-id="9a114-168">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9a114-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a114-169">Notes</span><span class="sxs-lookup"><span data-stu-id="9a114-169">Remarks</span></span>  
 <span data-ttu-id="9a114-170">Cette liaison assure la prise en charge de la création d'applications d'égal à égal ou entre plusieurs parties utilisant le transport d'homologue sur TCP.</span><span class="sxs-lookup"><span data-stu-id="9a114-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="9a114-171">Chaque nœud homologue peut héberger plusieurs canaux homologues définis avec ce type de liaison.</span><span class="sxs-lookup"><span data-stu-id="9a114-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a114-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a114-172">Example</span></span>  
 <span data-ttu-id="9a114-173">L’exemple suivant montre l’utilisation de la liaison NetPeerTcpBinding, qui fournit la communication pluripartite à l’aide d’un canal homologue.</span><span class="sxs-lookup"><span data-stu-id="9a114-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="9a114-174">Pour obtenir un scénario détaillé de l’utilisation de cette liaison, consultez [net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9a114-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a114-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a114-175">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="9a114-176">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9a114-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9a114-177">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="9a114-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9a114-178">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="9a114-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9a114-179">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="9a114-179">\<binding></span></span>](bindings.md)
- <span data-ttu-id="9a114-180">[TCP d’homologue net](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9a114-180">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="9a114-181">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="9a114-181">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
