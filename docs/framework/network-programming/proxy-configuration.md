---
title: Configuration du proxy
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047358"
---
# <a name="proxy-configuration"></a><span data-ttu-id="8c97c-102">Configuration du proxy</span><span class="sxs-lookup"><span data-stu-id="8c97c-102">Proxy Configuration</span></span>
<span data-ttu-id="8c97c-103">Un serveur proxy gère les demandes du client pour les ressources.</span><span class="sxs-lookup"><span data-stu-id="8c97c-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="8c97c-104">Un proxy peut retourner une ressource demandée à partir de son cache ou transférer la demande au serveur sur lequel réside la ressource.</span><span class="sxs-lookup"><span data-stu-id="8c97c-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="8c97c-105">Les proxies peuvent améliorer les performances réseau en réduisant le nombre de demandes envoyées aux serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="8c97c-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="8c97c-106">Les proxies peuvent également être utilisés pour restreindre l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="8c97c-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="8c97c-107">Proxies adaptatifs</span><span class="sxs-lookup"><span data-stu-id="8c97c-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="8c97c-108">Dans le .NET Framework, les proxies sont fournis sous deux formes : adaptatifs et statiques.</span><span class="sxs-lookup"><span data-stu-id="8c97c-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="8c97c-109">Les proxies adaptatifs ajustent leurs paramètres lorsque la configuration du réseau change.</span><span class="sxs-lookup"><span data-stu-id="8c97c-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="8c97c-110">Par exemple, si l'utilisateur d'un ordinateur portable démarre une connexion réseau d'accès à distance, un proxy adaptatif identifie cette modification, détecte et exécute son nouveau script de configuration, et ajuste ses paramètres de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="8c97c-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="8c97c-111">Les proxys adaptatifs sont configurés par un script de configuration (voir [Détection automatique de proxy](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="8c97c-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="8c97c-112">Le script génère un ensemble de protocoles d'application et un proxy pour chaque protocole.</span><span class="sxs-lookup"><span data-stu-id="8c97c-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="8c97c-113">Les modifications apportées à l'environnement réseau peuvent nécessiter que le système utilise un nouvel ensemble de proxies.</span><span class="sxs-lookup"><span data-stu-id="8c97c-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="8c97c-114">En cas de défaillance d'une connexion réseau ou d'initialisation d'une nouvelle connexion réseau, le système doit détecter la source appropriée du script de configuration dans le nouvel environnement et exécuter le nouveau script.</span><span class="sxs-lookup"><span data-stu-id="8c97c-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="8c97c-115">Vous pouvez `usesystemdefault` utiliser l’attribut de l’élément [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c97c-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="8c97c-116">L’attribut `usesystemdefault` détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus à partir des paramètres de proxy Internet Explorer de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c97c-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="8c97c-117">S’il a la valeur `true`, les paramètres de proxy statiques Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="8c97c-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8c97c-118">S’il a la valeur `false` ou s’il n’est pas défini, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8c97c-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="8c97c-119">En outre, cet attribut doit avoir la valeur `false` ou ne pas être défini pour que les proxys adaptatifs soient activés.</span><span class="sxs-lookup"><span data-stu-id="8c97c-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="8c97c-120">L'exemple suivant illustre une configuration de proxy adaptatif classique.</span><span class="sxs-lookup"><span data-stu-id="8c97c-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="8c97c-121">Proxies statiques</span><span class="sxs-lookup"><span data-stu-id="8c97c-121">Static Proxies</span></span>  
 <span data-ttu-id="8c97c-122">Les proxies statiques sont généralement configurés explicitement par une application, ou lorsqu'un fichier de configuration est appelé par une application ou le système.</span><span class="sxs-lookup"><span data-stu-id="8c97c-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="8c97c-123">Les proxies statiques sont utiles dans les réseaux dans lesquels la topologie change rarement, par exemple dans le cas d'un ordinateur de bureau connecté à un réseau d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="8c97c-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="8c97c-124">Plusieurs options déterminent le fonctionnement d'un proxy statique.</span><span class="sxs-lookup"><span data-stu-id="8c97c-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="8c97c-125">Spécifiez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c97c-125">You can specify the following:</span></span>  
  
- <span data-ttu-id="8c97c-126">l'adresse du proxy ;</span><span class="sxs-lookup"><span data-stu-id="8c97c-126">The address of the proxy.</span></span>  
  
- <span data-ttu-id="8c97c-127">si le proxy doit être ignoré pour les adresses locales ;</span><span class="sxs-lookup"><span data-stu-id="8c97c-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="8c97c-128">si le proxy doit être ignoré pour un ensemble d'adresses donné.</span><span class="sxs-lookup"><span data-stu-id="8c97c-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="8c97c-129">Le tableau suivant présente les options de configuration d'un proxy statique.</span><span class="sxs-lookup"><span data-stu-id="8c97c-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="8c97c-130">Attribut, propriété ou paramètre de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="8c97c-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="8c97c-131">Description</span><span class="sxs-lookup"><span data-stu-id="8c97c-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="8c97c-132">`proxyaddress` ou <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="8c97c-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="8c97c-133">L'adresse du proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8c97c-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="8c97c-134">`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="8c97c-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="8c97c-135">Détermine si le proxy est ignoré pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="8c97c-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="8c97c-136">`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="8c97c-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="8c97c-137">Décrit, avec des expressions régulières, un ensemble d'adresses qui ignorent le proxy.</span><span class="sxs-lookup"><span data-stu-id="8c97c-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="8c97c-138">Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c97c-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="8c97c-139">Si cet attribut à la valeur `true`, les paramètres de proxy statiques Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="8c97c-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8c97c-140">Dans .NET Framework 2.0, quand cet attribut à la valeur `true`, les paramètres de proxy Internet Explorer ne sont pas remplacés par d’autres paramètres de proxy figurant dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c97c-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="8c97c-141">Sur .NET Framework 1.1, les paramètres de proxy Internet Explorer peuvent être substituées par d'autres paramètres de proxy figurant dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c97c-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="8c97c-142">Si cet attribut à la valeur `false` ou s’il n’est pas défini, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8c97c-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="8c97c-143">En outre, cet attribut doit avoir la valeur `false` ou ne pas être défini pour que les proxys adaptatifs soient activés.</span><span class="sxs-lookup"><span data-stu-id="8c97c-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="8c97c-144">L'exemple suivant illustre une configuration de proxy statique classique.</span><span class="sxs-lookup"><span data-stu-id="8c97c-144">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c97c-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c97c-145">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="8c97c-146">Détection automatique de proxy</span><span class="sxs-lookup"><span data-stu-id="8c97c-146">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
