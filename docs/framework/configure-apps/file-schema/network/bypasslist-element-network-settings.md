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
ms.openlocfilehash: bd746f07b4c4eb08bf34b01d555b5799d9af0cf3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927478"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="9c4e7-102">\<BypassList >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="9c4e7-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="9c4e7-103">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="9c4e7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9c4e7-104">\<configuration></span></span>  
<span data-ttu-id="9c4e7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9c4e7-105">\<system.net></span></span>  
<span data-ttu-id="9c4e7-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="9c4e7-106">\<defaultProxy></span></span>  
<span data-ttu-id="9c4e7-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="9c4e7-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4e7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c4e7-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c4e7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c4e7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9c4e7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c4e7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c4e7-111">Attributes</span></span>  
 <span data-ttu-id="9c4e7-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c4e7-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c4e7-113">Child Elements</span></span>  
  
|<span data-ttu-id="9c4e7-114">**Élément**</span><span class="sxs-lookup"><span data-stu-id="9c4e7-114">**Element**</span></span>|<span data-ttu-id="9c4e7-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="9c4e7-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9c4e7-116">add</span><span class="sxs-lookup"><span data-stu-id="9c4e7-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="9c4e7-117">Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="9c4e7-118">clear</span><span class="sxs-lookup"><span data-stu-id="9c4e7-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="9c4e7-119">Efface la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="9c4e7-120">remove</span><span class="sxs-lookup"><span data-stu-id="9c4e7-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="9c4e7-121">Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c4e7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c4e7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9c4e7-123">**Élément**</span><span class="sxs-lookup"><span data-stu-id="9c4e7-123">**Element**</span></span>|<span data-ttu-id="9c4e7-124">**Description**</span><span class="sxs-lookup"><span data-stu-id="9c4e7-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9c4e7-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="9c4e7-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="9c4e7-126">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="9c4e7-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c4e7-127">Notes</span><span class="sxs-lookup"><span data-stu-id="9c4e7-127">Remarks</span></span>  
 <span data-ttu-id="9c4e7-128">La liste de contournement contient des expressions régulières qui <xref:System.Net.WebRequest> décrivent les URI qui excèdent directement l’accès au serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="9c4e7-129">Vous devez faire attention lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="9c4e7-130">L’expression régulière "[a-z] +\\. contoso\\. com" correspond à n’importe quel hôte dans le domaine contoso.com, mais correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="9c4e7-131">Pour correspondre uniquement à un hôte dans le domaine contoso.com, utilisez un point d’ancrage («$»): «[a-\\z]\\+. contoso. com $».</span><span class="sxs-lookup"><span data-stu-id="9c4e7-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="9c4e7-132">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9c4e7-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9c4e7-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="9c4e7-133">Configuration Files</span></span>  
 <span data-ttu-id="9c4e7-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9c4e7-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c4e7-135">Exemples</span><span class="sxs-lookup"><span data-stu-id="9c4e7-135">Example</span></span>  
 <span data-ttu-id="9c4e7-136">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="9c4e7-137">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192,168.</span><span class="sxs-lookup"><span data-stu-id="9c4e7-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c4e7-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c4e7-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="9c4e7-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="9c4e7-139">Network Settings Schema</span></span>](index.md)
