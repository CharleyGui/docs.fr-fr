---
title: <bypasslist>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 7a6c1282c9ca8381d2dbb21ffdc82f95732c42b3
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087526"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="d3ec6-102">\<BypassList >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="d3ec6-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="d3ec6-103">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="d3ec6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3ec6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3ec6-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d3ec6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="d3ec6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy**](defaultproxy-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="d3ec6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="d3ec6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="d3ec6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d3ec6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3ec6-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3ec6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d3ec6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d3ec6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3ec6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3ec6-111">Attributes</span></span>  
 <span data-ttu-id="d3ec6-112">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="d3ec6-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3ec6-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d3ec6-113">Child Elements</span></span>  
  
|<span data-ttu-id="d3ec6-114">**Élément**</span><span class="sxs-lookup"><span data-stu-id="d3ec6-114">**Element**</span></span>|<span data-ttu-id="d3ec6-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="d3ec6-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d3ec6-116">add</span><span class="sxs-lookup"><span data-stu-id="d3ec6-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="d3ec6-117">Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="d3ec6-118">clear</span><span class="sxs-lookup"><span data-stu-id="d3ec6-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="d3ec6-119">Efface la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="d3ec6-120">remove</span><span class="sxs-lookup"><span data-stu-id="d3ec6-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="d3ec6-121">Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3ec6-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d3ec6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d3ec6-123">**Élément**</span><span class="sxs-lookup"><span data-stu-id="d3ec6-123">**Element**</span></span>|<span data-ttu-id="d3ec6-124">**Description**</span><span class="sxs-lookup"><span data-stu-id="d3ec6-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d3ec6-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d3ec6-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="d3ec6-126">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="d3ec6-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3ec6-127">Notes</span><span class="sxs-lookup"><span data-stu-id="d3ec6-127">Remarks</span></span>  
 <span data-ttu-id="d3ec6-128">La liste de contournement contient des expressions régulières qui décrivent les URI auxquels <xref:System.Net.WebRequest> instances accèdent directement au lieu de passer par le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="d3ec6-129">Vous devez faire attention lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="d3ec6-130">L’expression régulière "[a-z] +\\. contoso\\. com" correspond à n’importe quel hôte dans le domaine contoso.com, mais correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="d3ec6-131">Pour correspondre uniquement à un hôte dans le domaine contoso.com, utilisez un point d’ancrage (« $ ») : « [a-z] +\\. contoso\\. com $ ».</span><span class="sxs-lookup"><span data-stu-id="d3ec6-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="d3ec6-132">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d3ec6-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d3ec6-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d3ec6-133">Configuration Files</span></span>  
 <span data-ttu-id="d3ec6-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d3ec6-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ec6-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3ec6-135">Example</span></span>  
 <span data-ttu-id="d3ec6-136">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="d3ec6-137">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192,168.</span><span class="sxs-lookup"><span data-stu-id="d3ec6-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3ec6-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3ec6-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d3ec6-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="d3ec6-139">Network Settings Schema</span></span>](index.md)
