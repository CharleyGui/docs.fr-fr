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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697892"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="140d8-102">\<supprimer > élément de bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="140d8-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="140d8-103">Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="140d8-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[<span data-ttu-id="140d8-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="140d8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="140d8-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="140d8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="140d8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy** >](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="140d8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="140d8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BypassList >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="140d8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="140d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**supprimer >**</span><span class="sxs-lookup"><span data-stu-id="140d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="140d8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="140d8-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="140d8-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="140d8-110">Attributes and Elements</span></span>

<span data-ttu-id="140d8-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="140d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="140d8-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="140d8-112">Attributes</span></span>

|<span data-ttu-id="140d8-113">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="140d8-113">**Attribute**</span></span>|<span data-ttu-id="140d8-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="140d8-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="140d8-115">Expression régulière décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="140d8-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="140d8-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="140d8-116">Child Elements</span></span>

<span data-ttu-id="140d8-117">Aucune.</span><span class="sxs-lookup"><span data-stu-id="140d8-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="140d8-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="140d8-118">Parent Elements</span></span>

|<span data-ttu-id="140d8-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="140d8-119">**Element**</span></span>|<span data-ttu-id="140d8-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="140d8-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="140d8-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="140d8-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="140d8-122">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="140d8-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="140d8-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="140d8-123">Remarks</span></span>

<span data-ttu-id="140d8-124">L’élément `remove` supprime les expressions régulières décrivant des adresses IP ou des noms de serveurs DNS de la liste des adresses qui contournent un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="140d8-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="140d8-125">Les adresses ont été définies précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="140d8-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="140d8-126">La valeur de l’attribut `address` doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôte.</span><span class="sxs-lookup"><span data-stu-id="140d8-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="140d8-127">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="140d8-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="140d8-128">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="140d8-128">Configuration Files</span></span>

<span data-ttu-id="140d8-129">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="140d8-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="140d8-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="140d8-130">Example</span></span>

<span data-ttu-id="140d8-131">L’exemple suivant supprime toute définition précédente du domaine adventure-works.com, puis ajoute le domaine contoso.com à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="140d8-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="140d8-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="140d8-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="140d8-133">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="140d8-133">Network Settings Schema</span></span>](index.md)
