---
title: Schéma des paramètres réseau
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664106"
---
# <a name="network-settings-schema"></a><span data-ttu-id="4af43-102">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="4af43-102">Network Settings Schema</span></span>
<span data-ttu-id="4af43-103">Les paramètres réseau spécifient la façon dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="4af43-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="4af43-104">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous [\<system.Net>, élément (paramètres réseau)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4af43-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="4af43-105">Élément</span><span class="sxs-lookup"><span data-stu-id="4af43-105">Element</span></span>|<span data-ttu-id="4af43-106">Description</span><span class="sxs-lookup"><span data-stu-id="4af43-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4af43-107">\<authenticationModules, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4af43-107">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4af43-108">Spécifie les modules utilisés pour authentifier les requêtes Internet.</span><span class="sxs-lookup"><span data-stu-id="4af43-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="4af43-109">\<connectionManagement>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4af43-109">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="4af43-110">Spécifie le nombre maximal de connexions à destination des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="4af43-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="4af43-111">\<defaultProxy>, élément(paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4af43-111">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="4af43-112">Spécifie le serveur proxy utilisé pour les requêtes HTTP à destination d’Internet.</span><span class="sxs-lookup"><span data-stu-id="4af43-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="4af43-113">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4af43-113">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="4af43-114">Contient les paramètres des options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="4af43-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="4af43-115">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4af43-115">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="4af43-116">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="4af43-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="4af43-117">\<webRequestModules>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4af43-117">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="4af43-118">Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="4af43-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="4af43-119">Les paramètres d’URI spécifient la façon dont le .NET Framework gère les adresses web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="4af43-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="4af43-120">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous [\<Uri>, élément (paramètres d’Uri)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4af43-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="4af43-121">Élément</span><span class="sxs-lookup"><span data-stu-id="4af43-121">Element</span></span>|<span data-ttu-id="4af43-122">Description</span><span class="sxs-lookup"><span data-stu-id="4af43-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4af43-123">\<idn>, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="4af43-123">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="4af43-124">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="4af43-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="4af43-125">\<iriParsing>, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="4af43-125">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="4af43-126">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="4af43-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="4af43-127">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="4af43-127">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="4af43-128">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4af43-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4af43-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4af43-129">See also</span></span>

- [<span data-ttu-id="4af43-130">Configuration des applications Internet</span><span class="sxs-lookup"><span data-stu-id="4af43-130">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="4af43-131">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4af43-131">Configuration File Schema</span></span>](../index.md)
