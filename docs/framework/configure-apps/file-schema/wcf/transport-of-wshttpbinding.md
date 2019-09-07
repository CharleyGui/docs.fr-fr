---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 95cfa076f62f767af431ff5a0bcc2ca31b824e30
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399242"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="ab5ab-102">\<> de transport \<de wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ab5ab-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="ab5ab-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="ab5ab-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab5ab-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ab5ab-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ab5ab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="ab5ab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="ab5ab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ab5ab-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="ab5ab-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="ab5ab-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ab5ab-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab5ab-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="ab5ab-112">Type</span><span class="sxs-lookup"><span data-stu-id="ab5ab-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="ab5ab-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ab5ab-113">Attributes and Elements</span></span>

<span data-ttu-id="ab5ab-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab5ab-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="ab5ab-115">Attributes</span></span>

|<span data-ttu-id="ab5ab-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="ab5ab-116">Attribute</span></span>|<span data-ttu-id="ab5ab-117">Description</span><span class="sxs-lookup"><span data-stu-id="ab5ab-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="ab5ab-118">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ab5ab-119">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="ab5ab-120">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ab5ab-121">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="ab5ab-122">Chaîne indiquant le domaine de l’authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ab5ab-123">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ab5ab-124">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ab5ab-125">Il peut également spécifier une collection d’utilisateurs disposant d’un accès.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="ab5ab-126">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="ab5ab-127">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="ab5ab-128">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="ab5ab-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="ab5ab-129">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="ab5ab-130">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="ab5ab-131">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ab5ab-132">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="ab5ab-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="ab5ab-133">Valeur</span><span class="sxs-lookup"><span data-stu-id="ab5ab-133">Value</span></span>|<span data-ttu-id="ab5ab-134">Description</span><span class="sxs-lookup"><span data-stu-id="ab5ab-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="ab5ab-135">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="ab5ab-136">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="ab5ab-137">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="ab5ab-138">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="ab5ab-139">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="ab5ab-140">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ab5ab-141">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="ab5ab-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="ab5ab-142">`Value`</span><span class="sxs-lookup"><span data-stu-id="ab5ab-142">Value</span></span>|<span data-ttu-id="ab5ab-143">Description</span><span class="sxs-lookup"><span data-stu-id="ab5ab-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="ab5ab-144">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="ab5ab-145">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="ab5ab-146">Utilise l’authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="ab5ab-147">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="ab5ab-148">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="ab5ab-149">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ab5ab-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ab5ab-150">Child Elements</span></span>

<span data-ttu-id="ab5ab-151">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab5ab-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ab5ab-152">Parent Elements</span></span>

|<span data-ttu-id="ab5ab-153">Élément</span><span class="sxs-lookup"><span data-stu-id="ab5ab-153">Element</span></span>|<span data-ttu-id="ab5ab-154">Description</span><span class="sxs-lookup"><span data-stu-id="ab5ab-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab5ab-155">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="ab5ab-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="ab5ab-156">Représente les fonctionnalités de sécurité de l' [ \<> WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ab5ab-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="ab5ab-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab5ab-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="ab5ab-158">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ab5ab-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ab5ab-159">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ab5ab-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ab5ab-160">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="ab5ab-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ab5ab-161">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ab5ab-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ab5ab-162">\<binding></span><span class="sxs-lookup"><span data-stu-id="ab5ab-162">\<binding></span></span>](../../../misc/binding.md)
