---
title: <security> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 00a933892376c2dc9771752beaf76d4994554968
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399896"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="6aaef-102">\<> de sécurité \<de BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6aaef-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="6aaef-103">Définit les fonctionnalités de sécurité du [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6aaef-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="6aaef-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6aaef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6aaef-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6aaef-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6aaef-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6aaef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6aaef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> basicHttpBinding**](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6aaef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="6aaef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="6aaef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6aaef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de sécurité**</span><span class="sxs-lookup"><span data-stu-id="6aaef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aaef-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6aaef-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6aaef-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6aaef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6aaef-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6aaef-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6aaef-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="6aaef-113">Attributes</span></span>  
  
|<span data-ttu-id="6aaef-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="6aaef-114">Attribute</span></span>|<span data-ttu-id="6aaef-115">Description</span><span class="sxs-lookup"><span data-stu-id="6aaef-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6aaef-116">mode</span><span class="sxs-lookup"><span data-stu-id="6aaef-116">mode</span></span>|<span data-ttu-id="6aaef-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aaef-117">Optional.</span></span> <span data-ttu-id="6aaef-118">Spécifie le type de sécurité qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="6aaef-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="6aaef-119">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="6aaef-119">The default is `None`.</span></span> <span data-ttu-id="6aaef-120">Cet attribut est de type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6aaef-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6aaef-121">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="6aaef-121">mode Attribute</span></span>  
  
|<span data-ttu-id="6aaef-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="6aaef-122">Value</span></span>|<span data-ttu-id="6aaef-123">Description</span><span class="sxs-lookup"><span data-stu-id="6aaef-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6aaef-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="6aaef-124">None</span></span>|<span data-ttu-id="6aaef-125">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="6aaef-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="6aaef-126">Transport</span><span class="sxs-lookup"><span data-stu-id="6aaef-126">Transport</span></span>|<span data-ttu-id="6aaef-127">La sécurité est fournie à l'aide du transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6aaef-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="6aaef-128">Les messages SOAP sont sécurisés par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6aaef-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="6aaef-129">Le service est authentifié auprès du client à l'aide du certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="6aaef-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="6aaef-130">Le client est authentifié à l'aide du ClientCredentialType fourni.</span><span class="sxs-lookup"><span data-stu-id="6aaef-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="6aaef-131">Consultez le [ \<> de transport](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6aaef-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="6aaef-132">Message</span><span class="sxs-lookup"><span data-stu-id="6aaef-132">Message</span></span>|<span data-ttu-id="6aaef-133">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="6aaef-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6aaef-134">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="6aaef-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6aaef-135">Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande.</span><span class="sxs-lookup"><span data-stu-id="6aaef-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="6aaef-136">Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="6aaef-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="6aaef-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6aaef-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="6aaef-138">L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="6aaef-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="6aaef-139">L'authentification du client est fournie au moyen de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="6aaef-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="6aaef-140">Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.</span><span class="sxs-lookup"><span data-stu-id="6aaef-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="6aaef-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="6aaef-141">TransportCredentialOnly</span></span>|<span data-ttu-id="6aaef-142">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="6aaef-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6aaef-143">Il fournit l'authentification du client basée sur http.</span><span class="sxs-lookup"><span data-stu-id="6aaef-143">It provides http-based client authentication.</span></span> <span data-ttu-id="6aaef-144">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="6aaef-144">This mode should be used with caution.</span></span> <span data-ttu-id="6aaef-145">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="6aaef-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6aaef-146">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6aaef-146">Child Elements</span></span>  
  
|<span data-ttu-id="6aaef-147">Élément</span><span class="sxs-lookup"><span data-stu-id="6aaef-147">Element</span></span>|<span data-ttu-id="6aaef-148">Description</span><span class="sxs-lookup"><span data-stu-id="6aaef-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aaef-149">\<transport></span><span class="sxs-lookup"><span data-stu-id="6aaef-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="6aaef-150">Définit les paramètres de sécurité de transport pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="6aaef-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="6aaef-151">Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="6aaef-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="6aaef-152">\<message></span><span class="sxs-lookup"><span data-stu-id="6aaef-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="6aaef-153">Définit les paramètres de sécurité de message pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="6aaef-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="6aaef-154">Cet élément correspond à <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="6aaef-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6aaef-155">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6aaef-155">Parent Elements</span></span>  
  
|<span data-ttu-id="6aaef-156">Élément</span><span class="sxs-lookup"><span data-stu-id="6aaef-156">Element</span></span>|<span data-ttu-id="6aaef-157">Description</span><span class="sxs-lookup"><span data-stu-id="6aaef-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6aaef-158">liaison</span><span class="sxs-lookup"><span data-stu-id="6aaef-158">binding</span></span>|<span data-ttu-id="6aaef-159">Élément de liaison de l' [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6aaef-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6aaef-160">Notes</span><span class="sxs-lookup"><span data-stu-id="6aaef-160">Remarks</span></span>  
 <span data-ttu-id="6aaef-161">Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié.</span><span class="sxs-lookup"><span data-stu-id="6aaef-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="6aaef-162">Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="6aaef-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aaef-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aaef-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6aaef-164">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="6aaef-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6aaef-165">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="6aaef-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6aaef-166">Liaisons</span><span class="sxs-lookup"><span data-stu-id="6aaef-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6aaef-167">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="6aaef-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6aaef-168">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="6aaef-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6aaef-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="6aaef-169">\<binding></span></span>](../../../misc/binding.md)
