---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139468"
---
# \<netNamedPipeBinding>
<span data-ttu-id="5c3af-101">Définit une liaison qui est sécurisée, fiable, optimisée pour la communication interprocessus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5c3af-101">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="5c3af-102">Par défaut, elle génère une pile de communication du runtime avec WS-ReliableMessaging pour la fiabilité, la sécurité du transport pour la sécurité du transfert, des canaux nommés pour la remise de messages et l'encodage binaire de messages.</span><span class="sxs-lookup"><span data-stu-id="5c3af-102">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="5c3af-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c3af-103">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c3af-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5c3af-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5c3af-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5c3af-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c3af-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="5c3af-106">Attributes</span></span>  
  
|<span data-ttu-id="5c3af-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="5c3af-107">Attribute</span></span>|<span data-ttu-id="5c3af-108">Description</span><span class="sxs-lookup"><span data-stu-id="5c3af-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c3af-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="5c3af-109">closeTimeout</span></span>|<span data-ttu-id="5c3af-110"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="5c3af-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5c3af-111">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c3af-112">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5c3af-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5c3af-113">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="5c3af-113">hostNameComparisonMode</span></span>|<span data-ttu-id="5c3af-114">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="5c3af-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="5c3af-115">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="5c3af-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="5c3af-116">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="5c3af-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="5c3af-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5c3af-117">maxBufferPoolSize</span></span>|<span data-ttu-id="5c3af-118">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-118">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="5c3af-119">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="5c3af-119">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="5c3af-120">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="5c3af-120">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="5c3af-121">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="5c3af-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="5c3af-122">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="5c3af-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="5c3af-123">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="5c3af-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="5c3af-124">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="5c3af-124">maxBufferSize</span></span>|<span data-ttu-id="5c3af-125">Entier positif qui spécifie la taille maximale, en octets, de la mémoire tampon utilisée pour stocker des messages en mémoire.</span><span class="sxs-lookup"><span data-stu-id="5c3af-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="5c3af-126">Si la mémoire tampon est pleine, les données excédentaires restent dans le socket sous-jacent jusqu'à ce que de l'espace disponible se libère dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5c3af-126">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="5c3af-127">Cette valeur ne peut pas être inférieure à l'attribut `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="5c3af-127">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="5c3af-128">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="5c3af-128">The default is 65536.</span></span> <span data-ttu-id="5c3af-129">Pour plus d’informations, consultez <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="5c3af-130">maxConnections</span><span class="sxs-lookup"><span data-stu-id="5c3af-130">maxConnections</span></span>|<span data-ttu-id="5c3af-131">Entier qui spécifie le nombre maximal de connexions sortantes et entrantes que le service créera/acceptera.</span><span class="sxs-lookup"><span data-stu-id="5c3af-131">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="5c3af-132">Les connexions entrantes et sortantes sont comptées par rapport à une limite distincte spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="5c3af-132">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="5c3af-133">Les connexions entrantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="5c3af-133">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="5c3af-134">Les connexions sortantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="5c3af-134">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="5c3af-135">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="5c3af-135">The default is 10.</span></span>|  
|<span data-ttu-id="5c3af-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5c3af-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="5c3af-137">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5c3af-138">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c3af-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="5c3af-139">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="5c3af-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5c3af-140">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="5c3af-140">The default is 65536.</span></span>|  
|<span data-ttu-id="5c3af-141">name</span><span class="sxs-lookup"><span data-stu-id="5c3af-141">name</span></span>|<span data-ttu-id="5c3af-142">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-142">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5c3af-143">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-143">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5c3af-144">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="5c3af-144">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5c3af-145">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5c3af-145">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="5c3af-146">openTimeout</span><span class="sxs-lookup"><span data-stu-id="5c3af-146">openTimeout</span></span>|<span data-ttu-id="5c3af-147"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="5c3af-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5c3af-148">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c3af-149">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5c3af-149">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5c3af-150">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5c3af-150">receiveTimeout</span></span>|<span data-ttu-id="5c3af-151"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="5c3af-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5c3af-152">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c3af-153">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5c3af-153">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="5c3af-154">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="5c3af-154">sendTimeout</span></span>|<span data-ttu-id="5c3af-155"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5c3af-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5c3af-156">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c3af-157">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5c3af-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5c3af-158">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="5c3af-158">transactionFlow</span></span>|<span data-ttu-id="5c3af-159">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="5c3af-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="5c3af-160">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="5c3af-160">The default is `false`.</span></span>|  
|<span data-ttu-id="5c3af-161">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="5c3af-161">transactionProtocol</span></span>|<span data-ttu-id="5c3af-162">Spécifie le protocole de transaction à utiliser avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="5c3af-163">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c3af-163">Valid values are</span></span><br /><br /> <span data-ttu-id="5c3af-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="5c3af-164">-   OleTransactions</span></span><br /><span data-ttu-id="5c3af-165">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="5c3af-165">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="5c3af-166">La valeur par défaut est OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="5c3af-166">The default is OleTransactions.</span></span> <span data-ttu-id="5c3af-167">Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="5c3af-168">transferMode</span><span class="sxs-lookup"><span data-stu-id="5c3af-168">transferMode</span></span>|<span data-ttu-id="5c3af-169">Valeur <xref:System.ServiceModel.TransferMode> qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="5c3af-169">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c3af-170">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5c3af-170">Child Elements</span></span>  
  
