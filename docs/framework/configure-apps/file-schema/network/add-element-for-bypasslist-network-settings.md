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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155075"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="5ae2c-102">\<add>, élément de bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5ae2c-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="5ae2c-103">Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5ae2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ae2c-104">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ae2c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ae2c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5ae2c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ae2c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ae2c-107">Attributes</span></span>  
  
|<span data-ttu-id="5ae2c-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="5ae2c-108">**Attribute**</span></span>|<span data-ttu-id="5ae2c-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="5ae2c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="5ae2c-110">**address**</span><span class="sxs-lookup"><span data-stu-id="5ae2c-110">**address**</span></span>|<span data-ttu-id="5ae2c-111">Expression régulière décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-111">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ae2c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ae2c-112">Child Elements</span></span>  
 <span data-ttu-id="5ae2c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ae2c-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ae2c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5ae2c-115">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="5ae2c-115">**Element**</span></span>|<span data-ttu-id="5ae2c-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="5ae2c-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5ae2c-117">BypassList</span><span class="sxs-lookup"><span data-stu-id="5ae2c-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="5ae2c-118">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ae2c-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ae2c-119">Remarks</span></span>  
 <span data-ttu-id="5ae2c-120">L' `add` élément insère des expressions régulières décrivant des adresses IP ou des noms de serveurs DNS à la liste des adresses qui contournent un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-120">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="5ae2c-121">La valeur de l' `address` attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôtes.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-121">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="5ae2c-122">Vous devez faire attention lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-122">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="5ae2c-123">L’expression régulière "[a-z] + \\ . contoso \\ . com" correspond à n’importe quel hôte dans le domaine contoso.com, mais correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-123">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="5ae2c-124">Pour correspondre uniquement à un hôte dans le domaine contoso.com, utilisez un point d’ancrage (« $ ») : « [a-z] + \\ . contoso \\ . com $ ».</span><span class="sxs-lookup"><span data-stu-id="5ae2c-124">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="5ae2c-125">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5ae2c-125">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5ae2c-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5ae2c-126">Configuration Files</span></span>  
 <span data-ttu-id="5ae2c-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5ae2c-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae2c-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="5ae2c-128">Example</span></span>  
 <span data-ttu-id="5ae2c-129">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-129">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="5ae2c-130">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192,168.</span><span class="sxs-lookup"><span data-stu-id="5ae2c-130">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ae2c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ae2c-131">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="5ae2c-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5ae2c-132">Network Settings Schema</span></span>](index.md)
