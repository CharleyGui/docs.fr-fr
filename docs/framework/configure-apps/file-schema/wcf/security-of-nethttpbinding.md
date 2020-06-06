---
title: <security> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736479"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="031a9-102">\<security> de \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="031a9-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="031a9-103">Définit les fonctionnalités de sécurité de [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="031a9-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="031a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="031a9-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="031a9-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="031a9-105">Attributes and elements</span></span>

<span data-ttu-id="031a9-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="031a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="031a9-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="031a9-107">Attributes</span></span>

|<span data-ttu-id="031a9-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="031a9-108">Attribute</span></span>|<span data-ttu-id="031a9-109">Description</span><span class="sxs-lookup"><span data-stu-id="031a9-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="031a9-110">mode</span><span class="sxs-lookup"><span data-stu-id="031a9-110">mode</span></span>|<span data-ttu-id="031a9-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="031a9-111">Optional.</span></span> <span data-ttu-id="031a9-112">Spécifie le type de sécurité qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="031a9-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="031a9-113">Par défaut, il s’agit de `None`.</span><span class="sxs-lookup"><span data-stu-id="031a9-113">The default is `None`.</span></span> <span data-ttu-id="031a9-114">Cet attribut est de type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="031a9-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="031a9-115">attribut mode</span><span class="sxs-lookup"><span data-stu-id="031a9-115">mode attribute</span></span>

|<span data-ttu-id="031a9-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="031a9-116">Value</span></span>|<span data-ttu-id="031a9-117">Description</span><span class="sxs-lookup"><span data-stu-id="031a9-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="031a9-118">None</span><span class="sxs-lookup"><span data-stu-id="031a9-118">None</span></span>|<span data-ttu-id="031a9-119">-Les messages ne sont pas sécurisés lors du transfert.</span><span class="sxs-lookup"><span data-stu-id="031a9-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="031a9-120">Transport</span><span class="sxs-lookup"><span data-stu-id="031a9-120">Transport</span></span>|<span data-ttu-id="031a9-121">La sécurité est fournie à l'aide du transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="031a9-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="031a9-122">Les messages SOAP sont sécurisés à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="031a9-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="031a9-123">Le service est authentifié auprès du client à l'aide du certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="031a9-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="031a9-124">Le client est authentifié à l'aide du ClientCredentialType fourni.</span><span class="sxs-lookup"><span data-stu-id="031a9-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="031a9-125">Message</span><span class="sxs-lookup"><span data-stu-id="031a9-125">Message</span></span>|<span data-ttu-id="031a9-126">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="031a9-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="031a9-127">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="031a9-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="031a9-128">Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande.</span><span class="sxs-lookup"><span data-stu-id="031a9-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="031a9-129">Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="031a9-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="031a9-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="031a9-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="031a9-131">L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="031a9-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="031a9-132">L'authentification du client est fournie au moyen de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="031a9-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="031a9-133">Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.</span><span class="sxs-lookup"><span data-stu-id="031a9-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="031a9-134">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="031a9-134">TransportCredentialOnly</span></span>|<span data-ttu-id="031a9-135">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="031a9-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="031a9-136">Il fournit l'authentification du client basée sur http.</span><span class="sxs-lookup"><span data-stu-id="031a9-136">It provides http-based client authentication.</span></span> <span data-ttu-id="031a9-137">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="031a9-137">This mode should be used with caution.</span></span> <span data-ttu-id="031a9-138">Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="031a9-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="031a9-139">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="031a9-139">Child elements</span></span>

|<span data-ttu-id="031a9-140">Élément</span><span class="sxs-lookup"><span data-stu-id="031a9-140">Element</span></span>|<span data-ttu-id="031a9-141">Description</span><span class="sxs-lookup"><span data-stu-id="031a9-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="031a9-142">Définit les paramètres de sécurité de transport pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="031a9-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="031a9-143">Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="031a9-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="031a9-144">Définit les paramètres de sécurité de message pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="031a9-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="031a9-145">Cet élément correspond à <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="031a9-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="031a9-146">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="031a9-146">Parent elements</span></span>

|<span data-ttu-id="031a9-147">Élément</span><span class="sxs-lookup"><span data-stu-id="031a9-147">Element</span></span>|<span data-ttu-id="031a9-148">Description</span><span class="sxs-lookup"><span data-stu-id="031a9-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="031a9-149">binding</span><span class="sxs-lookup"><span data-stu-id="031a9-149">binding</span></span>|<span data-ttu-id="031a9-150">Élément de liaison de [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="031a9-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="031a9-151">Remarques</span><span class="sxs-lookup"><span data-stu-id="031a9-151">Remarks</span></span>

 <span data-ttu-id="031a9-152">Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié.</span><span class="sxs-lookup"><span data-stu-id="031a9-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="031a9-153">Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `netHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="031a9-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="031a9-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="031a9-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="031a9-155">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="031a9-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="031a9-156">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="031a9-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="031a9-157">Liaisons</span><span class="sxs-lookup"><span data-stu-id="031a9-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="031a9-158">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="031a9-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="031a9-159">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="031a9-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
