---
title: <proxy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154788"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="1c5e6-102">\<élément> proxy (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="1c5e6-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="1c5e6-103">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-103">Defines a proxy server.</span></span>  

<span data-ttu-id="1c5e6-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1c5e6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1c5e6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1c5e6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="1c5e6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1c5e6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="1c5e6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>par procuration**</span><span class="sxs-lookup"><span data-stu-id="1c5e6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1c5e6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c5e6-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c5e6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1c5e6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1c5e6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c5e6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="1c5e6-111">Attributes</span></span>  
  
|<span data-ttu-id="1c5e6-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="1c5e6-112">**Attribute**</span></span>|<span data-ttu-id="1c5e6-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="1c5e6-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="1c5e6-114">Spécifie si le proxy est détecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="1c5e6-115">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="1c5e6-116">Spécifie si le proxy est contourné pour les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="1c5e6-117">Les ressources locales`http://localhost`comprennent `http://loopback`le `http://127.0.0.1`serveur local ( ,`http://webserver`, ou ) et un URI sans période ( ).</span><span class="sxs-lookup"><span data-stu-id="1c5e6-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="1c5e6-118">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="1c5e6-119">Spécifie l’URI proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="1c5e6-120">Spécifie l’emplacement du script de configuration.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="1c5e6-121">N’utilisez `bypassonlocal` pas l’attribut avec cet attribut.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="1c5e6-122">Précise s’il faut utiliser les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="1c5e6-123">Si défini `true`à , attributs ultérieurs remplacera les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="1c5e6-124">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c5e6-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1c5e6-125">Child Elements</span></span>  
 <span data-ttu-id="1c5e6-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c5e6-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1c5e6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1c5e6-128">**Élément**</span><span class="sxs-lookup"><span data-stu-id="1c5e6-128">**Element**</span></span>|<span data-ttu-id="1c5e6-129">**Description**</span><span class="sxs-lookup"><span data-stu-id="1c5e6-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1c5e6-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="1c5e6-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="1c5e6-131">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="1c5e6-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="1c5e6-132">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="1c5e6-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c5e6-133">Notes </span><span class="sxs-lookup"><span data-stu-id="1c5e6-133">Remarks</span></span>  
 <span data-ttu-id="1c5e6-134">L’élément `proxy` définit un serveur proxy pour une application.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="1c5e6-135">Si cet élément est absent du fichier de configuration, alors le cadre .NET utilisera les paramètres proxy dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="1c5e6-136">La valeur `proxyaddress` de l’attribut devrait être un indicateur uniforme bien formé des ressources (URI).</span><span class="sxs-lookup"><span data-stu-id="1c5e6-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="1c5e6-137">L’attribut `scriptLocation` se réfère à la détection automatique des scripts de configuration proxy.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="1c5e6-138">La <xref:System.Net.WebProxy> classe tentera de localiser un script de configuration (généralement appelé Wpad.dat) lorsque **l’option de script de configuration automatique Utiliser** est sélectionnée dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="1c5e6-139">Si `bypassonlocal` est réglé à `scriptLocation` une valeur quelconque, est ignoré.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="1c5e6-140">Utilisez `usesystemdefault` l’attribut pour les applications .NET Framework version 1.1 qui migrent vers la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="1c5e6-141">Une exception est `proxyaddress` lancée si l’attribut spécifie un proxy par défaut invalide.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="1c5e6-142">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1c5e6-143">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="1c5e6-143">Configuration Files</span></span>  
 <span data-ttu-id="1c5e6-144">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="1c5e6-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c5e6-145"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1c5e6-145">Example</span></span>  
 <span data-ttu-id="1c5e6-146">L’exemple suivant utilise les défauts du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.</span><span class="sxs-lookup"><span data-stu-id="1c5e6-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c5e6-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c5e6-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1c5e6-148">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="1c5e6-148">Network Settings Schema</span></span>](index.md)
