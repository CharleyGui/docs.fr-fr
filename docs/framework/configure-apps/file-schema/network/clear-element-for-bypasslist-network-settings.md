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
ms.openlocfilehash: 2ad6b16370f600299439d2e810dfefa1b5fa3c06
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087532"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="0238c-102">\<Clear > élément de bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="0238c-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="0238c-103">Efface la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="0238c-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="0238c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0238c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0238c-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0238c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="0238c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy**](defaultproxy-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="0238c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="0238c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0238c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="0238c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Clear** ></span><span class="sxs-lookup"><span data-stu-id="0238c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0238c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0238c-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0238c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0238c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0238c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0238c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0238c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0238c-112">Attributes</span></span>  
 <span data-ttu-id="0238c-113">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="0238c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0238c-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0238c-114">Child Elements</span></span>  
 <span data-ttu-id="0238c-115">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="0238c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0238c-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0238c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0238c-117">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0238c-117">**Element**</span></span>|<span data-ttu-id="0238c-118">**Description**</span><span class="sxs-lookup"><span data-stu-id="0238c-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0238c-119">BypassList</span><span class="sxs-lookup"><span data-stu-id="0238c-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="0238c-120">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="0238c-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0238c-121">Notes</span><span class="sxs-lookup"><span data-stu-id="0238c-121">Remarks</span></span>  
 <span data-ttu-id="0238c-122">L’élément `clear` efface toutes les entrées de la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="0238c-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0238c-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0238c-123">Configuration Files</span></span>  
 <span data-ttu-id="0238c-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0238c-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0238c-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="0238c-125">Example</span></span>  
 <span data-ttu-id="0238c-126">L’exemple suivant efface la liste de contournement, puis ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="0238c-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="0238c-127">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192,168.</span><span class="sxs-lookup"><span data-stu-id="0238c-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0238c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0238c-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0238c-129">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="0238c-129">Network Settings Schema</span></span>](index.md)
