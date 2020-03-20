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
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154944"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="b0f5a-102">\<bypasslist> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b0f5a-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="b0f5a-103">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas un proxy.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="b0f5a-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0f5a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b0f5a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b0f5a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b0f5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b0f5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="b0f5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de la liste de contournement**</span><span class="sxs-lookup"><span data-stu-id="b0f5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b0f5a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0f5a-108">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0f5a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b0f5a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b0f5a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0f5a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="b0f5a-111">Attributes</span></span>  
 <span data-ttu-id="b0f5a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0f5a-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b0f5a-113">Child Elements</span></span>  
  
|<span data-ttu-id="b0f5a-114">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b0f5a-114">**Element**</span></span>|<span data-ttu-id="b0f5a-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="b0f5a-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b0f5a-116">ajouter</span><span class="sxs-lookup"><span data-stu-id="b0f5a-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="b0f5a-117">Ajoute une adresse IP ou un nom DNS à la liste de contournement par procuration.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="b0f5a-118">Clair</span><span class="sxs-lookup"><span data-stu-id="b0f5a-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="b0f5a-119">Efface la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="b0f5a-120">retirer</span><span class="sxs-lookup"><span data-stu-id="b0f5a-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="b0f5a-121">Supprime une adresse IP ou un nom DNS de la liste de contournement par procuration.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0f5a-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b0f5a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b0f5a-123">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b0f5a-123">**Element**</span></span>|<span data-ttu-id="b0f5a-124">**Description**</span><span class="sxs-lookup"><span data-stu-id="b0f5a-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b0f5a-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="b0f5a-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="b0f5a-126">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="b0f5a-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0f5a-127">Notes </span><span class="sxs-lookup"><span data-stu-id="b0f5a-127">Remarks</span></span>  
 <span data-ttu-id="b0f5a-128">La liste de contournement contient <xref:System.Net.WebRequest> des expressions régulières qui décrivent les URL qui s’ent entrent directement au lieu de via le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="b0f5a-129">Vous devez faire preuve de prudence lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="b0f5a-130">L’expression régulière "[a-z]md\\\\.contoso .com" correspond à n’importe quel hôte dans le domaine contoso.com, mais elle correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="b0f5a-131">Pour n’égaler qu’un hôte dans le domaine contoso.com, utilisez une ancre\\(«$») : « [a-z]md .contoso\\.com$.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="b0f5a-132">Pour plus d’informations sur les expressions régulières, voir . [.NET Framework Expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b0f5a-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b0f5a-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b0f5a-133">Configuration Files</span></span>  
 <span data-ttu-id="b0f5a-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b0f5a-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f5a-135"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b0f5a-135">Example</span></span>  
 <span data-ttu-id="b0f5a-136">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="b0f5a-137">Le premier contourne le proxy pour tous les serveurs du domaine contoso.com ; le second contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192.168.</span><span class="sxs-lookup"><span data-stu-id="b0f5a-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0f5a-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0f5a-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="b0f5a-139">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="b0f5a-139">Network Settings Schema</span></span>](index.md)
