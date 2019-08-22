---
title: <clear>, élément de webRequestModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: e175c70bd4932d6a8f9428e8cd9159a47df52558
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659435"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="a396c-102">\<Clear >, élément de webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a396c-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="a396c-103">Supprime tous les modules de demande Web inscrits de l’application.</span><span class="sxs-lookup"><span data-stu-id="a396c-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="a396c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a396c-104">\<configuration></span></span>  
<span data-ttu-id="a396c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a396c-105">\<system.net></span></span>  
<span data-ttu-id="a396c-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="a396c-106">\<webRequestModules></span></span>  
<span data-ttu-id="a396c-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="a396c-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a396c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a396c-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a396c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a396c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a396c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a396c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a396c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a396c-111">Attributes</span></span>  
 <span data-ttu-id="a396c-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a396c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a396c-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a396c-113">Child Elements</span></span>  
 <span data-ttu-id="a396c-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a396c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a396c-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a396c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a396c-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="a396c-116">**Element**</span></span>|<span data-ttu-id="a396c-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="a396c-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a396c-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="a396c-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="a396c-119">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="a396c-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a396c-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a396c-120">Remarks</span></span>  
 <span data-ttu-id="a396c-121">L' `clear` élément supprime tous les modules de demande Web inscrits qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="a396c-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a396c-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a396c-122">Configuration Files</span></span>  
 <span data-ttu-id="a396c-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a396c-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a396c-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="a396c-124">Example</span></span>  
 <span data-ttu-id="a396c-125">L’exemple suivant efface tous les modules de demande Web, puis inscrit un module de demande Web pour HTTP.</span><span class="sxs-lookup"><span data-stu-id="a396c-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a396c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a396c-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="a396c-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a396c-127">Network Settings Schema</span></span>](index.md)
