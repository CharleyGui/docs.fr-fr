---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 60e8758d653848176ca3f287e253bd7990e78470
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162047"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="7086f-102">\<transport> de \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="7086f-102">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="7086f-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="7086f-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="7086f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7086f-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="7086f-105">Type</span><span class="sxs-lookup"><span data-stu-id="7086f-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7086f-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7086f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7086f-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7086f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7086f-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="7086f-108">Attributes</span></span>  
  
|<span data-ttu-id="7086f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="7086f-109">Attribute</span></span>|<span data-ttu-id="7086f-110">Description</span><span class="sxs-lookup"><span data-stu-id="7086f-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="7086f-111">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="7086f-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="7086f-112">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7086f-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="7086f-113">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="7086f-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="7086f-114">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7086f-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="7086f-115">Domaine d’authentification correspondant à l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="7086f-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="7086f-116">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="7086f-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="7086f-117">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="7086f-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="7086f-118">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="7086f-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="7086f-119">Un utilisateur peut interroger le domaine d'authentification afin de déterminer les noms d'utilisateur et les mots de passe pouvant être utilisés.</span><span class="sxs-lookup"><span data-stu-id="7086f-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="7086f-120">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="7086f-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7086f-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="7086f-121">Value</span></span>|<span data-ttu-id="7086f-122">Description</span><span class="sxs-lookup"><span data-stu-id="7086f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7086f-123">None</span><span class="sxs-lookup"><span data-stu-id="7086f-123">None</span></span>|<span data-ttu-id="7086f-124">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="7086f-124">Security is disabled.</span></span>|  
|<span data-ttu-id="7086f-125">Basic</span><span class="sxs-lookup"><span data-stu-id="7086f-125">Basic</span></span>|<span data-ttu-id="7086f-126">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="7086f-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="7086f-127">Digest</span><span class="sxs-lookup"><span data-stu-id="7086f-127">Digest</span></span>|<span data-ttu-id="7086f-128">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="7086f-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="7086f-129">Ntlm</span><span class="sxs-lookup"><span data-stu-id="7086f-129">Ntlm</span></span>|<span data-ttu-id="7086f-130">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="7086f-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="7086f-131">Windows</span><span class="sxs-lookup"><span data-stu-id="7086f-131">Windows</span></span>|<span data-ttu-id="7086f-132">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="7086f-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="7086f-133">Certificat</span><span class="sxs-lookup"><span data-stu-id="7086f-133">Certificate</span></span>|<span data-ttu-id="7086f-134">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="7086f-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="7086f-135">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="7086f-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7086f-136">Valeur</span><span class="sxs-lookup"><span data-stu-id="7086f-136">Value</span></span>|<span data-ttu-id="7086f-137">Description</span><span class="sxs-lookup"><span data-stu-id="7086f-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7086f-138">None</span><span class="sxs-lookup"><span data-stu-id="7086f-138">None</span></span>|<span data-ttu-id="7086f-139">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="7086f-139">Security is disabled.</span></span>|  
|<span data-ttu-id="7086f-140">Basic</span><span class="sxs-lookup"><span data-stu-id="7086f-140">Basic</span></span>|<span data-ttu-id="7086f-141">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="7086f-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="7086f-142">Digest</span><span class="sxs-lookup"><span data-stu-id="7086f-142">Digest</span></span>|<span data-ttu-id="7086f-143">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="7086f-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="7086f-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="7086f-144">Ntlm</span></span>|<span data-ttu-id="7086f-145">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="7086f-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="7086f-146">Windows</span><span class="sxs-lookup"><span data-stu-id="7086f-146">Windows</span></span>|<span data-ttu-id="7086f-147">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="7086f-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="7086f-148">Certificat</span><span class="sxs-lookup"><span data-stu-id="7086f-148">Certificate</span></span>|<span data-ttu-id="7086f-149">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="7086f-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7086f-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7086f-150">Child Elements</span></span>  

 <span data-ttu-id="7086f-151">None</span><span class="sxs-lookup"><span data-stu-id="7086f-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7086f-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7086f-152">Parent Elements</span></span>  
  
|<span data-ttu-id="7086f-153">Élément</span><span class="sxs-lookup"><span data-stu-id="7086f-153">Element</span></span>|<span data-ttu-id="7086f-154">Description</span><span class="sxs-lookup"><span data-stu-id="7086f-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="7086f-155">Représente les fonctionnalités de sécurité de l' [\<ws2007HttpBinding>](ws2007httpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="7086f-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7086f-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7086f-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="7086f-157">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7086f-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7086f-158">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7086f-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7086f-159">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="7086f-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7086f-160">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7086f-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
