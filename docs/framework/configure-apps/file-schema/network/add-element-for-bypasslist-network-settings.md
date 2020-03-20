---
title: <add>, élément de bypasslist (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155075"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="13f45-102">\<ajouter> Element pour la bypasslist (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="13f45-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="13f45-103">Ajoute une adresse IP ou un nom DNS à la liste de contournement par procuration.</span><span class="sxs-lookup"><span data-stu-id="13f45-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="13f45-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="13f45-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="13f45-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="13f45-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="13f45-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="13f45-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="13f45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de la liste de contournement**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="13f45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="13f45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="13f45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f45-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13f45-109">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13f45-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="13f45-110">Attributes and Elements</span></span>  
 <span data-ttu-id="13f45-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="13f45-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13f45-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="13f45-112">Attributes</span></span>  
  
|<span data-ttu-id="13f45-113">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="13f45-113">**Attribute**</span></span>|<span data-ttu-id="13f45-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="13f45-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="13f45-115">**Adresse**</span><span class="sxs-lookup"><span data-stu-id="13f45-115">**address**</span></span>|<span data-ttu-id="13f45-116">Une expression régulière décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="13f45-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13f45-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="13f45-117">Child Elements</span></span>  
 <span data-ttu-id="13f45-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="13f45-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13f45-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="13f45-119">Parent Elements</span></span>  
  
|<span data-ttu-id="13f45-120">**Élément**</span><span class="sxs-lookup"><span data-stu-id="13f45-120">**Element**</span></span>|<span data-ttu-id="13f45-121">**Description**</span><span class="sxs-lookup"><span data-stu-id="13f45-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="13f45-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="13f45-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="13f45-123">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas un proxy.</span><span class="sxs-lookup"><span data-stu-id="13f45-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13f45-124">Notes </span><span class="sxs-lookup"><span data-stu-id="13f45-124">Remarks</span></span>  
 <span data-ttu-id="13f45-125">L’élément `add` insère des expressions régulières décrivant les adresses IP ou les noms de serveur DNS à la liste des adresses qui contournent un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="13f45-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="13f45-126">La valeur `address` de l’attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôte.</span><span class="sxs-lookup"><span data-stu-id="13f45-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="13f45-127">Vous devez faire preuve de prudence lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="13f45-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="13f45-128">L’expression régulière "[a-z]md\\\\.contoso .com" correspond à n’importe quel hôte dans le domaine contoso.com, mais elle correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="13f45-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="13f45-129">Pour n’égaler qu’un hôte dans le domaine contoso.com, utilisez une ancre\\(«$») : « [a-z]md .contoso\\.com$.</span><span class="sxs-lookup"><span data-stu-id="13f45-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="13f45-130">Pour plus d’informations sur les expressions régulières, voir . [.NET Framework Expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="13f45-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="13f45-131">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="13f45-131">Configuration Files</span></span>  
 <span data-ttu-id="13f45-132">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="13f45-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f45-133"> Exemple</span><span class="sxs-lookup"><span data-stu-id="13f45-133">Example</span></span>  
 <span data-ttu-id="13f45-134">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="13f45-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="13f45-135">Le premier contourne le proxy pour tous les serveurs du domaine contoso.com ; le second contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192.168.</span><span class="sxs-lookup"><span data-stu-id="13f45-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13f45-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13f45-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="13f45-137">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="13f45-137">Network Settings Schema</span></span>](index.md)
