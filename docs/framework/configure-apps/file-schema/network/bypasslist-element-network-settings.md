---
title: <bypasslist>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154944"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="18ac5-102">\<bypasslist>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="18ac5-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="18ac5-103">Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.</span><span class="sxs-lookup"><span data-stu-id="18ac5-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="18ac5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18ac5-104">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18ac5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="18ac5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="18ac5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="18ac5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18ac5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="18ac5-107">Attributes</span></span>  
 <span data-ttu-id="18ac5-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="18ac5-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18ac5-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="18ac5-109">Child Elements</span></span>  
  
|<span data-ttu-id="18ac5-110">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="18ac5-110">**Element**</span></span>|<span data-ttu-id="18ac5-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="18ac5-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="18ac5-112">add</span><span class="sxs-lookup"><span data-stu-id="18ac5-112">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="18ac5-113">Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="18ac5-113">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="18ac5-114">clear</span><span class="sxs-lookup"><span data-stu-id="18ac5-114">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="18ac5-115">Efface la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="18ac5-115">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="18ac5-116">remove</span><span class="sxs-lookup"><span data-stu-id="18ac5-116">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="18ac5-117">Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="18ac5-117">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18ac5-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="18ac5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="18ac5-119">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="18ac5-119">**Element**</span></span>|<span data-ttu-id="18ac5-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="18ac5-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="18ac5-121">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="18ac5-121">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="18ac5-122">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="18ac5-122">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18ac5-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="18ac5-123">Remarks</span></span>  
 <span data-ttu-id="18ac5-124">La liste de contournement contient des expressions régulières qui décrivent les URI qui <xref:System.Net.WebRequest> excèdent directement l’accès au serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="18ac5-124">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="18ac5-125">Vous devez faire attention lorsque vous spécifiez une expression régulière pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="18ac5-125">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="18ac5-126">L’expression régulière "[a-z] + \\ . contoso \\ . com" correspond à n’importe quel hôte dans le domaine contoso.com, mais correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="18ac5-126">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="18ac5-127">Pour correspondre uniquement à un hôte dans le domaine contoso.com, utilisez un point d’ancrage (« $ ») : « [a-z] + \\ . contoso \\ . com $ ».</span><span class="sxs-lookup"><span data-stu-id="18ac5-127">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="18ac5-128">Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="18ac5-128">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="18ac5-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="18ac5-129">Configuration Files</span></span>  
 <span data-ttu-id="18ac5-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="18ac5-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ac5-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="18ac5-131">Example</span></span>  
 <span data-ttu-id="18ac5-132">L’exemple suivant ajoute deux adresses à la liste de contournement.</span><span class="sxs-lookup"><span data-stu-id="18ac5-132">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="18ac5-133">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192,168.</span><span class="sxs-lookup"><span data-stu-id="18ac5-133">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18ac5-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18ac5-134">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="18ac5-135">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="18ac5-135">Network Settings Schema</span></span>](index.md)
