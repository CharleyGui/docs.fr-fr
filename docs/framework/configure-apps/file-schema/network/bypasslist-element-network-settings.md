---
title: <bypasslist>, élément (paramètres réseau)
description: L' <bypasslist> élément paramètres réseau fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 42b6ddf4c3d09bcf8ef0ada105cefedccc63b505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504626"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="544fc-103">\<bypasslist>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="544fc-103">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="544fc-104">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="544fc-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="544fc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="544fc-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="544fc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="544fc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="544fc-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="544fc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="544fc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="544fc-108">Attributes</span></span>  
 <span data-ttu-id="544fc-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="544fc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="544fc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="544fc-110">Child Elements</span></span>  
  
|<span data-ttu-id="544fc-111">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="544fc-111">**Element**</span></span>|<span data-ttu-id="544fc-112">**Description**</span><span class="sxs-lookup"><span data-stu-id="544fc-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="544fc-113">add</span><span class="sxs-lookup"><span data-stu-id="544fc-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="544fc-114">Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="544fc-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="544fc-115">clear</span><span class="sxs-lookup"><span data-stu-id="544fc-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="544fc-116">Efface la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="544fc-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="544fc-117">remove</span><span class="sxs-lookup"><span data-stu-id="544fc-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="544fc-118">Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="544fc-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="544fc-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="544fc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="544fc-120">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="544fc-120">**Element**</span></span>|<span data-ttu-id="544fc-121">**Description**</span><span class="sxs-lookup"><span data-stu-id="544fc-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="544fc-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="544fc-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="544fc-123">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="544fc-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="544fc-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="544fc-124">Remarks</span></span>  
 <span data-ttu-id="544fc-125">La liste de contournement contient des expressions régulières qui décrivent les URI qui <xref:System.Net.WebRequest> excèdent directement l’accès au serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="544fc-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="544fc-126">Vous devez faire attention lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="544fc-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="544fc-127">L’expression régulière "[a-z] + \\ . contoso \\ . com" correspond à n’importe quel hôte dans le domaine contoso.com, mais correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="544fc-127">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="544fc-128">Pour correspondre uniquement à un hôte dans le domaine contoso.com, utilisez un point d’ancrage (« $ ») : « [a-z] + \\ . contoso \\ . com $ ».</span><span class="sxs-lookup"><span data-stu-id="544fc-128">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="544fc-129">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="544fc-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="544fc-130">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="544fc-130">Configuration Files</span></span>  
 <span data-ttu-id="544fc-131">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="544fc-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="544fc-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="544fc-132">Example</span></span>  
 <span data-ttu-id="544fc-133">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="544fc-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="544fc-134">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192,168.</span><span class="sxs-lookup"><span data-stu-id="544fc-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="544fc-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="544fc-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="544fc-136">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="544fc-136">Network Settings Schema</span></span>](index.md)
