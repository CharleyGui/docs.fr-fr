---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 9f984759fb52242bf8030a101b567c14627dd314
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158693"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="68c39-102">\<security> de \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="68c39-102">\<security> of \<wsHttpBinding></span></span>

<span data-ttu-id="68c39-103">Représente les fonctionnalités de sécurité de [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="68c39-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="68c39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68c39-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68c39-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="68c39-105">Attributes and Elements</span></span>  

 <span data-ttu-id="68c39-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="68c39-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68c39-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="68c39-107">Attributes</span></span>  
  
|<span data-ttu-id="68c39-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="68c39-108">Attribute</span></span>|<span data-ttu-id="68c39-109">Description</span><span class="sxs-lookup"><span data-stu-id="68c39-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68c39-110">mode</span><span class="sxs-lookup"><span data-stu-id="68c39-110">mode</span></span>|<span data-ttu-id="68c39-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="68c39-111">-   Optional.</span></span> <span data-ttu-id="68c39-112">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="68c39-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="68c39-113">Par défaut, il s’agit de `Message`.</span><span class="sxs-lookup"><span data-stu-id="68c39-113">The default is `Message`.</span></span><br /><span data-ttu-id="68c39-114">-Cet attribut est de type <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="68c39-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="68c39-115">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="68c39-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="68c39-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="68c39-116">Value</span></span>|<span data-ttu-id="68c39-117">Description</span><span class="sxs-lookup"><span data-stu-id="68c39-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68c39-118">None</span><span class="sxs-lookup"><span data-stu-id="68c39-118">None</span></span>|<span data-ttu-id="68c39-119">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="68c39-119">Security is disabled.</span></span>|  
|<span data-ttu-id="68c39-120">Transport</span><span class="sxs-lookup"><span data-stu-id="68c39-120">Transport</span></span>|<span data-ttu-id="68c39-121">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="68c39-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="68c39-122">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="68c39-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="68c39-123">Le message est entièrement sécurisé grâce à HTTPS et est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="68c39-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="68c39-124">L'authentification du client est contrôlée à l'aide de l'attribut `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="68c39-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="68c39-125">de [\<transport>](transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="68c39-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="68c39-126">Message</span><span class="sxs-lookup"><span data-stu-id="68c39-126">Message</span></span>|<span data-ttu-id="68c39-127">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="68c39-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="68c39-128">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="68c39-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="68c39-129">Ce mode offre diverses fonctionnalités, telles que, si les informations d’identification du service sont disponibles au client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message grâce à la propriété Security.Message.</span><span class="sxs-lookup"><span data-stu-id="68c39-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="68c39-130">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="68c39-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="68c39-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="68c39-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="68c39-132">Dans ce mode, le protocole HTTPS garantit l'intégrité, la confidentialité et l'authentification du serveur, et la sécurité des messages SOAP garantit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="68c39-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="68c39-133">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="68c39-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68c39-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="68c39-134">Child Elements</span></span>  
  
|<span data-ttu-id="68c39-135">Élément</span><span class="sxs-lookup"><span data-stu-id="68c39-135">Element</span></span>|<span data-ttu-id="68c39-136">Description</span><span class="sxs-lookup"><span data-stu-id="68c39-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="68c39-137">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="68c39-137">Defines the transport security settings.</span></span> <span data-ttu-id="68c39-138">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="68c39-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="68c39-139">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="68c39-139">Defines the security settings for the message.</span></span> <span data-ttu-id="68c39-140">Cet élément correspond au type <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="68c39-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68c39-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="68c39-141">Parent Elements</span></span>  
  
|<span data-ttu-id="68c39-142">Élément</span><span class="sxs-lookup"><span data-stu-id="68c39-142">Element</span></span>|<span data-ttu-id="68c39-143">Description</span><span class="sxs-lookup"><span data-stu-id="68c39-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="68c39-144">Liaison sécurisée pour les applications de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="68c39-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68c39-145">Notes</span><span class="sxs-lookup"><span data-stu-id="68c39-145">Remarks</span></span>  

 <span data-ttu-id="68c39-146">La classe WSHttpBinding est conçue pour interagir avec les services qui implémentent les spécifications WS-\*.</span><span class="sxs-lookup"><span data-stu-id="68c39-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="68c39-147">La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS.</span><span class="sxs-lookup"><span data-stu-id="68c39-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c39-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68c39-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="68c39-149">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="68c39-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="68c39-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="68c39-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="68c39-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="68c39-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="68c39-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="68c39-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
