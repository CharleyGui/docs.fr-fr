---
title: <netTcpBinding>
description: Représente une liaison sécurisée, fiable et optimisée, conçue uniquement pour la communication entre ordinateurs WCF à l’aide de TCP. La messagerie fiable est désactivée par défaut.
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: a366b26d87c8796822e4fbbb2001823c116f2629
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556126"
---
# \<netTcpBinding>

<span data-ttu-id="155b2-103">Spécifie une liaison sécurisée, fiable et optimisée, adaptée à la communication entre ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="155b2-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="155b2-104">Par défaut, elle génère une pile de communication du runtime avec Windows Security pour la sécurité et l'authentification des messages, TCP pour la remise de messages et un encodage de message binaire.</span><span class="sxs-lookup"><span data-stu-id="155b2-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="155b2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="155b2-105">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="155b2-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="155b2-106">Attributes and elements</span></span>

<span data-ttu-id="155b2-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="155b2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="155b2-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="155b2-108">Attributes</span></span>  
  
|<span data-ttu-id="155b2-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="155b2-109">Attribute</span></span>|<span data-ttu-id="155b2-110">Description</span><span class="sxs-lookup"><span data-stu-id="155b2-110">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="155b2-111"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="155b2-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="155b2-112">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="155b2-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="155b2-113">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="155b2-113">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="155b2-114">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="155b2-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="155b2-115">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="155b2-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="155b2-116">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="155b2-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="155b2-117">Entier positif qui spécifie le nombre maximal des canaux en attente d'être acceptés sur l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="155b2-117">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="155b2-118">Les connexions dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible en dessous cette limite.</span><span class="sxs-lookup"><span data-stu-id="155b2-118">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="155b2-119">L'attribut `connectionTimeout` limite le temps que devra attendre un client pour être connecté avant de lever une exception de connexion.</span><span class="sxs-lookup"><span data-stu-id="155b2-119">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="155b2-120">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="155b2-120">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="155b2-121">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="155b2-122">La valeur par défaut est 512 x 1024 octets.</span><span class="sxs-lookup"><span data-stu-id="155b2-122">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="155b2-123">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="155b2-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="155b2-124">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="155b2-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="155b2-125">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="155b2-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="155b2-126">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="155b2-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="155b2-127">Entier positif qui spécifie la taille maximale, en octets, de la mémoire tampon utilisée pour stocker des messages en mémoire.</span><span class="sxs-lookup"><span data-stu-id="155b2-127">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="155b2-128">Si l'attribut `transferMode` est égal à `Buffered`, cet attribut doit être égal à la valeur de l'attribut `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="155b2-128">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="155b2-129">Si l'attribut `transferMode` est égal à `Streamed`, cet attribut ne peut pas être supérieur à la valeur de l'attribut `maxReceivedMessageSize` et doit être au moins de la taille des en-têtes.</span><span class="sxs-lookup"><span data-stu-id="155b2-129">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="155b2-130">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="155b2-130">The default is 65536.</span></span> <span data-ttu-id="155b2-131">Pour plus d'informations, consultez <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="155b2-131">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="155b2-132">Entier qui spécifie le nombre maximal de connexions sortantes et entrantes que le service créera/acceptera.</span><span class="sxs-lookup"><span data-stu-id="155b2-132">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="155b2-133">Les connexions entrantes et sortantes sont comptées par rapport à une limite distincte spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="155b2-133">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="155b2-134">Les connexions entrantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="155b2-134">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="155b2-135">Les connexions sortantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="155b2-135">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="155b2-136">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="155b2-136">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="155b2-137">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="155b2-138">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="155b2-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="155b2-139">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="155b2-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="155b2-140">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="155b2-140">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="155b2-141">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-141">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="155b2-142">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="155b2-143">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="155b2-143">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="155b2-144">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="155b2-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="155b2-145"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="155b2-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="155b2-146">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="155b2-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="155b2-147">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="155b2-147">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="155b2-148">Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="155b2-148">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="155b2-149">Si elle est définie à `false`, chaque de liaison utilise son propre port exclusif.</span><span class="sxs-lookup"><span data-stu-id="155b2-149">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="155b2-150">Ce paramètre est uniquement pertinent aux services, du fait que les clients ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="155b2-150">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="155b2-151"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="155b2-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="155b2-152">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="155b2-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="155b2-153">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="155b2-153">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="155b2-154"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="155b2-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="155b2-155">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="155b2-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="155b2-156">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="155b2-156">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="155b2-157">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="155b2-157">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="155b2-158">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="155b2-158">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="155b2-159">Spécifie le protocole de transaction à utiliser avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-159">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="155b2-160">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="155b2-160">Valid values are</span></span><br /><br /> <span data-ttu-id="155b2-161">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="155b2-161">-   OleTransactions</span></span><br /><span data-ttu-id="155b2-162">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="155b2-162">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="155b2-163">La valeur par défaut est OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="155b2-163">The default is OleTransactions.</span></span> <span data-ttu-id="155b2-164">Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="155b2-164">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="155b2-165">Valeur <xref:System.ServiceModel.TransferMode> qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="155b2-165">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="155b2-166">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="155b2-166">Child elements</span></span>  
  
|<span data-ttu-id="155b2-167">Élément</span><span class="sxs-lookup"><span data-stu-id="155b2-167">Element</span></span>|<span data-ttu-id="155b2-168">Description</span><span class="sxs-lookup"><span data-stu-id="155b2-168">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="155b2-169">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-169">Defines the security settings for the binding.</span></span> <span data-ttu-id="155b2-170">Cet élément est de type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="155b2-170">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="155b2-171">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-171">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="155b2-172">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="155b2-172">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="155b2-173">Spécifie si des sessions fiables sont établies entre les points de terminaison du canal.</span><span class="sxs-lookup"><span data-stu-id="155b2-173">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="155b2-174">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="155b2-174">Parent elements</span></span>  
  
|<span data-ttu-id="155b2-175">Élément</span><span class="sxs-lookup"><span data-stu-id="155b2-175">Element</span></span>|<span data-ttu-id="155b2-176">Description</span><span class="sxs-lookup"><span data-stu-id="155b2-176">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="155b2-177">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="155b2-177">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="155b2-178">Notes</span><span class="sxs-lookup"><span data-stu-id="155b2-178">Remarks</span></span>

<span data-ttu-id="155b2-179">Par défaut, cette liaison génère une pile de communication au moment de l'exécution, qui utilise la sécurité de transport, le protocole TCP pour la remise des messages et un encodage de message binaire.</span><span class="sxs-lookup"><span data-stu-id="155b2-179">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="155b2-180">Cette liaison est un choix approprié fourni par le système Windows Communication Foundation (WCF) pour communiquer sur un intranet.</span><span class="sxs-lookup"><span data-stu-id="155b2-180">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="155b2-181">La configuration par défaut de `netTcpBinding` est plus rapide que la configuration fournie par le `wsHttpBinding` , mais elle est destinée uniquement à la communication WCF.</span><span class="sxs-lookup"><span data-stu-id="155b2-181">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="155b2-182">Le comportement de sécurité est configurable à l'aide de l'attribut facultatif `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="155b2-182">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="155b2-183">L'utilisation de WS-ReliableMessaging peut être configurée à l'aide de l'attribut facultatif `reliableSessionEnabled`.</span><span class="sxs-lookup"><span data-stu-id="155b2-183">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="155b2-184">Mais les fonctionnalités de messagerie fiable sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="155b2-184">But reliable messaging is off by default.</span></span> <span data-ttu-id="155b2-185">Plus généralement, les liaisons fournies par le système HTTP telles que `wsHttpBinding` et `basicHttpBinding` sont configurées pour activer certains éléments par défaut, alors que la liaison `netTcpBinding` en désactive par défaut. Par conséquent, vous devez demander de l’aide explicitement, par exemple pour les spécifications WS - \*.</span><span class="sxs-lookup"><span data-stu-id="155b2-185">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="155b2-186">Ainsi, la configuration TCP par défaut permet d’échanger des messages entre points de terminaison plus rapidement que ceux configurés par défaut pour les liaisons HTTP.</span><span class="sxs-lookup"><span data-stu-id="155b2-186">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="155b2-187"> Exemple</span><span class="sxs-lookup"><span data-stu-id="155b2-187">Example</span></span>

<span data-ttu-id="155b2-188">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="155b2-188">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="155b2-189">Le type de liaison est spécifié dans l’attribut `binding` de l’élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="155b2-189">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="155b2-190">Si vous souhaitez configurer la liaison netTcpBinding et modifier quelques-uns de ses paramètres, il est nécessaire de définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="155b2-190">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="155b2-191">Le point de terminaison doit référencer la configuration de liaison avec un attribut `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="155b2-191">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="155b2-192">Dans l’exemple suivant, une configuration de liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="155b2-192">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="155b2-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="155b2-193">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="155b2-194">Liaisons</span><span class="sxs-lookup"><span data-stu-id="155b2-194">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="155b2-195">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="155b2-195">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="155b2-196">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="155b2-196">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
