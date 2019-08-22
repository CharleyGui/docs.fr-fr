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
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664097"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="7b6ab-102">\<ipv6>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7b6ab-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="7b6ab-103">Active les réponses IPv6 (Internet Protocol version 6) à partir des membres <xref:System.Net.Dns> obsolètes de la classe.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="7b6ab-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7b6ab-104">\<configuration></span></span>  
<span data-ttu-id="7b6ab-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="7b6ab-105">\<system.net></span></span>  
<span data-ttu-id="7b6ab-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="7b6ab-106">\<settings></span></span>  
<span data-ttu-id="7b6ab-107">\<ipv6></span><span class="sxs-lookup"><span data-stu-id="7b6ab-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b6ab-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b6ab-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b6ab-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7b6ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7b6ab-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b6ab-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="7b6ab-111">Attributes</span></span>  
  
|<span data-ttu-id="7b6ab-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="7b6ab-112">**Attribute**</span></span>|<span data-ttu-id="7b6ab-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="7b6ab-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="7b6ab-114">Spécifie si les membres <xref:System.Net.Dns> de la classe retournent des adresses IPv6 (Internet Protocol version 6).</span><span class="sxs-lookup"><span data-stu-id="7b6ab-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="7b6ab-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b6ab-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7b6ab-116">Child Elements</span></span>  
 <span data-ttu-id="7b6ab-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b6ab-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7b6ab-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7b6ab-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="7b6ab-119">**Element**</span></span>|<span data-ttu-id="7b6ab-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="7b6ab-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7b6ab-121">settings</span><span class="sxs-lookup"><span data-stu-id="7b6ab-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7b6ab-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b6ab-123">Notes</span><span class="sxs-lookup"><span data-stu-id="7b6ab-123">Remarks</span></span>  
 <span data-ttu-id="7b6ab-124">Ce paramètre active la prise en charge IPv6 pour les membres <xref:System.Net.Dns> obsolètes de la classe <xref:System.Net.Dns.EndResolve%2A>: <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.Resolve%2A> <xref:System.Net.Dns.GetHostByName%2A> <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>,,, et.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="7b6ab-125">Pour les autres membres de <xref:System.Net?displayProperty=nameWithType> l’espace de noms, des adresses IPv6 peuvent être retournées si IPv6 est activé dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7b6ab-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7b6ab-126">Configuration Files</span></span>  
 <span data-ttu-id="7b6ab-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7b6ab-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b6ab-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="7b6ab-128">Example</span></span>  
 <span data-ttu-id="7b6ab-129">L’exemple suivant montre comment activer la prise en charge d’IPv6 <xref:System.Net.Dns> pour la classe.</span><span class="sxs-lookup"><span data-stu-id="7b6ab-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b6ab-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b6ab-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7b6ab-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="7b6ab-131">Network Settings Schema</span></span>](index.md)
