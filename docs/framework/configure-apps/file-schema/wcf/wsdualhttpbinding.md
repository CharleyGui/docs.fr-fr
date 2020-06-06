---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 01360ae8288b3cb7374597ad77935f634eb0a519
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139274"
---
# \<wsDualHttpBinding>
<span data-ttu-id="21931-101">Définit une liaison sécurisée, fiable et interopérable qui est appropriée pour les contrats de service ou les communications en duplex à travers des intermédiaires SOAP.</span><span class="sxs-lookup"><span data-stu-id="21931-101">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="21931-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21931-102">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21931-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="21931-103">Attributes and Elements</span></span>  
 <span data-ttu-id="21931-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="21931-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21931-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="21931-105">Attributes</span></span>  
  
|<span data-ttu-id="21931-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="21931-106">Attribute</span></span>|<span data-ttu-id="21931-107">Description</span><span class="sxs-lookup"><span data-stu-id="21931-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21931-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="21931-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="21931-109">Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="21931-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="21931-110">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="21931-110">The default is `false`.</span></span>|  
|<span data-ttu-id="21931-111">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="21931-111">clientBaseAddress</span></span>|<span data-ttu-id="21931-112">URI qui définit l'adresse de base que le client écoute pour les messages de réponse du service.</span><span class="sxs-lookup"><span data-stu-id="21931-112">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="21931-113">Si spécifiée, cette adresse (plus un GUID par canal) est utilisée pour écouter.</span><span class="sxs-lookup"><span data-stu-id="21931-113">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="21931-114">Si la valeur n'est pas spécifiée, l'adresse de base du client est générée de façon spécifique au transport.</span><span class="sxs-lookup"><span data-stu-id="21931-114">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="21931-115">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="21931-115">The default is `null`.</span></span>|  
|<span data-ttu-id="21931-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="21931-116">closeTimeout</span></span>|<span data-ttu-id="21931-117"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="21931-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="21931-118">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21931-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21931-119">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21931-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="21931-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="21931-120">hostnameComparisonMode</span></span>|<span data-ttu-id="21931-121">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="21931-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="21931-122">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="21931-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="21931-123">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="21931-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="21931-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="21931-124">maxBufferPoolSize</span></span>|<span data-ttu-id="21931-125">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="21931-126">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="21931-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="21931-127">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="21931-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="21931-128">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="21931-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="21931-129">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="21931-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="21931-130">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="21931-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="21931-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="21931-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="21931-132">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="21931-133">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="21931-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="21931-134">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="21931-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="21931-135">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="21931-135">The default is 65536.</span></span>|  
|<span data-ttu-id="21931-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="21931-136">messageEncoding</span></span>|<span data-ttu-id="21931-137">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="21931-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="21931-138">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="21931-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="21931-139">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="21931-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="21931-140">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="21931-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="21931-141">-La valeur par défaut est texte.</span><span class="sxs-lookup"><span data-stu-id="21931-141">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="21931-142">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="21931-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="21931-143">name</span><span class="sxs-lookup"><span data-stu-id="21931-143">name</span></span>|<span data-ttu-id="21931-144">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="21931-145">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="21931-146">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="21931-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="21931-147">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="21931-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="21931-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="21931-148">openTimeout</span></span>|<span data-ttu-id="21931-149"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="21931-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="21931-150">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21931-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21931-151">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21931-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="21931-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="21931-152">proxyAddress</span></span>|<span data-ttu-id="21931-153">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="21931-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="21931-154">Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="21931-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="21931-155">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="21931-155">The default is `null`.</span></span>|  
|<span data-ttu-id="21931-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="21931-156">receiveTimeout</span></span>|<span data-ttu-id="21931-157"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="21931-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="21931-158">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21931-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21931-159">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21931-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="21931-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="21931-160">sendTimeout</span></span>|<span data-ttu-id="21931-161"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="21931-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="21931-162">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21931-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21931-163">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21931-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="21931-164">textEncoding</span><span class="sxs-lookup"><span data-stu-id="21931-164">textEncoding</span></span>|<span data-ttu-id="21931-165">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="21931-166">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="21931-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="21931-167">-BigEndianUnicode : encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="21931-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="21931-168">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="21931-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="21931-169">-UTF8 : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="21931-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="21931-170">La valeur par défaut est UTF-8.</span><span class="sxs-lookup"><span data-stu-id="21931-170">The default is UTF8.</span></span> <span data-ttu-id="21931-171">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="21931-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="21931-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="21931-172">transactionFlow</span></span>|<span data-ttu-id="21931-173">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="21931-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="21931-174">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="21931-174">The default is `false`.</span></span>|  
|<span data-ttu-id="21931-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="21931-175">useDefaultWebProxy</span></span>|<span data-ttu-id="21931-176">Valeur booléenne qui indique si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="21931-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="21931-177">L'adresse proxy doit être `null` (autrement dit, pas de jeu) si cet attribut est `true`.</span><span class="sxs-lookup"><span data-stu-id="21931-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="21931-178">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="21931-178">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21931-179">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="21931-179">Child Elements</span></span>  
  
