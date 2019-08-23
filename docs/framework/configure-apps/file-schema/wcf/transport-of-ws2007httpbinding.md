---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911987"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="3ebc9-102">\<> de transport \<de WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3ebc9-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="3ebc9-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="3ebc9-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ebc9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3ebc9-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3ebc9-105">\<bindings></span></span>  
<span data-ttu-id="3ebc9-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="3ebc9-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="3ebc9-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="3ebc9-107">\<binding></span></span>  
<span data-ttu-id="3ebc9-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="3ebc9-108">\<security></span></span>  
<span data-ttu-id="3ebc9-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="3ebc9-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ebc9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ebc9-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="3ebc9-111">Type</span><span class="sxs-lookup"><span data-stu-id="3ebc9-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ebc9-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3ebc9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3ebc9-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ebc9-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="3ebc9-114">Attributes</span></span>  
  
|<span data-ttu-id="3ebc9-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="3ebc9-115">Attribute</span></span>|<span data-ttu-id="3ebc9-116">Description</span><span class="sxs-lookup"><span data-stu-id="3ebc9-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="3ebc9-117">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="3ebc9-118">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="3ebc9-119">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="3ebc9-120">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="3ebc9-121">Domaine d’authentification correspondant à l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="3ebc9-122">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="3ebc9-123">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="3ebc9-124">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="3ebc9-125">Un utilisateur peut interroger le domaine d'authentification afin de déterminer les noms d'utilisateur et les mots de passe pouvant être utilisés.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3ebc9-126">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3ebc9-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3ebc9-127">Valeur</span><span class="sxs-lookup"><span data-stu-id="3ebc9-127">Value</span></span>|<span data-ttu-id="3ebc9-128">Description</span><span class="sxs-lookup"><span data-stu-id="3ebc9-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ebc9-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="3ebc9-129">None</span></span>|<span data-ttu-id="3ebc9-130">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-130">Security is disabled.</span></span>|  
|<span data-ttu-id="3ebc9-131">De base</span><span class="sxs-lookup"><span data-stu-id="3ebc9-131">Basic</span></span>|<span data-ttu-id="3ebc9-132">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="3ebc9-133">Digest</span><span class="sxs-lookup"><span data-stu-id="3ebc9-133">Digest</span></span>|<span data-ttu-id="3ebc9-134">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="3ebc9-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="3ebc9-135">Ntlm</span></span>|<span data-ttu-id="3ebc9-136">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="3ebc9-137">Windows</span><span class="sxs-lookup"><span data-stu-id="3ebc9-137">Windows</span></span>|<span data-ttu-id="3ebc9-138">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="3ebc9-139">Certificat</span><span class="sxs-lookup"><span data-stu-id="3ebc9-139">Certificate</span></span>|<span data-ttu-id="3ebc9-140">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="3ebc9-141">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="3ebc9-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3ebc9-142">`Value`</span><span class="sxs-lookup"><span data-stu-id="3ebc9-142">Value</span></span>|<span data-ttu-id="3ebc9-143">Description</span><span class="sxs-lookup"><span data-stu-id="3ebc9-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ebc9-144">Aucun</span><span class="sxs-lookup"><span data-stu-id="3ebc9-144">None</span></span>|<span data-ttu-id="3ebc9-145">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-145">Security is disabled.</span></span>|  
|<span data-ttu-id="3ebc9-146">De base</span><span class="sxs-lookup"><span data-stu-id="3ebc9-146">Basic</span></span>|<span data-ttu-id="3ebc9-147">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="3ebc9-148">Digest</span><span class="sxs-lookup"><span data-stu-id="3ebc9-148">Digest</span></span>|<span data-ttu-id="3ebc9-149">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="3ebc9-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="3ebc9-150">Ntlm</span></span>|<span data-ttu-id="3ebc9-151">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="3ebc9-152">Windows</span><span class="sxs-lookup"><span data-stu-id="3ebc9-152">Windows</span></span>|<span data-ttu-id="3ebc9-153">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="3ebc9-154">Certificat</span><span class="sxs-lookup"><span data-stu-id="3ebc9-154">Certificate</span></span>|<span data-ttu-id="3ebc9-155">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="3ebc9-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ebc9-156">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3ebc9-156">Child Elements</span></span>  
 <span data-ttu-id="3ebc9-157">Aucun</span><span class="sxs-lookup"><span data-stu-id="3ebc9-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ebc9-158">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3ebc9-158">Parent Elements</span></span>  
  
|<span data-ttu-id="3ebc9-159">Élément</span><span class="sxs-lookup"><span data-stu-id="3ebc9-159">Element</span></span>|<span data-ttu-id="3ebc9-160">Description</span><span class="sxs-lookup"><span data-stu-id="3ebc9-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ebc9-161">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="3ebc9-161">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="3ebc9-162">Représente les fonctionnalités de sécurité de l' [ \<élément WS2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3ebc9-162">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ebc9-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ebc9-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="3ebc9-164">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3ebc9-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3ebc9-165">Liaisons</span><span class="sxs-lookup"><span data-stu-id="3ebc9-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3ebc9-166">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="3ebc9-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3ebc9-167">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3ebc9-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3ebc9-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="3ebc9-168">\<binding></span></span>](../../../misc/binding.md)
