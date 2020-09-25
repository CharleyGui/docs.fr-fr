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
ms.openlocfilehash: 96cef2dff3156e49a93be818230c83370dab5264
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185859"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="8228a-102">\<clear>, élément de bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="8228a-102">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="8228a-103">Efface la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="8228a-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="8228a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8228a-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8228a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8228a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8228a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8228a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8228a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8228a-107">Attributes</span></span>  

 <span data-ttu-id="8228a-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8228a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8228a-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8228a-109">Child Elements</span></span>  

 <span data-ttu-id="8228a-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8228a-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8228a-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8228a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8228a-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="8228a-112">**Element**</span></span>|<span data-ttu-id="8228a-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="8228a-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8228a-114">BypassList</span><span class="sxs-lookup"><span data-stu-id="8228a-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="8228a-115">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="8228a-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8228a-116">Notes</span><span class="sxs-lookup"><span data-stu-id="8228a-116">Remarks</span></span>  

 <span data-ttu-id="8228a-117">L' `clear` élément efface toutes les entrées de la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="8228a-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8228a-118">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8228a-118">Configuration Files</span></span>  

 <span data-ttu-id="8228a-119">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8228a-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8228a-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="8228a-120">Example</span></span>  

 <span data-ttu-id="8228a-121">L’exemple suivant efface la liste de contournement, puis ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="8228a-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="8228a-122">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192,168.</span><span class="sxs-lookup"><span data-stu-id="8228a-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8228a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8228a-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8228a-124">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="8228a-124">Network Settings Schema</span></span>](index.md)
