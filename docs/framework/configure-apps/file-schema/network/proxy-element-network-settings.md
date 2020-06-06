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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154788"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="f9e67-102">\<proxy>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="f9e67-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="f9e67-103">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="f9e67-103">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="f9e67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9e67-104">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9e67-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f9e67-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f9e67-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f9e67-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9e67-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f9e67-107">Attributes</span></span>  
  
|<span data-ttu-id="f9e67-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="f9e67-108">**Attribute**</span></span>|<span data-ttu-id="f9e67-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="f9e67-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="f9e67-110">Spécifie si le proxy est détecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="f9e67-110">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="f9e67-111">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="f9e67-111">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="f9e67-112">Spécifie si le proxy est contourné pour les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="f9e67-112">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="f9e67-113">Les ressources locales incluent le serveur local ( `http://localhost` , `http://loopback` ou `http://127.0.0.1` ) et un URI sans point ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="f9e67-113">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="f9e67-114">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="f9e67-114">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="f9e67-115">Spécifie l’URI du proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f9e67-115">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="f9e67-116">Spécifie l’emplacement du script de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9e67-116">Specifies the location of the configuration script.</span></span> <span data-ttu-id="f9e67-117">N’utilisez pas l' `bypassonlocal` attribut avec cet attribut.</span><span class="sxs-lookup"><span data-stu-id="f9e67-117">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="f9e67-118">Spécifie s’il faut utiliser les paramètres de proxy d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f9e67-118">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="f9e67-119">Si la valeur `true` est, les attributs suivants remplacent les paramètres de proxy d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f9e67-119">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="f9e67-120">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="f9e67-120">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9e67-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9e67-121">Child Elements</span></span>  
 <span data-ttu-id="f9e67-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f9e67-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9e67-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f9e67-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f9e67-124">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="f9e67-124">**Element**</span></span>|<span data-ttu-id="f9e67-125">**Description**</span><span class="sxs-lookup"><span data-stu-id="f9e67-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f9e67-126">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="f9e67-126">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="f9e67-127">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="f9e67-127">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="f9e67-128">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="f9e67-128">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9e67-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="f9e67-129">Remarks</span></span>  
 <span data-ttu-id="f9e67-130">L' `proxy` élément définit un serveur proxy pour une application.</span><span class="sxs-lookup"><span data-stu-id="f9e67-130">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="f9e67-131">Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilisera les paramètres de proxy dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f9e67-131">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="f9e67-132">La valeur de l' `proxyaddress` attribut doit être un URI (Uniform Resource Indicator) bien formé.</span><span class="sxs-lookup"><span data-stu-id="f9e67-132">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="f9e67-133">L' `scriptLocation` attribut fait référence à la détection automatique des scripts de configuration du proxy.</span><span class="sxs-lookup"><span data-stu-id="f9e67-133">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="f9e67-134">La <xref:System.Net.WebProxy> classe tente de localiser un script de configuration (généralement nommé WPAD. dat) lorsque l’option **utiliser le script de configuration automatique** est sélectionnée dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f9e67-134">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="f9e67-135">Si `bypassonlocal` est défini sur n’importe quelle valeur, `scriptLocation` est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f9e67-135">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="f9e67-136">Utilisez l' `usesystemdefault` attribut pour les applications .NET Framework version 1,1 qui migrent vers la version 2,0.</span><span class="sxs-lookup"><span data-stu-id="f9e67-136">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="f9e67-137">Une exception est levée si l' `proxyaddress` attribut spécifie un proxy par défaut non valide.</span><span class="sxs-lookup"><span data-stu-id="f9e67-137">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="f9e67-138">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="f9e67-138">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f9e67-139">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="f9e67-139">Configuration Files</span></span>  
 <span data-ttu-id="f9e67-140">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f9e67-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9e67-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9e67-141">Example</span></span>  
 <span data-ttu-id="f9e67-142">L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.</span><span class="sxs-lookup"><span data-stu-id="f9e67-142">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9e67-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9e67-143">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f9e67-144">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="f9e67-144">Network Settings Schema</span></span>](index.md)
