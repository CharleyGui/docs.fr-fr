---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732738"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="cdd66-102">\<transport> de \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cdd66-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="cdd66-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="cdd66-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="cdd66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdd66-104">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="cdd66-105">Type</span><span class="sxs-lookup"><span data-stu-id="cdd66-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="cdd66-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cdd66-106">Attributes and Elements</span></span>

<span data-ttu-id="cdd66-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cdd66-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cdd66-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="cdd66-108">Attributes</span></span>

|<span data-ttu-id="cdd66-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="cdd66-109">Attribute</span></span>|<span data-ttu-id="cdd66-110">Description</span><span class="sxs-lookup"><span data-stu-id="cdd66-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="cdd66-111">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="cdd66-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="cdd66-112">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="cdd66-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="cdd66-113">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="cdd66-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="cdd66-114">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="cdd66-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="cdd66-115">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="cdd66-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="cdd66-116">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="cdd66-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="cdd66-117">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="cdd66-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="cdd66-118">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="cdd66-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="cdd66-119">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="cdd66-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="cdd66-120">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="cdd66-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="cdd66-121">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="cdd66-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="cdd66-122">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="cdd66-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="cdd66-123">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="cdd66-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="cdd66-124">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="cdd66-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="cdd66-125">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="cdd66-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="cdd66-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="cdd66-126">Value</span></span>|<span data-ttu-id="cdd66-127">Description</span><span class="sxs-lookup"><span data-stu-id="cdd66-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="cdd66-128">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="cdd66-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="cdd66-129">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="cdd66-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="cdd66-130">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="cdd66-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="cdd66-131">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd66-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="cdd66-132">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd66-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="cdd66-133">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="cdd66-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="cdd66-134">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="cdd66-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="cdd66-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="cdd66-135">Value</span></span>|<span data-ttu-id="cdd66-136">Description</span><span class="sxs-lookup"><span data-stu-id="cdd66-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="cdd66-137">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="cdd66-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="cdd66-138">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="cdd66-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="cdd66-139">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="cdd66-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="cdd66-140">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd66-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="cdd66-141">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd66-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="cdd66-142">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="cdd66-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cdd66-143">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cdd66-143">Child Elements</span></span>

<span data-ttu-id="cdd66-144">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cdd66-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cdd66-145">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cdd66-145">Parent Elements</span></span>

|<span data-ttu-id="cdd66-146">Élément</span><span class="sxs-lookup"><span data-stu-id="cdd66-146">Element</span></span>|<span data-ttu-id="cdd66-147">Description</span><span class="sxs-lookup"><span data-stu-id="cdd66-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="cdd66-148">Représente les fonctionnalités de sécurité de [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="cdd66-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="cdd66-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdd66-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="cdd66-150">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="cdd66-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cdd66-151">Liaisons</span><span class="sxs-lookup"><span data-stu-id="cdd66-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cdd66-152">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="cdd66-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cdd66-153">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="cdd66-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
