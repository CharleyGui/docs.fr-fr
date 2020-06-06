---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140731"
---
# \<netPeerTcpBinding>
<span data-ttu-id="2ce50-101">Définit une liaison pour la messagerie TCP spécifique au canal homologue.</span><span class="sxs-lookup"><span data-stu-id="2ce50-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="2ce50-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ce50-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ce50-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2ce50-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2ce50-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2ce50-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ce50-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ce50-105">Attributes</span></span>  
  
|<span data-ttu-id="2ce50-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="2ce50-106">Attribute</span></span>|<span data-ttu-id="2ce50-107">Description</span><span class="sxs-lookup"><span data-stu-id="2ce50-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ce50-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="2ce50-108">closeTimeout</span></span>|<span data-ttu-id="2ce50-109"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="2ce50-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2ce50-110">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2ce50-111">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2ce50-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2ce50-112">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="2ce50-112">listenIPAddress</span></span>|<span data-ttu-id="2ce50-113">Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.</span><span class="sxs-lookup"><span data-stu-id="2ce50-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="2ce50-114">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="2ce50-114">The default is `null`.</span></span>|  
|<span data-ttu-id="2ce50-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2ce50-115">maxBufferPoolSize</span></span>|<span data-ttu-id="2ce50-116">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2ce50-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="2ce50-117">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="2ce50-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="2ce50-118">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="2ce50-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="2ce50-119">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="2ce50-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="2ce50-120">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="2ce50-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="2ce50-121">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="2ce50-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="2ce50-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2ce50-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="2ce50-123">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2ce50-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="2ce50-124">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="2ce50-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="2ce50-125">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="2ce50-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="2ce50-126">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="2ce50-126">The default is 65536.</span></span>|  
|<span data-ttu-id="2ce50-127">name</span><span class="sxs-lookup"><span data-stu-id="2ce50-127">name</span></span>|<span data-ttu-id="2ce50-128">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="2ce50-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2ce50-129">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="2ce50-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2ce50-130">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="2ce50-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2ce50-131">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2ce50-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="2ce50-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="2ce50-132">openTimeout</span></span>|<span data-ttu-id="2ce50-133"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="2ce50-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2ce50-134">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2ce50-135">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2ce50-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2ce50-136">port</span><span class="sxs-lookup"><span data-stu-id="2ce50-136">port</span></span>|<span data-ttu-id="2ce50-137">Entier indiquant le port d’interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.</span><span class="sxs-lookup"><span data-stu-id="2ce50-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="2ce50-138">Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="2ce50-139">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="2ce50-139">The default is 0.</span></span>|  
|<span data-ttu-id="2ce50-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2ce50-140">receiveTimeout</span></span>|<span data-ttu-id="2ce50-141"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="2ce50-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2ce50-142">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2ce50-143">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="2ce50-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="2ce50-144">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="2ce50-144">sendTimeout</span></span>|<span data-ttu-id="2ce50-145"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="2ce50-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2ce50-146">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2ce50-147">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2ce50-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ce50-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ce50-148">Child Elements</span></span>  
  
|<span data-ttu-id="2ce50-149">Élément</span><span class="sxs-lookup"><span data-stu-id="2ce50-149">Element</span></span>|<span data-ttu-id="2ce50-150">Description</span><span class="sxs-lookup"><span data-stu-id="2ce50-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="2ce50-151">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2ce50-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2ce50-152">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="2ce50-153">Spécifie un programme de résolution d’homologue utilisé par cette liaison pour résoudre un ID de maille d’homologues en adresses IP de point de terminaison de nœuds dans la maille d’homologues.</span><span class="sxs-lookup"><span data-stu-id="2ce50-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="2ce50-154">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="2ce50-154">Defines the security settings for the message.</span></span> <span data-ttu-id="2ce50-155">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2ce50-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ce50-156">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ce50-156">Parent Elements</span></span>  
  
|<span data-ttu-id="2ce50-157">Élément</span><span class="sxs-lookup"><span data-stu-id="2ce50-157">Element</span></span>|<span data-ttu-id="2ce50-158">Description</span><span class="sxs-lookup"><span data-stu-id="2ce50-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="2ce50-159">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2ce50-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ce50-160">Remarques</span><span class="sxs-lookup"><span data-stu-id="2ce50-160">Remarks</span></span>  
 <span data-ttu-id="2ce50-161">Cette liaison assure la prise en charge de la création d'applications d'égal à égal ou entre plusieurs parties utilisant le transport d'homologue sur TCP.</span><span class="sxs-lookup"><span data-stu-id="2ce50-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="2ce50-162">Chaque nœud homologue peut héberger plusieurs canaux homologues définis avec ce type de liaison.</span><span class="sxs-lookup"><span data-stu-id="2ce50-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ce50-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ce50-163">Example</span></span>  
 <span data-ttu-id="2ce50-164">L’exemple suivant montre l’utilisation de la liaison NetPeerTcpBinding, qui fournit la communication pluripartite à l’aide d’un canal homologue.</span><span class="sxs-lookup"><span data-stu-id="2ce50-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="2ce50-165">Pour obtenir un scénario détaillé de l’utilisation de cette liaison, consultez [net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2ce50-165">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ce50-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ce50-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="2ce50-167">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2ce50-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2ce50-168">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="2ce50-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2ce50-169">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="2ce50-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="2ce50-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2ce50-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="2ce50-171">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="2ce50-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
