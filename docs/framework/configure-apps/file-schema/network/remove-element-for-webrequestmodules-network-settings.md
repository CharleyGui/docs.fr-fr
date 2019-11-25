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
ms.openlocfilehash: ca3a78a491c61b6e23dab0f96eebceb3157706ae
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089133"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="3f6f0-102">\<supprimer > élément de webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3f6f0-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="3f6f0-103">Supprime un module de demande Web personnalisé de l’application.</span><span class="sxs-lookup"><span data-stu-id="3f6f0-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="3f6f0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3f6f0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3f6f0-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3f6f0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3f6f0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3f6f0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="3f6f0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**supprimer >**</span><span class="sxs-lookup"><span data-stu-id="3f6f0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="3f6f0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f6f0-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f6f0-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f6f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f6f0-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f6f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f6f0-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f6f0-111">Attributes</span></span>  
  
|<span data-ttu-id="3f6f0-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="3f6f0-112">**Attribute**</span></span>|<span data-ttu-id="3f6f0-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="3f6f0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="3f6f0-114">Préfixe URI pour les requêtes gérées par ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="3f6f0-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f6f0-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f6f0-115">Child Elements</span></span>  
 <span data-ttu-id="3f6f0-116">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="3f6f0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f6f0-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f6f0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3f6f0-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="3f6f0-118">**Element**</span></span>|<span data-ttu-id="3f6f0-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="3f6f0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3f6f0-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="3f6f0-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="3f6f0-121">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="3f6f0-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f6f0-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3f6f0-122">Remarks</span></span>  
 <span data-ttu-id="3f6f0-123">L’élément `remove` supprime le module de demande Web inscrit pour le préfixe URI spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f6f0-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="3f6f0-124">La valeur de l’attribut `prefix` doit être les caractères de début d’un URI valide, par exemple «`http`» ou «`http://www.contoso.com`».</span><span class="sxs-lookup"><span data-stu-id="3f6f0-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3f6f0-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3f6f0-125">Configuration Files</span></span>  
 <span data-ttu-id="3f6f0-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3f6f0-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6f0-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f6f0-127">Example</span></span>  

<span data-ttu-id="3f6f0-128">L’exemple suivant supprime le module de demande Web existant pour HTTP, puis inscrit un nouveau module de demande Web personnalisé pour les requêtes HTTP à `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="3f6f0-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f6f0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f6f0-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="3f6f0-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3f6f0-130">Network Settings Schema</span></span>](index.md)
