---
title: Configuration du proxy
description: En savoir plus sur la configuration des serveurs proxy adaptatifs et statiques. La configuration du proxy contrôle la manière dont un serveur proxy gère les demandes de ressources des clients.
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
ms.openlocfilehash: 5094a066fe6689a1c0cda227b284accaac49ad54
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263163"
---
# <a name="proxy-configuration"></a><span data-ttu-id="16c1e-104">Configuration du proxy</span><span class="sxs-lookup"><span data-stu-id="16c1e-104">Proxy Configuration</span></span>

<span data-ttu-id="16c1e-105">Un serveur proxy gère les demandes du client pour les ressources.</span><span class="sxs-lookup"><span data-stu-id="16c1e-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="16c1e-106">Un proxy peut retourner une ressource demandée à partir de son cache ou transférer la demande au serveur sur lequel réside la ressource.</span><span class="sxs-lookup"><span data-stu-id="16c1e-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="16c1e-107">Les proxies peuvent améliorer les performances réseau en réduisant le nombre de demandes envoyées aux serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="16c1e-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="16c1e-108">Les proxies peuvent également être utilisés pour restreindre l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="16c1e-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="16c1e-109">Proxies adaptatifs</span><span class="sxs-lookup"><span data-stu-id="16c1e-109">Adaptive Proxies</span></span>  

 <span data-ttu-id="16c1e-110">Dans le .NET Framework, les proxies sont fournis sous deux formes : adaptatifs et statiques.</span><span class="sxs-lookup"><span data-stu-id="16c1e-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="16c1e-111">Les proxies adaptatifs ajustent leurs paramètres lorsque la configuration du réseau change.</span><span class="sxs-lookup"><span data-stu-id="16c1e-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="16c1e-112">Par exemple, si l'utilisateur d'un ordinateur portable démarre une connexion réseau d'accès à distance, un proxy adaptatif identifie cette modification, détecte et exécute son nouveau script de configuration, et ajuste ses paramètres de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="16c1e-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="16c1e-113">Les proxys adaptatifs sont configurés par un script de configuration (voir [Détection automatique de proxy](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="16c1e-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="16c1e-114">Le script génère un ensemble de protocoles d'application et un proxy pour chaque protocole.</span><span class="sxs-lookup"><span data-stu-id="16c1e-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="16c1e-115">Les modifications apportées à l'environnement réseau peuvent nécessiter que le système utilise un nouvel ensemble de proxies.</span><span class="sxs-lookup"><span data-stu-id="16c1e-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="16c1e-116">En cas de défaillance d'une connexion réseau ou d'initialisation d'une nouvelle connexion réseau, le système doit détecter la source appropriée du script de configuration dans le nouvel environnement et exécuter le nouveau script.</span><span class="sxs-lookup"><span data-stu-id="16c1e-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="16c1e-117">Vous pouvez utiliser l' `usesystemdefault` attribut de l' [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) élément dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="16c1e-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="16c1e-118">L’attribut `usesystemdefault` détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus à partir des paramètres de proxy Internet Explorer de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="16c1e-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="16c1e-119">S’il a la valeur `true`, les paramètres de proxy statiques Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="16c1e-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="16c1e-120">S’il a la valeur `false` ou s’il n’est pas défini, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="16c1e-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="16c1e-121">En outre, cet attribut doit avoir la valeur `false` ou ne pas être défini pour que les proxys adaptatifs soient activés.</span><span class="sxs-lookup"><span data-stu-id="16c1e-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="16c1e-122">L'exemple suivant illustre une configuration de proxy adaptatif classique.</span><span class="sxs-lookup"><span data-stu-id="16c1e-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="16c1e-123">Proxies statiques</span><span class="sxs-lookup"><span data-stu-id="16c1e-123">Static Proxies</span></span>  

 <span data-ttu-id="16c1e-124">Les proxies statiques sont généralement configurés explicitement par une application, ou lorsqu'un fichier de configuration est appelé par une application ou le système.</span><span class="sxs-lookup"><span data-stu-id="16c1e-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="16c1e-125">Les proxies statiques sont utiles dans les réseaux dans lesquels la topologie change rarement, par exemple dans le cas d'un ordinateur de bureau connecté à un réseau d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="16c1e-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="16c1e-126">Plusieurs options déterminent le fonctionnement d'un proxy statique.</span><span class="sxs-lookup"><span data-stu-id="16c1e-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="16c1e-127">Spécifiez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="16c1e-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="16c1e-128">l'adresse du proxy ;</span><span class="sxs-lookup"><span data-stu-id="16c1e-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="16c1e-129">si le proxy doit être ignoré pour les adresses locales ;</span><span class="sxs-lookup"><span data-stu-id="16c1e-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="16c1e-130">si le proxy doit être ignoré pour un ensemble d'adresses donné.</span><span class="sxs-lookup"><span data-stu-id="16c1e-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="16c1e-131">Le tableau suivant présente les options de configuration d'un proxy statique.</span><span class="sxs-lookup"><span data-stu-id="16c1e-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="16c1e-132">Attribut, propriété ou paramètre de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="16c1e-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="16c1e-133">Description</span><span class="sxs-lookup"><span data-stu-id="16c1e-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="16c1e-134">`proxyaddress` ou <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="16c1e-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="16c1e-135">L'adresse du proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="16c1e-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="16c1e-136">`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="16c1e-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="16c1e-137">Détermine si le proxy est ignoré pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="16c1e-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="16c1e-138">`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="16c1e-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="16c1e-139">Décrit, avec des expressions régulières, un ensemble d'adresses qui ignorent le proxy.</span><span class="sxs-lookup"><span data-stu-id="16c1e-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="16c1e-140">Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="16c1e-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="16c1e-141">Si cet attribut à la valeur `true`, les paramètres de proxy statiques Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="16c1e-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="16c1e-142">Dans .NET Framework 2.0, quand cet attribut à la valeur `true`, les paramètres de proxy Internet Explorer ne sont pas remplacés par d’autres paramètres de proxy figurant dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="16c1e-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="16c1e-143">Sur .NET Framework 1.1, les paramètres de proxy Internet Explorer peuvent être substituées par d'autres paramètres de proxy figurant dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="16c1e-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="16c1e-144">Si cet attribut à la valeur `false` ou s’il n’est pas défini, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="16c1e-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="16c1e-145">En outre, cet attribut doit avoir la valeur `false` ou ne pas être défini pour que les proxys adaptatifs soient activés.</span><span class="sxs-lookup"><span data-stu-id="16c1e-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="16c1e-146">L'exemple suivant illustre une configuration de proxy statique classique.</span><span class="sxs-lookup"><span data-stu-id="16c1e-146">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16c1e-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16c1e-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="16c1e-148">Détection automatique de proxy</span><span class="sxs-lookup"><span data-stu-id="16c1e-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
