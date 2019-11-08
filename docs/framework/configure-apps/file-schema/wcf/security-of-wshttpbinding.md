---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738580"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="8266b-102">\<> de sécurité de \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8266b-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="8266b-103">Représente les fonctionnalités de sécurité du [\<wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8266b-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="8266b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8266b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8266b-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8266b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8266b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="8266b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="8266b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8266b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="8266b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="8266b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="8266b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="8266b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8266b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8266b-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8266b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8266b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8266b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8266b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8266b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="8266b-113">Attributes</span></span>  
  
|<span data-ttu-id="8266b-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="8266b-114">Attribute</span></span>|<span data-ttu-id="8266b-115">Description</span><span class="sxs-lookup"><span data-stu-id="8266b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8266b-116">mode</span><span class="sxs-lookup"><span data-stu-id="8266b-116">mode</span></span>|<span data-ttu-id="8266b-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8266b-117">-   Optional.</span></span> <span data-ttu-id="8266b-118">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="8266b-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="8266b-119">La valeur par défaut est `Message`,</span><span class="sxs-lookup"><span data-stu-id="8266b-119">The default is `Message`.</span></span><br /><span data-ttu-id="8266b-120">-Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8266b-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8266b-121">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="8266b-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="8266b-122">valeur</span><span class="sxs-lookup"><span data-stu-id="8266b-122">Value</span></span>|<span data-ttu-id="8266b-123">Description</span><span class="sxs-lookup"><span data-stu-id="8266b-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8266b-124">aucune.</span><span class="sxs-lookup"><span data-stu-id="8266b-124">None</span></span>|<span data-ttu-id="8266b-125">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="8266b-125">Security is disabled.</span></span>|  
|<span data-ttu-id="8266b-126">Transport</span><span class="sxs-lookup"><span data-stu-id="8266b-126">Transport</span></span>|<span data-ttu-id="8266b-127">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8266b-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="8266b-128">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="8266b-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="8266b-129">Le message est entièrement sécurisé grâce à HTTPS et est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="8266b-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="8266b-130">L'authentification du client est contrôlée à l'aide de l'attribut `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="8266b-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="8266b-131">du [> de transport\<](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8266b-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="8266b-132">Message</span><span class="sxs-lookup"><span data-stu-id="8266b-132">Message</span></span>|<span data-ttu-id="8266b-133">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="8266b-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="8266b-134">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="8266b-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="8266b-135">Ce mode offre diverses fonctionnalités, telles que, si les informations d’identification du service sont disponibles au client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message grâce à la propriété Security.Message.</span><span class="sxs-lookup"><span data-stu-id="8266b-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="8266b-136">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="8266b-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="8266b-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8266b-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="8266b-138">Dans ce mode, le protocole HTTPS garantit l'intégrité, la confidentialité et l'authentification du serveur, et la sécurité des messages SOAP garantit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="8266b-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="8266b-139">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="8266b-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8266b-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8266b-140">Child Elements</span></span>  
  
|<span data-ttu-id="8266b-141">Élément</span><span class="sxs-lookup"><span data-stu-id="8266b-141">Element</span></span>|<span data-ttu-id="8266b-142">Description</span><span class="sxs-lookup"><span data-stu-id="8266b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8266b-143">> de transport \<</span><span class="sxs-lookup"><span data-stu-id="8266b-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="8266b-144">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="8266b-144">Defines the transport security settings.</span></span> <span data-ttu-id="8266b-145">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8266b-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="8266b-146">message de \<</span><span class="sxs-lookup"><span data-stu-id="8266b-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="8266b-147">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="8266b-147">Defines the security settings for the message.</span></span> <span data-ttu-id="8266b-148">Cet élément correspond au type <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="8266b-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8266b-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8266b-149">Parent Elements</span></span>  
  
|<span data-ttu-id="8266b-150">Élément</span><span class="sxs-lookup"><span data-stu-id="8266b-150">Element</span></span>|<span data-ttu-id="8266b-151">Description</span><span class="sxs-lookup"><span data-stu-id="8266b-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8266b-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8266b-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="8266b-153">Liaison sécurisée pour les applications de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="8266b-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8266b-154">Notes</span><span class="sxs-lookup"><span data-stu-id="8266b-154">Remarks</span></span>  
 <span data-ttu-id="8266b-155">La classe WSHttpBinding est conçue pour interagir avec les services qui implémentent les spécifications WS-\*.</span><span class="sxs-lookup"><span data-stu-id="8266b-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="8266b-156">La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8266b-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8266b-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8266b-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="8266b-158">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="8266b-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8266b-159">Liaisons</span><span class="sxs-lookup"><span data-stu-id="8266b-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8266b-160">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="8266b-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8266b-161">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="8266b-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8266b-162">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="8266b-162">\<binding></span></span>](bindings.md)
