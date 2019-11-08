---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732738"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="da82d-102">\<> de transport de \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="da82d-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="da82d-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="da82d-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="da82d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="da82d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="da82d-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="da82d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="da82d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="da82d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="da82d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="da82d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="da82d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="da82d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="da82d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-wshttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="da82d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="da82d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="da82d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="da82d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da82d-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="da82d-112">Tapez</span><span class="sxs-lookup"><span data-stu-id="da82d-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="da82d-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="da82d-113">Attributes and Elements</span></span>

<span data-ttu-id="da82d-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="da82d-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="da82d-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="da82d-115">Attributes</span></span>

|<span data-ttu-id="da82d-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="da82d-116">Attribute</span></span>|<span data-ttu-id="da82d-117">Description</span><span class="sxs-lookup"><span data-stu-id="da82d-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="da82d-118">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="da82d-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="da82d-119">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="da82d-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="da82d-120">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="da82d-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="da82d-121">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="da82d-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="da82d-122">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="da82d-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="da82d-123">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="da82d-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="da82d-124">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="da82d-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="da82d-125">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="da82d-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="da82d-126">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="da82d-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="da82d-127">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="da82d-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="da82d-128">1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="da82d-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="da82d-129">2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="da82d-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="da82d-130">3. Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="da82d-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="da82d-131">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="da82d-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="da82d-132">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="da82d-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="da82d-133">valeur</span><span class="sxs-lookup"><span data-stu-id="da82d-133">Value</span></span>|<span data-ttu-id="da82d-134">Description</span><span class="sxs-lookup"><span data-stu-id="da82d-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="da82d-135">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="da82d-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="da82d-136">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="da82d-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="da82d-137">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="da82d-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="da82d-138">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="da82d-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="da82d-139">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="da82d-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="da82d-140">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="da82d-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="da82d-141">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="da82d-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="da82d-142">valeur</span><span class="sxs-lookup"><span data-stu-id="da82d-142">Value</span></span>|<span data-ttu-id="da82d-143">Description</span><span class="sxs-lookup"><span data-stu-id="da82d-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="da82d-144">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="da82d-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="da82d-145">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="da82d-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="da82d-146">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="da82d-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="da82d-147">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="da82d-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="da82d-148">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="da82d-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="da82d-149">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="da82d-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="da82d-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="da82d-150">Child Elements</span></span>

<span data-ttu-id="da82d-151">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="da82d-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="da82d-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="da82d-152">Parent Elements</span></span>

|<span data-ttu-id="da82d-153">Élément</span><span class="sxs-lookup"><span data-stu-id="da82d-153">Element</span></span>|<span data-ttu-id="da82d-154">Description</span><span class="sxs-lookup"><span data-stu-id="da82d-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da82d-155">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="da82d-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="da82d-156">Représente les fonctionnalités de sécurité du [\<wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="da82d-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="da82d-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da82d-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="da82d-158">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="da82d-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="da82d-159">Liaisons</span><span class="sxs-lookup"><span data-stu-id="da82d-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="da82d-160">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="da82d-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="da82d-161">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="da82d-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="da82d-162">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="da82d-162">\<binding></span></span>](bindings.md)
