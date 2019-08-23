---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 384267e3d018d714f95356461eb303bc9ec0cb3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934637"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="15146-102">\<> de transport \<de wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="15146-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="15146-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="15146-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="15146-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="15146-104">\<system.serviceModel></span></span>\
<span data-ttu-id="15146-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="15146-105">\<bindings></span></span>\
<span data-ttu-id="15146-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="15146-106">\<wsHttpBinding></span></span>\
<span data-ttu-id="15146-107">\<liaison > </span><span class="sxs-lookup"><span data-stu-id="15146-107">\<binding></span></span>\
<span data-ttu-id="15146-108">\<> de sécurité </span><span class="sxs-lookup"><span data-stu-id="15146-108">\<security></span></span>\
<span data-ttu-id="15146-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="15146-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="15146-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15146-110">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="15146-111">Type</span><span class="sxs-lookup"><span data-stu-id="15146-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="15146-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="15146-112">Attributes and Elements</span></span>

<span data-ttu-id="15146-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="15146-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="15146-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="15146-114">Attributes</span></span>

|<span data-ttu-id="15146-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="15146-115">Attribute</span></span>|<span data-ttu-id="15146-116">Description</span><span class="sxs-lookup"><span data-stu-id="15146-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="15146-117">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="15146-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="15146-118">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="15146-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="15146-119">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="15146-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="15146-120">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="15146-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="15146-121">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="15146-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="15146-122">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="15146-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="15146-123">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="15146-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="15146-124">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="15146-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="15146-125">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="15146-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="15146-126">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="15146-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="15146-127">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="15146-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="15146-128">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="15146-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="15146-129">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="15146-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="15146-130">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="15146-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="15146-131">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="15146-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="15146-132">`Value`</span><span class="sxs-lookup"><span data-stu-id="15146-132">Value</span></span>|<span data-ttu-id="15146-133">Description</span><span class="sxs-lookup"><span data-stu-id="15146-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="15146-134">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="15146-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="15146-135">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="15146-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="15146-136">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="15146-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="15146-137">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="15146-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="15146-138">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="15146-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="15146-139">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="15146-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="15146-140">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="15146-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="15146-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="15146-141">Value</span></span>|<span data-ttu-id="15146-142">Description</span><span class="sxs-lookup"><span data-stu-id="15146-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="15146-143">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="15146-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="15146-144">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="15146-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="15146-145">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="15146-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="15146-146">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="15146-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="15146-147">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="15146-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="15146-148">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="15146-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="15146-149">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="15146-149">Child Elements</span></span>

<span data-ttu-id="15146-150">Aucun.</span><span class="sxs-lookup"><span data-stu-id="15146-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15146-151">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="15146-151">Parent Elements</span></span>

|<span data-ttu-id="15146-152">Élément</span><span class="sxs-lookup"><span data-stu-id="15146-152">Element</span></span>|<span data-ttu-id="15146-153">Description</span><span class="sxs-lookup"><span data-stu-id="15146-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15146-154">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="15146-154">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="15146-155">Représente les fonctionnalités de sécurité de l' [ \<> WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="15146-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="15146-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15146-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="15146-157">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="15146-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="15146-158">Liaisons</span><span class="sxs-lookup"><span data-stu-id="15146-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="15146-159">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="15146-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="15146-160">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="15146-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="15146-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="15146-161">\<binding></span></span>](../../../misc/binding.md)
