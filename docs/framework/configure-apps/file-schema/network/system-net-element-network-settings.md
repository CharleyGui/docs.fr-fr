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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154554"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="a2fa8-102">\<system.Net>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a2fa8-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="a2fa8-103">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="a2fa8-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="a2fa8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a2fa8-105">&nbsp;&nbsp;**\<system.net>**</span><span class="sxs-lookup"><span data-stu-id="a2fa8-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2fa8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2fa8-106">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2fa8-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a2fa8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a2fa8-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2fa8-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a2fa8-109">Attributes</span></span>  
 <span data-ttu-id="a2fa8-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2fa8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a2fa8-111">Child Elements</span></span>  
  
|<span data-ttu-id="a2fa8-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="a2fa8-112">**Element**</span></span>|<span data-ttu-id="a2fa8-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="a2fa8-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a2fa8-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a2fa8-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="a2fa8-115">Spécifie les modules utilisés pour authentifier les demandes Internet.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="a2fa8-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a2fa8-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a2fa8-117">Spécifie le nombre maximum de connexions à un hébergeur Internet.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="a2fa8-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a2fa8-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a2fa8-119">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="a2fa8-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="a2fa8-120">mailSettings (en)</span><span class="sxs-lookup"><span data-stu-id="a2fa8-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="a2fa8-121">Configure les options d’envoi de courrier simple par protocole de transport de courrier (SMTP).</span><span class="sxs-lookup"><span data-stu-id="a2fa8-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="a2fa8-122">demandeCaching</span><span class="sxs-lookup"><span data-stu-id="a2fa8-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="a2fa8-123">Contrôle le mécanisme de mise en cache des demandes de réseau.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="a2fa8-124">source de données</span><span class="sxs-lookup"><span data-stu-id="a2fa8-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a2fa8-125">Configure les options réseau de <xref:System.Net> base pour les classes dans les espaces nominaux pour enfants et les enfants apparentés.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="a2fa8-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="a2fa8-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="a2fa8-127">Spécifie les modules à utiliser pour demander des informations aux hébergeurs Internet.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2fa8-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a2fa8-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a2fa8-129">**Élément**</span><span class="sxs-lookup"><span data-stu-id="a2fa8-129">**Element**</span></span>|<span data-ttu-id="a2fa8-130">**Description**</span><span class="sxs-lookup"><span data-stu-id="a2fa8-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a2fa8-131">configuration</span><span class="sxs-lookup"><span data-stu-id="a2fa8-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="a2fa8-132">Contient des paramètres pour tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2fa8-133">Notes </span><span class="sxs-lookup"><span data-stu-id="a2fa8-133">Remarks</span></span>  
 <span data-ttu-id="a2fa8-134">[ \<L’élément system.net>](system-net-element-network-settings.md) contient des paramètres pour <xref:System.Net> les classes dans les espaces nominaux des enfants et connexes.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="a2fa8-135">Les paramètres configurent les modules d’authentification, la gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demande Internet pour recevoir des informations provenant d’hébergeurs Internet.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2fa8-136"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a2fa8-136">Example</span></span>  
 <span data-ttu-id="a2fa8-137">L’exemple suivant montre une <xref:System.Net> configuration typique utilisée par les classes.</span><span class="sxs-lookup"><span data-stu-id="a2fa8-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2fa8-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2fa8-138">See also</span></span>

- [<span data-ttu-id="a2fa8-139">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="a2fa8-139">Network Settings Schema</span></span>](index.md)
