---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2fb9f7a16a360ddd61e6f8b935f928ddfdeb6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915253"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="984be-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="984be-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="984be-102">Définit une liaison interopérable qui assure la prise en charge des versions appropriées des éléments de liaison <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession> et <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.</span><span class="sxs-lookup"><span data-stu-id="984be-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="984be-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="984be-103">\<system.serviceModel></span></span>  
<span data-ttu-id="984be-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="984be-104">\<bindings></span></span>  
<span data-ttu-id="984be-105">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="984be-105">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="984be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="984be-106">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="984be-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="984be-107">Attributes and Elements</span></span>  
 <span data-ttu-id="984be-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="984be-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="984be-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="984be-109">Attributes</span></span>  
  
|<span data-ttu-id="984be-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="984be-110">Attribute</span></span>|<span data-ttu-id="984be-111">Description</span><span class="sxs-lookup"><span data-stu-id="984be-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="984be-112">Valeur qui indique si le client accepte les cookies et les propage aux demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="984be-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="984be-113">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="984be-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="984be-114">Vous pouvez utiliser cette propriété lors de l'interaction avec des services Web ASP.NET (ASMX) qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="984be-114">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="984be-115">Cela garantit que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.</span><span class="sxs-lookup"><span data-stu-id="984be-115">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="984be-116">Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="984be-116">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="984be-117">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="984be-117">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="984be-118">Valeur <xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="984be-118">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="984be-119">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="984be-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="984be-120">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="984be-120">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="984be-121">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="984be-121">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="984be-122">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="984be-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="984be-123">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="984be-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="984be-124">Taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-124">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="984be-125">La valeur par défaut est 524 288 octets (512 × 1 024).</span><span class="sxs-lookup"><span data-stu-id="984be-125">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="984be-126">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="984be-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="984be-127">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme le processus de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="984be-127">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="984be-128">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la renvoyer dans le pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="984be-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="984be-129">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="984be-129">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="984be-130">Taille maximale du message (en octets), en-têtes compris, qu’un canal configuré avec cette liaison peut recevoir.</span><span class="sxs-lookup"><span data-stu-id="984be-130">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="984be-131">L'expéditeur d'un message dépassant cette limite reçoit une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="984be-131">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="984be-132">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="984be-132">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="984be-133">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="984be-133">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="984be-134">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="984be-134">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="984be-135">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="984be-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="984be-136">-   `Text` : Utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="984be-136">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="984be-137">-   `Mtom` : Utilisez un encodeur de transmission de message (MTOM) message transmission Organization 1,0.</span><span class="sxs-lookup"><span data-stu-id="984be-137">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="984be-138">Par défaut, il s’agit de `Text`.</span><span class="sxs-lookup"><span data-stu-id="984be-138">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="984be-139">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="984be-139">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="984be-140">Nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-140">The configuration name of the binding.</span></span> <span data-ttu-id="984be-141">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="984be-142">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="984be-142">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="984be-143">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="984be-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="984be-144"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="984be-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="984be-145">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="984be-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="984be-146">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="984be-146">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="984be-147">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="984be-147">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="984be-148">Si `useSystemWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="984be-148">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="984be-149">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="984be-149">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="984be-150"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="984be-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="984be-151">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="984be-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="984be-152">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="984be-152">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="984be-153"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="984be-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="984be-154">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="984be-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="984be-155">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="984be-155">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="984be-156">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-156">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="984be-157">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="984be-157">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="984be-158">-   `UnicodeFffeTextEncoding` : Encodage Unicode Big endian.</span><span class="sxs-lookup"><span data-stu-id="984be-158">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="984be-159">-   `Utf16TextEncoding` : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="984be-159">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="984be-160">-   `Utf8TextEncoding` : encodage 8 bits.</span><span class="sxs-lookup"><span data-stu-id="984be-160">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="984be-161">Par défaut, il s’agit de `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="984be-161">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="984be-162">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="984be-162">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="984be-163">Valeur indiquant si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="984be-163">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="984be-164">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="984be-164">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="984be-165">Valeur qui spécifie si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="984be-165">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="984be-166">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="984be-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="984be-167">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="984be-167">Child Elements</span></span>  
  
|<span data-ttu-id="984be-168">Élément</span><span class="sxs-lookup"><span data-stu-id="984be-168">Element</span></span>|<span data-ttu-id="984be-169">Description</span><span class="sxs-lookup"><span data-stu-id="984be-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="984be-170">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="984be-170">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="984be-171">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-171">Defines the security settings for the binding.</span></span> <span data-ttu-id="984be-172">Cet élément est de type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="984be-172">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="984be-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="984be-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="984be-174">Définit les contraintes de la complexité des messages SOAP que peuvent traiter les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-174">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="984be-175">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="984be-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="984be-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="984be-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="984be-177">Indique si des sessions fiables sont établies entre les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="984be-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="984be-178">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="984be-178">Parent Elements</span></span>  
  
|<span data-ttu-id="984be-179">Élément</span><span class="sxs-lookup"><span data-stu-id="984be-179">Element</span></span>|<span data-ttu-id="984be-180">Description</span><span class="sxs-lookup"><span data-stu-id="984be-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="984be-181">\<bindings></span><span class="sxs-lookup"><span data-stu-id="984be-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="984be-182">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="984be-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="984be-183">Notes</span><span class="sxs-lookup"><span data-stu-id="984be-183">Remarks</span></span>  
 <span data-ttu-id="984be-184">`WS2007HttpBinding` ajoute une liaison fournie par le système semblable à `WSHttpBinding`, mais utilise les versions OASIS (Organization for the Advancement of Structured Information Standards) standard des protocoles ReliableSession, Security et TransactionFlow.</span><span class="sxs-lookup"><span data-stu-id="984be-184">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="984be-185">Aucune modification du modèle objet ou des paramètres par défaut n’est requise en cas d’utilisation de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="984be-185">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="984be-186">Exemple</span><span class="sxs-lookup"><span data-stu-id="984be-186">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="984be-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="984be-187">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="984be-188">Liaisons</span><span class="sxs-lookup"><span data-stu-id="984be-188">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="984be-189">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="984be-189">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="984be-190">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="984be-190">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="984be-191">\<binding></span><span class="sxs-lookup"><span data-stu-id="984be-191">\<binding></span></span>](../../../misc/binding.md)
