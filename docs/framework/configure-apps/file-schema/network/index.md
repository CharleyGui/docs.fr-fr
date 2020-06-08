---
title: Schéma des paramètres réseau
description: Découvrez le schéma des paramètres réseau qui spécifient la façon dont le .NET Framework se connecte à Internet et gère les URI.
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
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504574"
---
# <a name="network-settings-schema"></a><span data-ttu-id="6978d-103">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6978d-103">Network Settings Schema</span></span>
<span data-ttu-id="6978d-104">Les paramètres réseau spécifient la façon dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="6978d-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="6978d-105">Les \<system.net> paramètres spécifient la façon dont le .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="6978d-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="6978d-106">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous l' [ \<system.Net> élément (paramètres réseau)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6978d-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="6978d-107">Élément</span><span class="sxs-lookup"><span data-stu-id="6978d-107">Element</span></span>|<span data-ttu-id="6978d-108">Description</span><span class="sxs-lookup"><span data-stu-id="6978d-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6978d-109">\<authenticationModules>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6978d-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="6978d-110">Spécifie les modules utilisés pour authentifier les requêtes Internet.</span><span class="sxs-lookup"><span data-stu-id="6978d-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="6978d-111">\<connectionManagement>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6978d-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="6978d-112">Spécifie le nombre maximal de connexions à destination des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="6978d-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="6978d-113">\<defaultProxy>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6978d-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="6978d-114">Spécifie le serveur proxy utilisé pour les requêtes HTTP à destination d’Internet.</span><span class="sxs-lookup"><span data-stu-id="6978d-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="6978d-115">\<mailSettings>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6978d-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="6978d-116">Contient les paramètres des options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="6978d-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="6978d-117">\<requestCaching>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6978d-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="6978d-118">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="6978d-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="6978d-119">\<webRequestModules>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6978d-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="6978d-120">Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="6978d-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="6978d-121">Les \<uri> paramètres spécifient la façon dont le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="6978d-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="6978d-122">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous l' [ \<uri> élément (paramètres d’URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6978d-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="6978d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="6978d-123">Element</span></span>|<span data-ttu-id="6978d-124">Description</span><span class="sxs-lookup"><span data-stu-id="6978d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6978d-125">\<idn>, Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="6978d-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="6978d-126">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="6978d-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="6978d-127">\<iriParsing>, Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="6978d-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="6978d-128">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="6978d-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="6978d-129">\<schemeSettings>, Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="6978d-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="6978d-130">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="6978d-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6978d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6978d-131">See also</span></span>

- [<span data-ttu-id="6978d-132">Configuration des applications Internet</span><span class="sxs-lookup"><span data-stu-id="6978d-132">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="6978d-133">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="6978d-133">Configuration File Schema</span></span>](../index.md)
