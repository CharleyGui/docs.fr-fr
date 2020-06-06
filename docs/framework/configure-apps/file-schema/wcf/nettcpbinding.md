---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c43c141093c8287adb6d5a841a43ac893deefccd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139345"
---
# \<netTcpBinding>

<span data-ttu-id="15029-101">Spécifie une liaison sécurisée, fiable et optimisée, adaptée à la communication entre ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="15029-101">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="15029-102">Par défaut, elle génère une pile de communication du runtime avec Windows Security pour la sécurité et l'authentification des messages, TCP pour la remise de messages et un encodage de message binaire.</span><span class="sxs-lookup"><span data-stu-id="15029-102">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="15029-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15029-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15029-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="15029-104">Attributes and elements</span></span>

<span data-ttu-id="15029-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="15029-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15029-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="15029-106">Attributes</span></span>  
  
|<span data-ttu-id="15029-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="15029-107">Attribute</span></span>|<span data-ttu-id="15029-108">Description</span><span class="sxs-lookup"><span data-stu-id="15029-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="15029-109"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="15029-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="15029-110">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="15029-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="15029-111">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="15029-111">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="15029-112">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="15029-112">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="15029-113">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="15029-113">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="15029-114">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="15029-114">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="15029-115">Entier positif qui spécifie le nombre maximal des canaux en attente d'être acceptés sur l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="15029-115">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="15029-116">Les connexions dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible en dessous cette limite.</span><span class="sxs-lookup"><span data-stu-id="15029-116">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="15029-117">L'attribut `connectionTimeout` limite le temps que devra attendre un client pour être connecté avant de lever une exception de connexion.</span><span class="sxs-lookup"><span data-stu-id="15029-117">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="15029-118">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="15029-118">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="15029-119">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="15029-120">La valeur par défaut est 512 x 1024 octets.</span><span class="sxs-lookup"><span data-stu-id="15029-120">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="15029-121">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="15029-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="15029-122">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="15029-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="15029-123">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="15029-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="15029-124">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="15029-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="15029-125">Entier positif qui spécifie la taille maximale, en octets, de la mémoire tampon utilisée pour stocker des messages en mémoire.</span><span class="sxs-lookup"><span data-stu-id="15029-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="15029-126">Si l'attribut `transferMode` est égal à `Buffered`, cet attribut doit être égal à la valeur de l'attribut `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="15029-126">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="15029-127">Si l'attribut `transferMode` est égal à `Streamed`, cet attribut ne peut pas être supérieur à la valeur de l'attribut `maxReceivedMessageSize` et doit être au moins de la taille des en-têtes.</span><span class="sxs-lookup"><span data-stu-id="15029-127">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="15029-128">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="15029-128">The default is 65536.</span></span> <span data-ttu-id="15029-129">Pour plus d’informations, consultez <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="15029-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="15029-130">Entier qui spécifie le nombre maximal de connexions sortantes et entrantes que le service créera/acceptera.</span><span class="sxs-lookup"><span data-stu-id="15029-130">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="15029-131">Les connexions entrantes et sortantes sont comptées par rapport à une limite distincte spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="15029-131">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="15029-132">Les connexions entrantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="15029-132">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="15029-133">Les connexions sortantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="15029-133">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="15029-134">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="15029-134">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="15029-135">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="15029-136">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="15029-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="15029-137">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="15029-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="15029-138">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="15029-138">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="15029-139">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="15029-140">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="15029-141">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="15029-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="15029-142">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="15029-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="15029-143"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="15029-143">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="15029-144">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="15029-144">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="15029-145">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="15029-145">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="15029-146">Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="15029-146">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="15029-147">Si elle est définie à `false`, chaque de liaison utilise son propre port exclusif.</span><span class="sxs-lookup"><span data-stu-id="15029-147">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="15029-148">Ce paramètre est uniquement pertinent aux services, du fait que les clients ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="15029-148">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="15029-149"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="15029-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="15029-150">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="15029-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="15029-151">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="15029-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="15029-152"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="15029-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="15029-153">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="15029-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="15029-154">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="15029-154">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="15029-155">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="15029-155">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="15029-156">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="15029-156">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="15029-157">Spécifie le protocole de transaction à utiliser avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-157">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="15029-158">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="15029-158">Valid values are</span></span><br /><br /> <span data-ttu-id="15029-159">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="15029-159">-   OleTransactions</span></span><br /><span data-ttu-id="15029-160">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="15029-160">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="15029-161">La valeur par défaut est OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="15029-161">The default is OleTransactions.</span></span> <span data-ttu-id="15029-162">Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="15029-162">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="15029-163">Valeur <xref:System.ServiceModel.TransferMode> qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="15029-163">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15029-164">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="15029-164">Child elements</span></span>  
  
