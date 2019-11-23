---
title: <webRequestModules>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697462"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="94798-102">\<webRequestModules >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="94798-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="94798-103">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="94798-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="94798-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="94798-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="94798-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="94798-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="94798-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="94798-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94798-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94798-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94798-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="94798-108">Attributes and Elements</span></span>  
 <span data-ttu-id="94798-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="94798-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94798-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="94798-110">Attributes</span></span>  
 <span data-ttu-id="94798-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="94798-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94798-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="94798-112">Child Elements</span></span>  
  
|<span data-ttu-id="94798-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="94798-113">**Element**</span></span>|<span data-ttu-id="94798-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="94798-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="94798-115">add</span><span class="sxs-lookup"><span data-stu-id="94798-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="94798-116">Ajoute un module de demande Web personnalisé à l’application.</span><span class="sxs-lookup"><span data-stu-id="94798-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="94798-117">clear</span><span class="sxs-lookup"><span data-stu-id="94798-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="94798-118">Supprime tous les modules de demande Web inscrits de l’application.</span><span class="sxs-lookup"><span data-stu-id="94798-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="94798-119">remove</span><span class="sxs-lookup"><span data-stu-id="94798-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="94798-120">Supprime un module de demande Web personnalisé de l’application.</span><span class="sxs-lookup"><span data-stu-id="94798-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94798-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="94798-121">Parent Elements</span></span>  
  
|<span data-ttu-id="94798-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="94798-122">**Element**</span></span>|<span data-ttu-id="94798-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="94798-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="94798-124">system.net</span><span class="sxs-lookup"><span data-stu-id="94798-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="94798-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="94798-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94798-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="94798-126">Remarks</span></span>  
 <span data-ttu-id="94798-127">L’élément `webRequestModules` inscrit les descendants de la classe <xref:System.Net.WebRequest> pour gérer les demandes d’informations aux hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="94798-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="94798-128">Les modules de demande Web doivent implémenter l’interface <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="94798-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="94798-129">Le .NET Framework comprend des modules de demande Web pour les URI qui commencent par `http://`, `https://`et `file://`.</span><span class="sxs-lookup"><span data-stu-id="94798-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="94798-130">Vous pouvez remplacer les modules par défaut uniquement en inscrivant un module personnalisé dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="94798-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="94798-131">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="94798-131">Configuration Files</span></span>  
 <span data-ttu-id="94798-132">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="94798-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94798-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="94798-133">Example</span></span>  
 <span data-ttu-id="94798-134">L’exemple suivant enregistre le module HTTP par défaut.</span><span class="sxs-lookup"><span data-stu-id="94798-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="94798-135">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="94798-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94798-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94798-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="94798-137">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="94798-137">Network Settings Schema</span></span>](index.md)
