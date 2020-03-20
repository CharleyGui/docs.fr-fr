---
title: <clear>, élément de bypasslist (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: c25477c2c99be66b34b07e1f7e50115bfa8d14e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154931"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="f3f3f-102">\<élément clair> pour la bypasslist (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="f3f3f-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="f3f3f-103">Efface la liste de dérivation par procuration.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="f3f3f-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3f3f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3f3f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f3f3f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f3f3f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f3f3f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="f3f3f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de la liste de contournement**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f3f3f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="f3f3f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clair>**</span><span class="sxs-lookup"><span data-stu-id="f3f3f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f3f3f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3f3f-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3f3f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f3f3f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3f3f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3f3f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f3f3f-112">Attributes</span></span>  
 <span data-ttu-id="f3f3f-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3f3f-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f3f3f-114">Child Elements</span></span>  
 <span data-ttu-id="f3f3f-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3f3f-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f3f3f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f3f3f-117">**Élément**</span><span class="sxs-lookup"><span data-stu-id="f3f3f-117">**Element**</span></span>|<span data-ttu-id="f3f3f-118">**Description**</span><span class="sxs-lookup"><span data-stu-id="f3f3f-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3f3f-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="f3f3f-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="f3f3f-120">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas un proxy.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3f3f-121">Notes </span><span class="sxs-lookup"><span data-stu-id="f3f3f-121">Remarks</span></span>  
 <span data-ttu-id="f3f3f-122">L’élément `clear` efface toutes les entrées de la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f3f3f-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="f3f3f-123">Configuration Files</span></span>  
 <span data-ttu-id="f3f3f-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f3f3f-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f3f-125"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f3f3f-125">Example</span></span>  
 <span data-ttu-id="f3f3f-126">L’exemple suivant efface la liste de contournement, puis ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="f3f3f-127">Le premier contourne le proxy pour tous les serveurs du domaine contoso.com ; le second contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192.168.</span><span class="sxs-lookup"><span data-stu-id="f3f3f-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="f3f3f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3f3f-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f3f3f-129">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="f3f3f-129">Network Settings Schema</span></span>](index.md)
