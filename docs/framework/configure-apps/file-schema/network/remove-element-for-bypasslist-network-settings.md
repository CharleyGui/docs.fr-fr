---
title: <remove>, élément de bypasslist (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697892"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="3a66a-102">\<remove>, élément de bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3a66a-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="3a66a-103">Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="3a66a-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="3a66a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a66a-104">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a66a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a66a-105">Attributes and Elements</span></span>

<span data-ttu-id="3a66a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a66a-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a66a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a66a-107">Attributes</span></span>

|<span data-ttu-id="3a66a-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="3a66a-108">**Attribute**</span></span>|<span data-ttu-id="3a66a-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="3a66a-109">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="3a66a-110">Expression régulière décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="3a66a-110">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3a66a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a66a-111">Child Elements</span></span>

<span data-ttu-id="3a66a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3a66a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a66a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a66a-113">Parent Elements</span></span>

|<span data-ttu-id="3a66a-114">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="3a66a-114">**Element**</span></span>|<span data-ttu-id="3a66a-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="3a66a-115">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="3a66a-116">BypassList</span><span class="sxs-lookup"><span data-stu-id="3a66a-116">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="3a66a-117">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="3a66a-117">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3a66a-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="3a66a-118">Remarks</span></span>

<span data-ttu-id="3a66a-119">L' `remove` élément supprime les expressions régulières décrivant des adresses IP ou des noms de serveurs DNS de la liste des adresses qui contournent un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="3a66a-119">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="3a66a-120">Les adresses ont été définies précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="3a66a-120">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="3a66a-121">La valeur de l' `address` attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôtes.</span><span class="sxs-lookup"><span data-stu-id="3a66a-121">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="3a66a-122">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3a66a-122">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="3a66a-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3a66a-123">Configuration Files</span></span>

<span data-ttu-id="3a66a-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3a66a-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="3a66a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a66a-125">Example</span></span>

<span data-ttu-id="3a66a-126">L’exemple suivant supprime toute définition précédente du domaine adventure-works.com, puis ajoute le domaine contoso.com à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="3a66a-126">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3a66a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a66a-127">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="3a66a-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3a66a-128">Network Settings Schema</span></span>](index.md)