|<span data-ttu-id="15029-165">Élément</span><span class="sxs-lookup"><span data-stu-id="15029-165">Element</span></span>|<span data-ttu-id="15029-166">Description</span><span class="sxs-lookup"><span data-stu-id="15029-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="15029-167">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="15029-168">Cet élément est de type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="15029-168">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="15029-169">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-169">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="15029-170">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="15029-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="15029-171">Spécifie si des sessions fiables sont établies entre les points de terminaison du canal.</span><span class="sxs-lookup"><span data-stu-id="15029-171">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15029-172">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="15029-172">Parent elements</span></span>  
  
|<span data-ttu-id="15029-173">Élément</span><span class="sxs-lookup"><span data-stu-id="15029-173">Element</span></span>|<span data-ttu-id="15029-174">Description</span><span class="sxs-lookup"><span data-stu-id="15029-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="15029-175">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="15029-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15029-176">Remarques</span><span class="sxs-lookup"><span data-stu-id="15029-176">Remarks</span></span>

<span data-ttu-id="15029-177">Par défaut, cette liaison génère une pile de communication au moment de l'exécution, qui utilise la sécurité de transport, le protocole TCP pour la remise des messages et un encodage de message binaire.</span><span class="sxs-lookup"><span data-stu-id="15029-177">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="15029-178">Cette liaison est un choix approprié fourni par le système Windows Communication Foundation (WCF) pour communiquer sur un intranet.</span><span class="sxs-lookup"><span data-stu-id="15029-178">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="15029-179">La configuration par défaut de `netTcpBinding` est plus rapide que la configuration fournie par le `wsHttpBinding` , mais elle est destinée uniquement à la communication WCF.</span><span class="sxs-lookup"><span data-stu-id="15029-179">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="15029-180">Le comportement de sécurité est configurable à l'aide de l'attribut facultatif `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="15029-180">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="15029-181">L'utilisation de WS-ReliableMessaging peut être configurée à l'aide de l'attribut facultatif `reliableSessionEnabled`.</span><span class="sxs-lookup"><span data-stu-id="15029-181">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="15029-182">Mais les fonctionnalités de messagerie fiable sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="15029-182">But reliable messaging is off by default.</span></span> <span data-ttu-id="15029-183">Plus généralement, les liaisons fournies par le système HTTP telles que `wsHttpBinding` et `basicHttpBinding` sont configurées pour activer certains éléments par défaut, alors que la liaison `netTcpBinding` en désactive par défaut. Par conséquent, vous devez demander de l’aide explicitement, par exemple pour les spécifications WS - \*.</span><span class="sxs-lookup"><span data-stu-id="15029-183">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="15029-184">Ainsi, la configuration TCP par défaut permet d’échanger des messages entre points de terminaison plus rapidement que ceux configurés par défaut pour les liaisons HTTP.</span><span class="sxs-lookup"><span data-stu-id="15029-184">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15029-185">Exemple</span><span class="sxs-lookup"><span data-stu-id="15029-185">Example</span></span>

<span data-ttu-id="15029-186">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="15029-186">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="15029-187">Le type de liaison est spécifié dans l’attribut `binding` de l’élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="15029-187">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="15029-188">Si vous souhaitez configurer la liaison netTcpBinding et modifier quelques-uns de ses paramètres, il est nécessaire de définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="15029-188">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="15029-189">Le point de terminaison doit référencer la configuration de liaison avec un attribut `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="15029-189">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="15029-190">Dans l’exemple suivant, une configuration de liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="15029-190">In the following example, a binding configuration is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15029-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15029-191">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="15029-192">Liaisons</span><span class="sxs-lookup"><span data-stu-id="15029-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="15029-193">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="15029-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="15029-194">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="15029-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
