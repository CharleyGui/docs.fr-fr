---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 98cdaa86441f91552c7133d8e5694f88019a6dbf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399280"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="09e19-102">\<> de transport \<de WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="09e19-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="09e19-103">Définit les paramètres de sécurité au niveau du transport pour un point de terminaison de service configuré pour recevoir des demandes HTTP.</span><span class="sxs-lookup"><span data-stu-id="09e19-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="09e19-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="09e19-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09e19-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="09e19-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="09e19-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="09e19-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="09e19-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="09e19-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="09e19-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="09e19-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="09e19-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="09e19-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="09e19-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="09e19-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e19-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09e19-111">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="09e19-112">Type</span><span class="sxs-lookup"><span data-stu-id="09e19-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09e19-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="09e19-113">Attributes and Elements</span></span>  
 <span data-ttu-id="09e19-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="09e19-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09e19-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="09e19-115">Attributes</span></span>  
  
|<span data-ttu-id="09e19-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="09e19-116">Attribute</span></span>|<span data-ttu-id="09e19-117">Description</span><span class="sxs-lookup"><span data-stu-id="09e19-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="09e19-118">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="09e19-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="09e19-119">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="09e19-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="09e19-120">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="09e19-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="09e19-121">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="09e19-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="09e19-122">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="09e19-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="09e19-123">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="09e19-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="09e19-124">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="09e19-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="09e19-125">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="09e19-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="09e19-126">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="09e19-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="09e19-127">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="09e19-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="09e19-128">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="09e19-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="09e19-129">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="09e19-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="09e19-130">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="09e19-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="09e19-131">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="09e19-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="09e19-132">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="09e19-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="09e19-133">`Value`</span><span class="sxs-lookup"><span data-stu-id="09e19-133">Value</span></span>|<span data-ttu-id="09e19-134">Description</span><span class="sxs-lookup"><span data-stu-id="09e19-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="09e19-135">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="09e19-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="09e19-136">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="09e19-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="09e19-137">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="09e19-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="09e19-138">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="09e19-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="09e19-139">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="09e19-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="09e19-140">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="09e19-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="09e19-141">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="09e19-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="09e19-142">`Value`</span><span class="sxs-lookup"><span data-stu-id="09e19-142">Value</span></span>|<span data-ttu-id="09e19-143">Description</span><span class="sxs-lookup"><span data-stu-id="09e19-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="09e19-144">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="09e19-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="09e19-145">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="09e19-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="09e19-146">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="09e19-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="09e19-147">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="09e19-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="09e19-148">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="09e19-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09e19-149">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="09e19-149">Child Elements</span></span>  
 <span data-ttu-id="09e19-150">Aucun.</span><span class="sxs-lookup"><span data-stu-id="09e19-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09e19-151">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="09e19-151">Parent Elements</span></span>  
  
|<span data-ttu-id="09e19-152">Élément</span><span class="sxs-lookup"><span data-stu-id="09e19-152">Element</span></span>|<span data-ttu-id="09e19-153">Description</span><span class="sxs-lookup"><span data-stu-id="09e19-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09e19-154">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="09e19-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="09e19-155">Représente les fonctionnalités de sécurité de l' [ \<élément WSHttpBinding >](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="09e19-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09e19-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09e19-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="09e19-157">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="09e19-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="09e19-158">Liaisons</span><span class="sxs-lookup"><span data-stu-id="09e19-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="09e19-159">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="09e19-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="09e19-160">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="09e19-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="09e19-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="09e19-161">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="09e19-162">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="09e19-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