|<span data-ttu-id="5c3af-171">Élément</span><span class="sxs-lookup"><span data-stu-id="5c3af-171">Element</span></span>|<span data-ttu-id="5c3af-172">Description</span><span class="sxs-lookup"><span data-stu-id="5c3af-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="5c3af-173">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="5c3af-174">Cet élément est de type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-174">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="5c3af-175">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5c3af-176">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5c3af-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c3af-177">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5c3af-177">Parent Elements</span></span>  
  
|<span data-ttu-id="5c3af-178">Élément</span><span class="sxs-lookup"><span data-stu-id="5c3af-178">Element</span></span>|<span data-ttu-id="5c3af-179">Description</span><span class="sxs-lookup"><span data-stu-id="5c3af-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="5c3af-180">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5c3af-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c3af-181">Remarques</span><span class="sxs-lookup"><span data-stu-id="5c3af-181">Remarks</span></span>  
 <span data-ttu-id="5c3af-182">`NetNamedPipeBinding` génère par défaut une pile de communication au moment de l'exécution, qui utilise la sécurité de transport, des canaux nommés pour la remise des messages et un encodage de message binaire.</span><span class="sxs-lookup"><span data-stu-id="5c3af-182">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="5c3af-183">Cette liaison est une solution fournie par le système WCF (Windows Communication Foundation) adaptée à la communication sur les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5c3af-183">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="5c3af-184">Elle prend en outre en charge des transactions.</span><span class="sxs-lookup"><span data-stu-id="5c3af-184">It also supports transactions.</span></span>  
  
 <span data-ttu-id="5c3af-185">La configuration par défaut de `NetNamedPipeBinding` est similaire à celle fournie par `NetTcpBinding`, mais en plus simple, car l’implémentation de WCF est uniquement destinée à être utilisée sur un ordinateur, de sorte qu’il y a moins de fonctionnalités exposées.</span><span class="sxs-lookup"><span data-stu-id="5c3af-185">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="5c3af-186">La différence la plus notable est que le paramètre `securityMode` offre uniquement les options `None` et `Transport`.</span><span class="sxs-lookup"><span data-stu-id="5c3af-186">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="5c3af-187">La prise en charge de la sécurité SOAP ne fait pas partie des options incluses.</span><span class="sxs-lookup"><span data-stu-id="5c3af-187">SOAP security support is not an included option.</span></span> <span data-ttu-id="5c3af-188">Le comportement de sécurité est configurable à l'aide de l'attribut facultatif `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="5c3af-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c3af-189">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c3af-189">Example</span></span>  
 <span data-ttu-id="5c3af-190">L’exemple suivant montre la liaison netNamedPipeBinding, qui fournit la communication interprocessus sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5c3af-190">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="5c3af-191">Les canaux nommés ne fonctionnent pas sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5c3af-191">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="5c3af-192">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="5c3af-192">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="5c3af-193">Le type de liaison est spécifié dans l’attribut `binding` de l’élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="5c3af-193">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="5c3af-194">Si vous souhaitez configurer la liaison netNamedPipeBinding et modifier quelques-uns de ses paramètres, vous devez définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="5c3af-194">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="5c3af-195">Le point de terminaison doit référencer la configuration de liaison par nom avec un attribut `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="5c3af-195">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="5c3af-196">Dans cet exemple, la configuration de liaison est nommée Binding1.</span><span class="sxs-lookup"><span data-stu-id="5c3af-196">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="5c3af-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c3af-197">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="5c3af-198">Liaisons</span><span class="sxs-lookup"><span data-stu-id="5c3af-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c3af-199">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="5c3af-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c3af-200">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="5c3af-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
