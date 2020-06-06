---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738580"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="a9748-102">\<security> de \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a9748-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="a9748-103">Représente les fonctionnalités de sécurité de [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a9748-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a9748-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9748-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9748-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a9748-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a9748-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a9748-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9748-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a9748-107">Attributes</span></span>  
  
|<span data-ttu-id="a9748-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a9748-108">Attribute</span></span>|<span data-ttu-id="a9748-109">Description</span><span class="sxs-lookup"><span data-stu-id="a9748-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9748-110">mode</span><span class="sxs-lookup"><span data-stu-id="a9748-110">mode</span></span>|<span data-ttu-id="a9748-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a9748-111">-   Optional.</span></span> <span data-ttu-id="a9748-112">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="a9748-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a9748-113">Par défaut, il s’agit de `Message`.</span><span class="sxs-lookup"><span data-stu-id="a9748-113">The default is `Message`.</span></span><br /><span data-ttu-id="a9748-114">-Cet attribut est de type <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="a9748-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a9748-115">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="a9748-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="a9748-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="a9748-116">Value</span></span>|<span data-ttu-id="a9748-117">Description</span><span class="sxs-lookup"><span data-stu-id="a9748-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a9748-118">None</span><span class="sxs-lookup"><span data-stu-id="a9748-118">None</span></span>|<span data-ttu-id="a9748-119">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a9748-119">Security is disabled.</span></span>|  
|<span data-ttu-id="a9748-120">Transport</span><span class="sxs-lookup"><span data-stu-id="a9748-120">Transport</span></span>|<span data-ttu-id="a9748-121">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9748-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="a9748-122">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="a9748-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="a9748-123">Le message est entièrement sécurisé grâce à HTTPS et est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="a9748-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a9748-124">L'authentification du client est contrôlée à l'aide de l'attribut `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="a9748-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="a9748-125">de [\<transport>](transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a9748-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="a9748-126">Message</span><span class="sxs-lookup"><span data-stu-id="a9748-126">Message</span></span>|<span data-ttu-id="a9748-127">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="a9748-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a9748-128">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="a9748-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="a9748-129">Ce mode offre diverses fonctionnalités, telles que, si les informations d’identification du service sont disponibles au client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message grâce à la propriété Security.Message.</span><span class="sxs-lookup"><span data-stu-id="a9748-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="a9748-130">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="a9748-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="a9748-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a9748-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="a9748-132">Dans ce mode, le protocole HTTPS garantit l'intégrité, la confidentialité et l'authentification du serveur, et la sécurité des messages SOAP garantit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="a9748-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="a9748-133">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="a9748-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9748-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a9748-134">Child Elements</span></span>  
  
|<span data-ttu-id="a9748-135">Élément</span><span class="sxs-lookup"><span data-stu-id="a9748-135">Element</span></span>|<span data-ttu-id="a9748-136">Description</span><span class="sxs-lookup"><span data-stu-id="a9748-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="a9748-137">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="a9748-137">Defines the transport security settings.</span></span> <span data-ttu-id="a9748-138">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a9748-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="a9748-139">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="a9748-139">Defines the security settings for the message.</span></span> <span data-ttu-id="a9748-140">Cet élément correspond au type <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="a9748-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9748-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a9748-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a9748-142">Élément</span><span class="sxs-lookup"><span data-stu-id="a9748-142">Element</span></span>|<span data-ttu-id="a9748-143">Description</span><span class="sxs-lookup"><span data-stu-id="a9748-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="a9748-144">Liaison sécurisée pour les applications de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9748-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9748-145">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9748-145">Remarks</span></span>  
 <span data-ttu-id="a9748-146">La classe WSHttpBinding est conçue pour interagir avec les services qui implémentent les spécifications WS-\*.</span><span class="sxs-lookup"><span data-stu-id="a9748-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="a9748-147">La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9748-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9748-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9748-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="a9748-149">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="a9748-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a9748-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a9748-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a9748-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a9748-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a9748-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a9748-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
