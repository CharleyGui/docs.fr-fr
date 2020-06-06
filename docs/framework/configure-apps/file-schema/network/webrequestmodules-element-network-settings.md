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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154541"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="50eb3-102">\<webRequestModules>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="50eb3-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="50eb3-103">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="50eb3-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="50eb3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50eb3-104">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50eb3-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50eb3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="50eb3-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="50eb3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50eb3-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="50eb3-107">Attributes</span></span>  
 <span data-ttu-id="50eb3-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50eb3-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="50eb3-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50eb3-109">Child Elements</span></span>  
  
|<span data-ttu-id="50eb3-110">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="50eb3-110">**Element**</span></span>|<span data-ttu-id="50eb3-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="50eb3-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="50eb3-112">add</span><span class="sxs-lookup"><span data-stu-id="50eb3-112">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="50eb3-113">Ajoute un module de demande Web personnalisé à l’application.</span><span class="sxs-lookup"><span data-stu-id="50eb3-113">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="50eb3-114">clear</span><span class="sxs-lookup"><span data-stu-id="50eb3-114">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="50eb3-115">Supprime tous les modules de demande Web inscrits de l’application.</span><span class="sxs-lookup"><span data-stu-id="50eb3-115">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="50eb3-116">remove</span><span class="sxs-lookup"><span data-stu-id="50eb3-116">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="50eb3-117">Supprime un module de demande Web personnalisé de l’application.</span><span class="sxs-lookup"><span data-stu-id="50eb3-117">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50eb3-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50eb3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="50eb3-119">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="50eb3-119">**Element**</span></span>|<span data-ttu-id="50eb3-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="50eb3-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="50eb3-121">system.net</span><span class="sxs-lookup"><span data-stu-id="50eb3-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="50eb3-122">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="50eb3-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50eb3-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="50eb3-123">Remarks</span></span>  
 <span data-ttu-id="50eb3-124">L' `webRequestModules` élément inscrit les descendants de la <xref:System.Net.WebRequest> classe pour gérer les demandes d’informations aux hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="50eb3-124">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="50eb3-125">Les modules de demande Web doivent implémenter l' <xref:System.Net.IWebRequestCreate> interface.</span><span class="sxs-lookup"><span data-stu-id="50eb3-125">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="50eb3-126">Le .NET Framework comprend des modules de demande Web pour les URI qui commencent par `http://` , `https://` et `file://` .</span><span class="sxs-lookup"><span data-stu-id="50eb3-126">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="50eb3-127">Vous pouvez remplacer les modules par défaut uniquement en inscrivant un module personnalisé dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="50eb3-127">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="50eb3-128">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="50eb3-128">Configuration Files</span></span>  
 <span data-ttu-id="50eb3-129">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="50eb3-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50eb3-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="50eb3-130">Example</span></span>  
 <span data-ttu-id="50eb3-131">L’exemple suivant enregistre le module HTTP par défaut.</span><span class="sxs-lookup"><span data-stu-id="50eb3-131">The following example registers the default HTTP module.</span></span> <span data-ttu-id="50eb3-132">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="50eb3-132">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50eb3-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50eb3-133">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="50eb3-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="50eb3-134">Network Settings Schema</span></span>](index.md)
