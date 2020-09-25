---
title: <system.Net>, élément (paramètres réseau)
description: L’élément paramètres réseau <system.Net> contient des paramètres qui spécifient la façon dont le .NET Framework se connecte aux options réseau dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 80d54df40c6798e146013b4f2d867386ae35169c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201718"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="cf8a0-103">\<system.Net>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="cf8a0-103">\<system.Net> Element (Network Settings)</span></span>

<span data-ttu-id="cf8a0-104">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-104">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="cf8a0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf8a0-105">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf8a0-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cf8a0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cf8a0-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf8a0-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="cf8a0-108">Attributes</span></span>  

 <span data-ttu-id="cf8a0-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf8a0-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cf8a0-110">Child Elements</span></span>  
  
|<span data-ttu-id="cf8a0-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="cf8a0-111">**Element**</span></span>|<span data-ttu-id="cf8a0-112">**Description**</span><span class="sxs-lookup"><span data-stu-id="cf8a0-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cf8a0-113">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="cf8a0-113">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="cf8a0-114">Spécifie les modules utilisés pour authentifier les requêtes Internet.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-114">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="cf8a0-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="cf8a0-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="cf8a0-116">Spécifie le nombre maximal de connexions à un hôte Internet.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-116">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="cf8a0-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="cf8a0-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="cf8a0-118">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="cf8a0-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="cf8a0-119">mailSettings</span><span class="sxs-lookup"><span data-stu-id="cf8a0-119">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="cf8a0-120">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="cf8a0-120">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="cf8a0-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="cf8a0-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="cf8a0-122">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-122">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="cf8a0-123">settings</span><span class="sxs-lookup"><span data-stu-id="cf8a0-123">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="cf8a0-124">Configure les options réseau de base pour les classes dans les <xref:System.Net> espaces de noms enfants associés.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-124">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="cf8a0-125">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="cf8a0-125">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="cf8a0-126">Spécifie les modules à utiliser pour demander des informations à partir d’hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-126">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf8a0-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cf8a0-127">Parent Elements</span></span>  
  
|<span data-ttu-id="cf8a0-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="cf8a0-128">**Element**</span></span>|<span data-ttu-id="cf8a0-129">**Description**</span><span class="sxs-lookup"><span data-stu-id="cf8a0-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cf8a0-130">configuration</span><span class="sxs-lookup"><span data-stu-id="cf8a0-130">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="cf8a0-131">Contient les paramètres de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-131">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf8a0-132">Notes</span><span class="sxs-lookup"><span data-stu-id="cf8a0-132">Remarks</span></span>  

 <span data-ttu-id="cf8a0-133">L' [\<system.net>](system-net-element-network-settings.md) élément contient des paramètres pour les classes dans les <xref:System.Net> espaces de noms enfants associés.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-133">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="cf8a0-134">Les paramètres configurent les modules d’authentification, la gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demande Internet pour la réception d’informations à partir d’hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-134">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8a0-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf8a0-135">Example</span></span>  

 <span data-ttu-id="cf8a0-136">L’exemple suivant montre une configuration classique utilisée par les <xref:System.Net> classes.</span><span class="sxs-lookup"><span data-stu-id="cf8a0-136">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf8a0-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf8a0-137">See also</span></span>

- [<span data-ttu-id="cf8a0-138">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="cf8a0-138">Network Settings Schema</span></span>](index.md)