|<span data-ttu-id="21931-180">Élément</span><span class="sxs-lookup"><span data-stu-id="21931-180">Element</span></span>|<span data-ttu-id="21931-181">Description</span><span class="sxs-lookup"><span data-stu-id="21931-181">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="21931-182">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-182">Defines the security settings for the binding.</span></span> <span data-ttu-id="21931-183">Cet élément est de type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="21931-183">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="21931-184">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="21931-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="21931-185">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="21931-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="21931-186">Spécifie si des sessions fiables sont établies entre les points de terminaison du canal.</span><span class="sxs-lookup"><span data-stu-id="21931-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21931-187">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="21931-187">Parent Elements</span></span>  
  
|<span data-ttu-id="21931-188">Élément</span><span class="sxs-lookup"><span data-stu-id="21931-188">Element</span></span>|<span data-ttu-id="21931-189">Description</span><span class="sxs-lookup"><span data-stu-id="21931-189">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="21931-190">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="21931-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21931-191">Remarques</span><span class="sxs-lookup"><span data-stu-id="21931-191">Remarks</span></span>  
 <span data-ttu-id="21931-192">`WSDualHttpBinding` fournit la même prise en charge des protocoles de services Web que `WSHttpBinding`, mais pour des contrats duplex.</span><span class="sxs-lookup"><span data-stu-id="21931-192">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="21931-193">`WSDualHttpBinding` prend uniquement en charge la sécurité SOAP et requiert une messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="21931-193">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="21931-194">Dans le cadre de cette liaison, le client doit avoir un URI public servant de point de terminaison de rappel pour le service.</span><span class="sxs-lookup"><span data-stu-id="21931-194">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="21931-195">Cet élément est fourni par l'attribut `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="21931-195">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="21931-196">Une liaison double expose l'adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="21931-196">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="21931-197">Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.</span><span class="sxs-lookup"><span data-stu-id="21931-197">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="21931-198">Cette liaison peut être utilisée pour une communication fiable via un ou plusieurs intermédiaires SOAP.</span><span class="sxs-lookup"><span data-stu-id="21931-198">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="21931-199">Par défaut, cette liaison génère une pile de runtime avec WS-ReliableMessaging pour la fiabilité, WS-Security pour la sécurité et l’authentification des messages, HTTP pour la remise de messages et un encodage de messages Texte/XML.</span><span class="sxs-lookup"><span data-stu-id="21931-199">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21931-200">Exemple</span><span class="sxs-lookup"><span data-stu-id="21931-200">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="21931-201">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21931-201">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="21931-202">Liaisons</span><span class="sxs-lookup"><span data-stu-id="21931-202">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="21931-203">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="21931-203">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="21931-204">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="21931-204">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
