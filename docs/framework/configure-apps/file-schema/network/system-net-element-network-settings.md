---
title: <system.Net>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154554"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="0af55-102">\<system.Net>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="0af55-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="0af55-103">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="0af55-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="0af55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0af55-104">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0af55-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0af55-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0af55-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0af55-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0af55-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="0af55-107">Attributes</span></span>  
 <span data-ttu-id="0af55-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0af55-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0af55-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0af55-109">Child Elements</span></span>  
  
|<span data-ttu-id="0af55-110">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="0af55-110">**Element**</span></span>|<span data-ttu-id="0af55-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="0af55-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0af55-112">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="0af55-112">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="0af55-113">Spécifie les modules utilisés pour authentifier les requêtes Internet.</span><span class="sxs-lookup"><span data-stu-id="0af55-113">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="0af55-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="0af55-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="0af55-115">Spécifie le nombre maximal de connexions à un hôte Internet.</span><span class="sxs-lookup"><span data-stu-id="0af55-115">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="0af55-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="0af55-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="0af55-117">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="0af55-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="0af55-118">mailSettings</span><span class="sxs-lookup"><span data-stu-id="0af55-118">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="0af55-119">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="0af55-119">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="0af55-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="0af55-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="0af55-121">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="0af55-121">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="0af55-122">settings</span><span class="sxs-lookup"><span data-stu-id="0af55-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="0af55-123">Configure les options réseau de base pour les classes dans les <xref:System.Net> espaces de noms enfants associés.</span><span class="sxs-lookup"><span data-stu-id="0af55-123">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="0af55-124">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="0af55-124">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="0af55-125">Spécifie les modules à utiliser pour demander des informations à partir d’hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="0af55-125">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0af55-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0af55-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0af55-127">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="0af55-127">**Element**</span></span>|<span data-ttu-id="0af55-128">**Description**</span><span class="sxs-lookup"><span data-stu-id="0af55-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0af55-129">configuration</span><span class="sxs-lookup"><span data-stu-id="0af55-129">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="0af55-130">Contient les paramètres de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="0af55-130">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0af55-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="0af55-131">Remarks</span></span>  
 <span data-ttu-id="0af55-132">L' [\<system.net>](system-net-element-network-settings.md) élément contient des paramètres pour les classes dans les <xref:System.Net> espaces de noms enfants associés.</span><span class="sxs-lookup"><span data-stu-id="0af55-132">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="0af55-133">Les paramètres configurent les modules d’authentification, la gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demande Internet pour la réception d’informations à partir d’hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="0af55-133">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0af55-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="0af55-134">Example</span></span>  
 <span data-ttu-id="0af55-135">L’exemple suivant montre une configuration classique utilisée par les <xref:System.Net> classes.</span><span class="sxs-lookup"><span data-stu-id="0af55-135">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0af55-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0af55-136">See also</span></span>

- [<span data-ttu-id="0af55-137">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="0af55-137">Network Settings Schema</span></span>](index.md)
