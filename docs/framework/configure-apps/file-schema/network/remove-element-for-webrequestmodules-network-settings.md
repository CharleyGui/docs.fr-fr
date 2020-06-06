---
title: <remove>, élément de webRequestModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154723"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="df505-102">\<remove>, élément de webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="df505-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="df505-103">Supprime un module de demande Web personnalisé de l’application.</span><span class="sxs-lookup"><span data-stu-id="df505-103">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="df505-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df505-104">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df505-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="df505-105">Attributes and Elements</span></span>  
 <span data-ttu-id="df505-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="df505-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df505-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="df505-107">Attributes</span></span>  
  
|<span data-ttu-id="df505-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="df505-108">**Attribute**</span></span>|<span data-ttu-id="df505-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="df505-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="df505-110">Préfixe URI pour les requêtes gérées par ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="df505-110">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df505-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="df505-111">Child Elements</span></span>  
 <span data-ttu-id="df505-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="df505-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df505-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="df505-113">Parent Elements</span></span>  
  
|<span data-ttu-id="df505-114">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="df505-114">**Element**</span></span>|<span data-ttu-id="df505-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="df505-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="df505-116">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="df505-116">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="df505-117">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="df505-117">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df505-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="df505-118">Remarks</span></span>  
 <span data-ttu-id="df505-119">L' `remove` élément supprime le module de demande Web inscrit pour le préfixe URI spécifié.</span><span class="sxs-lookup"><span data-stu-id="df505-119">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="df505-120">La valeur de l' `prefix` attribut doit être les caractères de début d’un URI valide, par exemple, « `http` » ou « `http://www.contoso.com` ».</span><span class="sxs-lookup"><span data-stu-id="df505-120">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="df505-121">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="df505-121">Configuration Files</span></span>  
 <span data-ttu-id="df505-122">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="df505-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df505-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="df505-123">Example</span></span>  

<span data-ttu-id="df505-124">L’exemple suivant supprime le module de demande Web existant pour HTTP, puis inscrit un nouveau module de demande Web personnalisé pour les requêtes HTTP à `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="df505-124">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df505-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df505-125">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="df505-126">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="df505-126">Network Settings Schema</span></span>](index.md)
