---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: b9efc732832a8862373b14f657796a59fb52c1a1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162112"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="dddd4-102">\<transport> de \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="dddd4-102">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="dddd4-103">Définit les paramètres de sécurité au niveau du transport pour un point de terminaison de service configuré pour recevoir des demandes HTTP.</span><span class="sxs-lookup"><span data-stu-id="dddd4-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="dddd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dddd4-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="dddd4-105">Type</span><span class="sxs-lookup"><span data-stu-id="dddd4-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dddd4-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dddd4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dddd4-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dddd4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dddd4-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="dddd4-108">Attributes</span></span>  
  
|<span data-ttu-id="dddd4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="dddd4-109">Attribute</span></span>|<span data-ttu-id="dddd4-110">Description</span><span class="sxs-lookup"><span data-stu-id="dddd4-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="dddd4-111">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="dddd4-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="dddd4-112">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="dddd4-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="dddd4-113">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="dddd4-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="dddd4-114">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="dddd4-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="dddd4-115">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="dddd4-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="dddd4-116">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="dddd4-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="dddd4-117">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="dddd4-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="dddd4-118">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="dddd4-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="dddd4-119">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="dddd4-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="dddd4-120">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="dddd4-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="dddd4-121">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="dddd4-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="dddd4-122">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="dddd4-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="dddd4-123">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="dddd4-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="dddd4-124">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="dddd4-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="dddd4-125">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="dddd4-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="dddd4-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="dddd4-126">Value</span></span>|<span data-ttu-id="dddd4-127">Description</span><span class="sxs-lookup"><span data-stu-id="dddd4-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="dddd4-128">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="dddd4-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="dddd4-129">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="dddd4-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="dddd4-130">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="dddd4-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="dddd4-131">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="dddd4-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="dddd4-132">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="dddd4-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="dddd4-133">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="dddd4-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="dddd4-134">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="dddd4-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="dddd4-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="dddd4-135">Value</span></span>|<span data-ttu-id="dddd4-136">Description</span><span class="sxs-lookup"><span data-stu-id="dddd4-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="dddd4-137">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="dddd4-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="dddd4-138">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="dddd4-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="dddd4-139">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="dddd4-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="dddd4-140">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="dddd4-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="dddd4-141">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="dddd4-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dddd4-142">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dddd4-142">Child Elements</span></span>  

 <span data-ttu-id="dddd4-143">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dddd4-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dddd4-144">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dddd4-144">Parent Elements</span></span>  
  
|<span data-ttu-id="dddd4-145">Élément</span><span class="sxs-lookup"><span data-stu-id="dddd4-145">Element</span></span>|<span data-ttu-id="dddd4-146">Description</span><span class="sxs-lookup"><span data-stu-id="dddd4-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="dddd4-147">Représente les fonctionnalités de sécurité de l' [\<wsHttpBinding>](wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="dddd4-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dddd4-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dddd4-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="dddd4-149">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="dddd4-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dddd4-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="dddd4-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dddd4-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="dddd4-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dddd4-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="dddd4-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="dddd4-153">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="dddd4-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
