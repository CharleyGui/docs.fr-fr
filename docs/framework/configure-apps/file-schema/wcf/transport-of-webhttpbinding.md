---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732792"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="e7afb-102">\<transport> de \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e7afb-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="e7afb-103">Définit les paramètres de sécurité au niveau du transport pour un point de terminaison de service configuré pour recevoir des demandes HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7afb-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="e7afb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7afb-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="e7afb-105">Type</span><span class="sxs-lookup"><span data-stu-id="e7afb-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7afb-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7afb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e7afb-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7afb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7afb-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7afb-108">Attributes</span></span>  
  
|<span data-ttu-id="e7afb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7afb-109">Attribute</span></span>|<span data-ttu-id="e7afb-110">Description</span><span class="sxs-lookup"><span data-stu-id="e7afb-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="e7afb-111">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="e7afb-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="e7afb-112">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e7afb-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="e7afb-113">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="e7afb-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="e7afb-114">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e7afb-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="e7afb-115">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="e7afb-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="e7afb-116">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="e7afb-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e7afb-117">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="e7afb-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="e7afb-118">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="e7afb-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="e7afb-119">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="e7afb-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="e7afb-120">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="e7afb-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e7afb-121">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="e7afb-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e7afb-122">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="e7afb-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e7afb-123">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="e7afb-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e7afb-124">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="e7afb-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e7afb-125">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e7afb-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e7afb-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="e7afb-126">Value</span></span>|<span data-ttu-id="e7afb-127">Description</span><span class="sxs-lookup"><span data-stu-id="e7afb-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="e7afb-128">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="e7afb-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="e7afb-129">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="e7afb-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="e7afb-130">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="e7afb-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="e7afb-131">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="e7afb-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="e7afb-132">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="e7afb-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="e7afb-133">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="e7afb-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e7afb-134">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="e7afb-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e7afb-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="e7afb-135">Value</span></span>|<span data-ttu-id="e7afb-136">Description</span><span class="sxs-lookup"><span data-stu-id="e7afb-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="e7afb-137">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="e7afb-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="e7afb-138">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="e7afb-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="e7afb-139">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="e7afb-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="e7afb-140">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="e7afb-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="e7afb-141">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="e7afb-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7afb-142">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7afb-142">Child Elements</span></span>  
 <span data-ttu-id="e7afb-143">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7afb-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7afb-144">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7afb-144">Parent Elements</span></span>  
  
|<span data-ttu-id="e7afb-145">Élément</span><span class="sxs-lookup"><span data-stu-id="e7afb-145">Element</span></span>|<span data-ttu-id="e7afb-146">Description</span><span class="sxs-lookup"><span data-stu-id="e7afb-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="e7afb-147">Représente les fonctionnalités de sécurité de l' [\<wsHttpBinding>](wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="e7afb-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7afb-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7afb-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="e7afb-149">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="e7afb-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e7afb-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e7afb-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e7afb-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e7afb-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e7afb-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e7afb-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="e7afb-153">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="e7afb-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
