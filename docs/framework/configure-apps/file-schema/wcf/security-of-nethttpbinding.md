---
title: <security> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736479"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="23885-102">\<> de sécurité de \<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="23885-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="23885-103">Définit les fonctionnalités de sécurité du [\<NetHttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="23885-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="23885-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23885-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23885-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="23885-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="23885-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="23885-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="23885-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetHttpBinding**](nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="23885-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="23885-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="23885-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="23885-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="23885-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="23885-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23885-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23885-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="23885-111">Attributes and elements</span></span>

<span data-ttu-id="23885-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="23885-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="23885-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="23885-113">Attributes</span></span>

|<span data-ttu-id="23885-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="23885-114">Attribute</span></span>|<span data-ttu-id="23885-115">Description</span><span class="sxs-lookup"><span data-stu-id="23885-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="23885-116">mode</span><span class="sxs-lookup"><span data-stu-id="23885-116">mode</span></span>|<span data-ttu-id="23885-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="23885-117">Optional.</span></span> <span data-ttu-id="23885-118">Spécifie le type de sécurité qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="23885-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="23885-119">La valeur par défaut est `None`,</span><span class="sxs-lookup"><span data-stu-id="23885-119">The default is `None`.</span></span> <span data-ttu-id="23885-120">Cet attribut est de type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="23885-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="23885-121">attribut mode</span><span class="sxs-lookup"><span data-stu-id="23885-121">mode attribute</span></span>

|<span data-ttu-id="23885-122">valeur</span><span class="sxs-lookup"><span data-stu-id="23885-122">Value</span></span>|<span data-ttu-id="23885-123">Description</span><span class="sxs-lookup"><span data-stu-id="23885-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="23885-124">aucune.</span><span class="sxs-lookup"><span data-stu-id="23885-124">None</span></span>|<span data-ttu-id="23885-125">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="23885-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="23885-126">Transport</span><span class="sxs-lookup"><span data-stu-id="23885-126">Transport</span></span>|<span data-ttu-id="23885-127">La sécurité est fournie à l'aide du transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="23885-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="23885-128">Les messages SOAP sont sécurisés par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="23885-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="23885-129">Le service est authentifié auprès du client à l'aide du certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="23885-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="23885-130">Le client est authentifié à l'aide du ClientCredentialType fourni.</span><span class="sxs-lookup"><span data-stu-id="23885-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="23885-131">Message</span><span class="sxs-lookup"><span data-stu-id="23885-131">Message</span></span>|<span data-ttu-id="23885-132">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="23885-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="23885-133">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="23885-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="23885-134">Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande.</span><span class="sxs-lookup"><span data-stu-id="23885-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="23885-135">Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="23885-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="23885-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="23885-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="23885-137">L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="23885-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="23885-138">L'authentification du client est fournie au moyen de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="23885-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="23885-139">Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.</span><span class="sxs-lookup"><span data-stu-id="23885-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="23885-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="23885-140">TransportCredentialOnly</span></span>|<span data-ttu-id="23885-141">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="23885-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="23885-142">Il fournit l'authentification du client basée sur http.</span><span class="sxs-lookup"><span data-stu-id="23885-142">It provides http-based client authentication.</span></span> <span data-ttu-id="23885-143">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="23885-143">This mode should be used with caution.</span></span> <span data-ttu-id="23885-144">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="23885-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="23885-145">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="23885-145">Child elements</span></span>

|<span data-ttu-id="23885-146">Élément</span><span class="sxs-lookup"><span data-stu-id="23885-146">Element</span></span>|<span data-ttu-id="23885-147">Description</span><span class="sxs-lookup"><span data-stu-id="23885-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23885-148">> de transport \<</span><span class="sxs-lookup"><span data-stu-id="23885-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="23885-149">Définit les paramètres de sécurité de transport pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="23885-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="23885-150">Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="23885-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="23885-151">message de \<</span><span class="sxs-lookup"><span data-stu-id="23885-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="23885-152">Définit les paramètres de sécurité de message pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="23885-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="23885-153">Cet élément correspond à <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="23885-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="23885-154">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="23885-154">Parent elements</span></span>

|<span data-ttu-id="23885-155">Élément</span><span class="sxs-lookup"><span data-stu-id="23885-155">Element</span></span>|<span data-ttu-id="23885-156">Description</span><span class="sxs-lookup"><span data-stu-id="23885-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="23885-157">liaison</span><span class="sxs-lookup"><span data-stu-id="23885-157">binding</span></span>|<span data-ttu-id="23885-158">Élément de liaison de la [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="23885-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="23885-159">Notes</span><span class="sxs-lookup"><span data-stu-id="23885-159">Remarks</span></span>

 <span data-ttu-id="23885-160">Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié.</span><span class="sxs-lookup"><span data-stu-id="23885-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="23885-161">Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `netHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="23885-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="23885-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23885-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="23885-163">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="23885-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="23885-164">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="23885-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="23885-165">Liaisons</span><span class="sxs-lookup"><span data-stu-id="23885-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="23885-166">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="23885-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="23885-167">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="23885-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="23885-168">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="23885-168">\<binding></span></span>](bindings.md)
