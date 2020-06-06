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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088132"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="4098e-102">\<ipv6>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4098e-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="4098e-103">Active les réponses IPv6 (Internet Protocol version 6) à partir des membres obsolètes de la <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="4098e-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="4098e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4098e-104">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4098e-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4098e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4098e-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4098e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4098e-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="4098e-107">Attributes</span></span>  
  
|<span data-ttu-id="4098e-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="4098e-108">**Attribute**</span></span>|<span data-ttu-id="4098e-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="4098e-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="4098e-110">Spécifie si les membres de la <xref:System.Net.Dns> classe retournent des adresses IPv6 (Internet Protocol version 6).</span><span class="sxs-lookup"><span data-stu-id="4098e-110">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="4098e-111">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="4098e-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4098e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4098e-112">Child Elements</span></span>  
 <span data-ttu-id="4098e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4098e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4098e-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4098e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4098e-115">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="4098e-115">**Element**</span></span>|<span data-ttu-id="4098e-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="4098e-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4098e-117">settings</span><span class="sxs-lookup"><span data-stu-id="4098e-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="4098e-118">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="4098e-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4098e-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="4098e-119">Remarks</span></span>  
 <span data-ttu-id="4098e-120">Ce paramètre active la prise en charge IPv6 pour les membres obsolètes de la <xref:System.Net.Dns> classe :,,,,, <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Net.Dns.BeginResolve%2A> <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> et <xref:System.Net.Dns.Resolve%2A> .</span><span class="sxs-lookup"><span data-stu-id="4098e-120">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="4098e-121">Pour les autres membres de l' <xref:System.Net?displayProperty=nameWithType> espace de noms, des adresses IPv6 peuvent être retournées si IPv6 est activé dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4098e-121">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4098e-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4098e-122">Configuration Files</span></span>  
 <span data-ttu-id="4098e-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4098e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4098e-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="4098e-124">Example</span></span>  
 <span data-ttu-id="4098e-125">L’exemple suivant montre comment activer la prise en charge D’ipv6 pour la <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="4098e-125">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4098e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4098e-126">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4098e-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="4098e-127">Network Settings Schema</span></span>](index.md)
