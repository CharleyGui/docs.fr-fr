---
title: <security> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 6144e5448526d7f2a7c89693f70f71a7f26c4a22
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183661"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="d772d-102">\<security> de \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d772d-102">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="d772d-103">Définit les fonctionnalités de sécurité de [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d772d-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="d772d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d772d-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d772d-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d772d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d772d-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d772d-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d772d-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d772d-107">Attributes</span></span>  
  
|<span data-ttu-id="d772d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d772d-108">Attribute</span></span>|<span data-ttu-id="d772d-109">Description</span><span class="sxs-lookup"><span data-stu-id="d772d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d772d-110">mode</span><span class="sxs-lookup"><span data-stu-id="d772d-110">mode</span></span>|<span data-ttu-id="d772d-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="d772d-111">Optional.</span></span> <span data-ttu-id="d772d-112">Spécifie le type de sécurité qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d772d-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="d772d-113">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="d772d-113">The default is `None`.</span></span> <span data-ttu-id="d772d-114">Cet attribut est de type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d772d-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d772d-115">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="d772d-115">mode Attribute</span></span>  
  
|<span data-ttu-id="d772d-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="d772d-116">Value</span></span>|<span data-ttu-id="d772d-117">Description</span><span class="sxs-lookup"><span data-stu-id="d772d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d772d-118">None</span><span class="sxs-lookup"><span data-stu-id="d772d-118">None</span></span>|<span data-ttu-id="d772d-119">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="d772d-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d772d-120">Transport</span><span class="sxs-lookup"><span data-stu-id="d772d-120">Transport</span></span>|<span data-ttu-id="d772d-121">La sécurité est fournie à l'aide du transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d772d-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="d772d-122">Les messages SOAP sont sécurisés à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d772d-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="d772d-123">Le service est authentifié auprès du client à l'aide du certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="d772d-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="d772d-124">Le client est authentifié à l'aide du ClientCredentialType fourni.</span><span class="sxs-lookup"><span data-stu-id="d772d-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="d772d-125">Consultez le [\<transport>](transport-of-basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d772d-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="d772d-126">Message</span><span class="sxs-lookup"><span data-stu-id="d772d-126">Message</span></span>|<span data-ttu-id="d772d-127">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="d772d-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d772d-128">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="d772d-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d772d-129">Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande.</span><span class="sxs-lookup"><span data-stu-id="d772d-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="d772d-130">Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="d772d-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="d772d-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d772d-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="d772d-132">L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="d772d-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="d772d-133">L'authentification du client est fournie au moyen de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="d772d-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="d772d-134">Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.</span><span class="sxs-lookup"><span data-stu-id="d772d-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="d772d-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="d772d-135">TransportCredentialOnly</span></span>|<span data-ttu-id="d772d-136">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="d772d-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="d772d-137">Il fournit l'authentification du client basée sur http.</span><span class="sxs-lookup"><span data-stu-id="d772d-137">It provides http-based client authentication.</span></span> <span data-ttu-id="d772d-138">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="d772d-138">This mode should be used with caution.</span></span> <span data-ttu-id="d772d-139">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="d772d-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d772d-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d772d-140">Child Elements</span></span>  
  
|<span data-ttu-id="d772d-141">Élément</span><span class="sxs-lookup"><span data-stu-id="d772d-141">Element</span></span>|<span data-ttu-id="d772d-142">Description</span><span class="sxs-lookup"><span data-stu-id="d772d-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="d772d-143">Définit les paramètres de sécurité de transport pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="d772d-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="d772d-144">Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="d772d-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="d772d-145">Définit les paramètres de sécurité de message pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="d772d-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="d772d-146">Cet élément correspond à <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="d772d-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d772d-147">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d772d-147">Parent Elements</span></span>  
  
|<span data-ttu-id="d772d-148">Élément</span><span class="sxs-lookup"><span data-stu-id="d772d-148">Element</span></span>|<span data-ttu-id="d772d-149">Description</span><span class="sxs-lookup"><span data-stu-id="d772d-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d772d-150">binding</span><span class="sxs-lookup"><span data-stu-id="d772d-150">binding</span></span>|<span data-ttu-id="d772d-151">Élément de liaison de [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d772d-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d772d-152">Notes</span><span class="sxs-lookup"><span data-stu-id="d772d-152">Remarks</span></span>  

 <span data-ttu-id="d772d-153">Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié.</span><span class="sxs-lookup"><span data-stu-id="d772d-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="d772d-154">Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d772d-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d772d-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d772d-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="d772d-156">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d772d-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d772d-157">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="d772d-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d772d-158">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d772d-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d772d-159">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d772d-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d772d-160">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d772d-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
