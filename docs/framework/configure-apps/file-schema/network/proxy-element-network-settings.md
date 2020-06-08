---
title: <proxy>, élément (paramètres réseau)
description: L' <proxy> élément paramètres réseau définit les options de serveur proxy dans la .NET Framework. Cet article contient un exemple.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 0d462fcc92fc1be5ddbc2e76237d8436219c7295
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504535"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="a87b8-104">\<proxy>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a87b8-104">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="a87b8-105">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="a87b8-105">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="a87b8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a87b8-106">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a87b8-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a87b8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a87b8-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a87b8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a87b8-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a87b8-109">Attributes</span></span>  
  
|<span data-ttu-id="a87b8-110">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="a87b8-110">**Attribute**</span></span>|<span data-ttu-id="a87b8-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="a87b8-111">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="a87b8-112">Spécifie si le proxy est détecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a87b8-112">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="a87b8-113">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="a87b8-113">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="a87b8-114">Spécifie si le proxy est contourné pour les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="a87b8-114">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="a87b8-115">Les ressources locales incluent le serveur local ( `http://localhost` , `http://loopback` ou `http://127.0.0.1` ) et un URI sans point ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="a87b8-115">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="a87b8-116">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="a87b8-116">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="a87b8-117">Spécifie l’URI du proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a87b8-117">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="a87b8-118">Spécifie l’emplacement du script de configuration.</span><span class="sxs-lookup"><span data-stu-id="a87b8-118">Specifies the location of the configuration script.</span></span> <span data-ttu-id="a87b8-119">N’utilisez pas l' `bypassonlocal` attribut avec cet attribut.</span><span class="sxs-lookup"><span data-stu-id="a87b8-119">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="a87b8-120">Spécifie s’il faut utiliser les paramètres de proxy d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a87b8-120">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="a87b8-121">Si la valeur `true` est, les attributs suivants remplacent les paramètres de proxy d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a87b8-121">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="a87b8-122">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="a87b8-122">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a87b8-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a87b8-123">Child Elements</span></span>  
 <span data-ttu-id="a87b8-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a87b8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a87b8-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a87b8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a87b8-126">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="a87b8-126">**Element**</span></span>|<span data-ttu-id="a87b8-127">**Description**</span><span class="sxs-lookup"><span data-stu-id="a87b8-127">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a87b8-128">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a87b8-128">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a87b8-129">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="a87b8-129">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="a87b8-130">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a87b8-130">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87b8-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="a87b8-131">Remarks</span></span>  
 <span data-ttu-id="a87b8-132">L' `proxy` élément définit un serveur proxy pour une application.</span><span class="sxs-lookup"><span data-stu-id="a87b8-132">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="a87b8-133">Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilisera les paramètres de proxy dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a87b8-133">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="a87b8-134">La valeur de l' `proxyaddress` attribut doit être un URI (Uniform Resource Indicator) bien formé.</span><span class="sxs-lookup"><span data-stu-id="a87b8-134">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="a87b8-135">L' `scriptLocation` attribut fait référence à la détection automatique des scripts de configuration du proxy.</span><span class="sxs-lookup"><span data-stu-id="a87b8-135">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="a87b8-136">La <xref:System.Net.WebProxy> classe tente de localiser un script de configuration (généralement nommé WPAD. dat) lorsque l’option **utiliser le script de configuration automatique** est sélectionnée dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a87b8-136">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="a87b8-137">Si `bypassonlocal` est défini sur n’importe quelle valeur, `scriptLocation` est ignoré.</span><span class="sxs-lookup"><span data-stu-id="a87b8-137">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="a87b8-138">Utilisez l' `usesystemdefault` attribut pour les applications .NET Framework version 1,1 qui migrent vers la version 2,0.</span><span class="sxs-lookup"><span data-stu-id="a87b8-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="a87b8-139">Une exception est levée si l' `proxyaddress` attribut spécifie un proxy par défaut non valide.</span><span class="sxs-lookup"><span data-stu-id="a87b8-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="a87b8-140">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="a87b8-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a87b8-141">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a87b8-141">Configuration Files</span></span>  
 <span data-ttu-id="a87b8-142">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a87b8-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a87b8-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="a87b8-143">Example</span></span>  
 <span data-ttu-id="a87b8-144">L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.</span><span class="sxs-lookup"><span data-stu-id="a87b8-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a87b8-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a87b8-145">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a87b8-146">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a87b8-146">Network Settings Schema</span></span>](index.md)
