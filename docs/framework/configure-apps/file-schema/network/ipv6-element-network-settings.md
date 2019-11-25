---
title: <ipv6>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: c16949171d082bd02abb0a02db83c2e71c2f17df
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088132"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="3472e-102">\<ipv6>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3472e-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="3472e-103">Active les réponses IPv6 (Internet Protocol version 6) à partir des membres obsolètes de la classe <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="3472e-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

<span data-ttu-id="3472e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3472e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3472e-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3472e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3472e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<</span><span class="sxs-lookup"><span data-stu-id="3472e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="3472e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**ipv6 >**</span><span class="sxs-lookup"><span data-stu-id="3472e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3472e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3472e-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3472e-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3472e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3472e-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3472e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3472e-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3472e-111">Attributes</span></span>  
  
|<span data-ttu-id="3472e-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="3472e-112">**Attribute**</span></span>|<span data-ttu-id="3472e-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="3472e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="3472e-114">Spécifie si les membres de la classe <xref:System.Net.Dns> retournent des adresses IPv6 (Internet Protocol version 6).</span><span class="sxs-lookup"><span data-stu-id="3472e-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="3472e-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="3472e-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3472e-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3472e-116">Child Elements</span></span>  
 <span data-ttu-id="3472e-117">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="3472e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3472e-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3472e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3472e-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="3472e-119">**Element**</span></span>|<span data-ttu-id="3472e-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="3472e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3472e-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3472e-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3472e-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="3472e-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3472e-123">Notes</span><span class="sxs-lookup"><span data-stu-id="3472e-123">Remarks</span></span>  
 <span data-ttu-id="3472e-124">Ce paramètre active la prise en charge D’ipv6 pour les membres obsolètes de la classe <xref:System.Net.Dns> : <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>et <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="3472e-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="3472e-125">Pour les autres membres de l’espace de noms <xref:System.Net?displayProperty=nameWithType>, des adresses IPv6 peuvent être retournées si IPv6 est activé dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3472e-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3472e-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3472e-126">Configuration Files</span></span>  
 <span data-ttu-id="3472e-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3472e-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3472e-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="3472e-128">Example</span></span>  
 <span data-ttu-id="3472e-129">L’exemple suivant montre comment activer la prise en charge D’ipv6 pour la classe <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="3472e-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3472e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3472e-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3472e-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3472e-131">Network Settings Schema</span></span>](index.md)
