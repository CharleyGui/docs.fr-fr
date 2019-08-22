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
ms.openlocfilehash: a183c4160c4cd55b05c5c23f7a10e3a1d1c74ea4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659294"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="e619f-102">\<Élément proxy > (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e619f-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="e619f-103">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="e619f-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="e619f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e619f-104">\<configuration></span></span>  
<span data-ttu-id="e619f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e619f-105">\<system.net></span></span>  
<span data-ttu-id="e619f-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="e619f-106">\<defaultProxy></span></span>  
<span data-ttu-id="e619f-107">\<proxy></span><span class="sxs-lookup"><span data-stu-id="e619f-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e619f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e619f-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e619f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e619f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e619f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e619f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e619f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e619f-111">Attributes</span></span>  
  
|<span data-ttu-id="e619f-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="e619f-112">**Attribute**</span></span>|<span data-ttu-id="e619f-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="e619f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="e619f-114">Spécifie si le proxy est détecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e619f-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="e619f-115">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e619f-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="e619f-116">Spécifie si le proxy est contourné pour les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="e619f-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="e619f-117">Les ressources locales incluent le serveur local`http://localhost`( `http://loopback`, ou `http://127.0.0.1`) et un URI sans point (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="e619f-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="e619f-118">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e619f-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="e619f-119">Spécifie l’URI du proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e619f-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="e619f-120">Spécifie l’emplacement du script de configuration.</span><span class="sxs-lookup"><span data-stu-id="e619f-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="e619f-121">N’utilisez pas l' `bypassonlocal` attribut avec cet attribut.</span><span class="sxs-lookup"><span data-stu-id="e619f-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="e619f-122">Spécifie s’il faut utiliser les paramètres de proxy d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e619f-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="e619f-123">Si la valeur `true`est, les attributs suivants remplacent les paramètres de proxy d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e619f-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="e619f-124">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e619f-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e619f-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e619f-125">Child Elements</span></span>  
 <span data-ttu-id="e619f-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e619f-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e619f-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e619f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e619f-128">**Élément**</span><span class="sxs-lookup"><span data-stu-id="e619f-128">**Element**</span></span>|<span data-ttu-id="e619f-129">**Description**</span><span class="sxs-lookup"><span data-stu-id="e619f-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e619f-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e619f-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e619f-131">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="e619f-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="e619f-132">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e619f-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e619f-133">Notes</span><span class="sxs-lookup"><span data-stu-id="e619f-133">Remarks</span></span>  
 <span data-ttu-id="e619f-134">L' `proxy` élément définit un serveur proxy pour une application.</span><span class="sxs-lookup"><span data-stu-id="e619f-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="e619f-135">Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilisera les paramètres de proxy dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e619f-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="e619f-136">La valeur de l' `proxyaddress` attribut doit être un URI (Uniform Resource Indicator) bien formé.</span><span class="sxs-lookup"><span data-stu-id="e619f-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="e619f-137">L' `scriptLocation` attribut fait référence à la détection automatique des scripts de configuration du proxy.</span><span class="sxs-lookup"><span data-stu-id="e619f-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="e619f-138">La <xref:System.Net.WebProxy> classe tente de localiser un script de configuration (généralement nommé WPAD. dat) lorsque l’option **utiliser le script de configuration automatique** est sélectionnée dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e619f-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="e619f-139">Si `bypassonlocal` est défini sur n’importe quelle `scriptLocation` valeur, est ignoré.</span><span class="sxs-lookup"><span data-stu-id="e619f-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="e619f-140">Utilisez l' `usesystemdefault` attribut pour les applications .NET Framework version 1,1 qui migrent vers la version 2,0.</span><span class="sxs-lookup"><span data-stu-id="e619f-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="e619f-141">Une exception est levée si l' `proxyaddress` attribut spécifie un proxy par défaut non valide.</span><span class="sxs-lookup"><span data-stu-id="e619f-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="e619f-142">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="e619f-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e619f-143">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e619f-143">Configuration Files</span></span>  
 <span data-ttu-id="e619f-144">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e619f-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e619f-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="e619f-145">Example</span></span>  
 <span data-ttu-id="e619f-146">L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.</span><span class="sxs-lookup"><span data-stu-id="e619f-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e619f-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e619f-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e619f-148">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="e619f-148">Network Settings Schema</span></span>](index.md)
