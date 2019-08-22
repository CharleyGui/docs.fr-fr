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
ms.openlocfilehash: e5305d9aed09b6c4d1ad4201e5e08e007a14c7c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664183"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="83d47-102">\<Clear >, élément de bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="83d47-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="83d47-103">Efface la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="83d47-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="83d47-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="83d47-104">\<configuration></span></span>  
<span data-ttu-id="83d47-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="83d47-105">\<system.net></span></span>  
<span data-ttu-id="83d47-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="83d47-106">\<defaultProxy></span></span>  
<span data-ttu-id="83d47-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="83d47-107">\<bypasslist></span></span>  
<span data-ttu-id="83d47-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="83d47-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d47-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83d47-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83d47-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="83d47-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83d47-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="83d47-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83d47-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="83d47-112">Attributes</span></span>  
 <span data-ttu-id="83d47-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="83d47-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="83d47-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="83d47-114">Child Elements</span></span>  
 <span data-ttu-id="83d47-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="83d47-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83d47-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="83d47-116">Parent Elements</span></span>  
  
|<span data-ttu-id="83d47-117">**Élément**</span><span class="sxs-lookup"><span data-stu-id="83d47-117">**Element**</span></span>|<span data-ttu-id="83d47-118">**Description**</span><span class="sxs-lookup"><span data-stu-id="83d47-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="83d47-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="83d47-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="83d47-120">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="83d47-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83d47-121">Notes</span><span class="sxs-lookup"><span data-stu-id="83d47-121">Remarks</span></span>  
 <span data-ttu-id="83d47-122">L' `clear` élément efface toutes les entrées de la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="83d47-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="83d47-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="83d47-123">Configuration Files</span></span>  
 <span data-ttu-id="83d47-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="83d47-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83d47-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="83d47-125">Example</span></span>  
 <span data-ttu-id="83d47-126">L’exemple suivant efface la liste de contournement, puis ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="83d47-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="83d47-127">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192,168.</span><span class="sxs-lookup"><span data-stu-id="83d47-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83d47-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d47-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="83d47-129">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="83d47-129">Network Settings Schema</span></span>](index.md)
