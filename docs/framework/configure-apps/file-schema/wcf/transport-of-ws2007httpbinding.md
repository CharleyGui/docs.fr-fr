---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 4ea60ccaba58bc0b3fa8f2263295bf1413d25e89
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399268"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="f4c63-102">\<> de transport \<de WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f4c63-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="f4c63-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4c63-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="f4c63-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4c63-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4c63-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f4c63-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f4c63-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f4c63-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f4c63-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f4c63-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="f4c63-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="f4c63-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f4c63-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f4c63-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="f4c63-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="f4c63-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c63-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4c63-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="f4c63-112">Type</span><span class="sxs-lookup"><span data-stu-id="f4c63-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4c63-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f4c63-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f4c63-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f4c63-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4c63-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4c63-115">Attributes</span></span>  
  
|<span data-ttu-id="f4c63-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="f4c63-116">Attribute</span></span>|<span data-ttu-id="f4c63-117">Description</span><span class="sxs-lookup"><span data-stu-id="f4c63-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="f4c63-118">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="f4c63-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="f4c63-119">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f4c63-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="f4c63-120">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="f4c63-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="f4c63-121">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f4c63-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="f4c63-122">Domaine d’authentification correspondant à l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="f4c63-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="f4c63-123">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="f4c63-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="f4c63-124">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="f4c63-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="f4c63-125">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="f4c63-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="f4c63-126">Un utilisateur peut interroger le domaine d'authentification afin de déterminer les noms d'utilisateur et les mots de passe pouvant être utilisés.</span><span class="sxs-lookup"><span data-stu-id="f4c63-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f4c63-127">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f4c63-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f4c63-128">Valeur</span><span class="sxs-lookup"><span data-stu-id="f4c63-128">Value</span></span>|<span data-ttu-id="f4c63-129">Description</span><span class="sxs-lookup"><span data-stu-id="f4c63-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4c63-130">Aucun</span><span class="sxs-lookup"><span data-stu-id="f4c63-130">None</span></span>|<span data-ttu-id="f4c63-131">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="f4c63-131">Security is disabled.</span></span>|  
|<span data-ttu-id="f4c63-132">De base</span><span class="sxs-lookup"><span data-stu-id="f4c63-132">Basic</span></span>|<span data-ttu-id="f4c63-133">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="f4c63-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="f4c63-134">Digest</span><span class="sxs-lookup"><span data-stu-id="f4c63-134">Digest</span></span>|<span data-ttu-id="f4c63-135">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="f4c63-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="f4c63-136">Ntlm</span><span class="sxs-lookup"><span data-stu-id="f4c63-136">Ntlm</span></span>|<span data-ttu-id="f4c63-137">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="f4c63-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="f4c63-138">Windows</span><span class="sxs-lookup"><span data-stu-id="f4c63-138">Windows</span></span>|<span data-ttu-id="f4c63-139">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="f4c63-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="f4c63-140">Certificat</span><span class="sxs-lookup"><span data-stu-id="f4c63-140">Certificate</span></span>|<span data-ttu-id="f4c63-141">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="f4c63-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="f4c63-142">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="f4c63-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f4c63-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="f4c63-143">Value</span></span>|<span data-ttu-id="f4c63-144">Description</span><span class="sxs-lookup"><span data-stu-id="f4c63-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4c63-145">Aucun</span><span class="sxs-lookup"><span data-stu-id="f4c63-145">None</span></span>|<span data-ttu-id="f4c63-146">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="f4c63-146">Security is disabled.</span></span>|  
|<span data-ttu-id="f4c63-147">De base</span><span class="sxs-lookup"><span data-stu-id="f4c63-147">Basic</span></span>|<span data-ttu-id="f4c63-148">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="f4c63-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="f4c63-149">Digest</span><span class="sxs-lookup"><span data-stu-id="f4c63-149">Digest</span></span>|<span data-ttu-id="f4c63-150">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="f4c63-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="f4c63-151">Ntlm</span><span class="sxs-lookup"><span data-stu-id="f4c63-151">Ntlm</span></span>|<span data-ttu-id="f4c63-152">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="f4c63-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="f4c63-153">Windows</span><span class="sxs-lookup"><span data-stu-id="f4c63-153">Windows</span></span>|<span data-ttu-id="f4c63-154">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="f4c63-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="f4c63-155">Certificat</span><span class="sxs-lookup"><span data-stu-id="f4c63-155">Certificate</span></span>|<span data-ttu-id="f4c63-156">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="f4c63-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4c63-157">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4c63-157">Child Elements</span></span>  
 <span data-ttu-id="f4c63-158">Aucun</span><span class="sxs-lookup"><span data-stu-id="f4c63-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4c63-159">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4c63-159">Parent Elements</span></span>  
  
|<span data-ttu-id="f4c63-160">Élément</span><span class="sxs-lookup"><span data-stu-id="f4c63-160">Element</span></span>|<span data-ttu-id="f4c63-161">Description</span><span class="sxs-lookup"><span data-stu-id="f4c63-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4c63-162">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="f4c63-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="f4c63-163">Représente les fonctionnalités de sécurité de l' [ \<élément WS2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f4c63-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4c63-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4c63-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="f4c63-165">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f4c63-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f4c63-166">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f4c63-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f4c63-167">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f4c63-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f4c63-168">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f4c63-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f4c63-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="f4c63-169">\<binding></span></span>](../../../misc/binding.md)
