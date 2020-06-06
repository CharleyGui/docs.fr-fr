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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698152"
---
# <a name="network-settings-schema"></a><span data-ttu-id="a6e79-102">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a6e79-102">Network Settings Schema</span></span>
<span data-ttu-id="a6e79-103">Les paramètres réseau spécifient la façon dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="a6e79-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="a6e79-104">Les \<system.net> paramètres spécifient la façon dont le .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="a6e79-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="a6e79-105">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous l' [ \<system.Net> élément (paramètres réseau)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a6e79-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="a6e79-106">Élément</span><span class="sxs-lookup"><span data-stu-id="a6e79-106">Element</span></span>|<span data-ttu-id="a6e79-107">Description</span><span class="sxs-lookup"><span data-stu-id="a6e79-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6e79-108">\<authenticationModules>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a6e79-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="a6e79-109">Spécifie les modules utilisés pour authentifier les requêtes Internet.</span><span class="sxs-lookup"><span data-stu-id="a6e79-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="a6e79-110">\<connectionManagement>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a6e79-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a6e79-111">Spécifie le nombre maximal de connexions à destination des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="a6e79-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="a6e79-112">\<defaultProxy>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a6e79-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a6e79-113">Spécifie le serveur proxy utilisé pour les requêtes HTTP à destination d’Internet.</span><span class="sxs-lookup"><span data-stu-id="a6e79-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="a6e79-114">\<mailSettings>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a6e79-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="a6e79-115">Contient les paramètres des options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="a6e79-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="a6e79-116">\<requestCaching>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a6e79-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="a6e79-117">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="a6e79-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="a6e79-118">\<webRequestModules>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a6e79-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="a6e79-119">Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="a6e79-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="a6e79-120">Les \<uri> paramètres spécifient la façon dont le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="a6e79-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="a6e79-121">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous l' [ \<uri> élément (paramètres d’URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a6e79-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="a6e79-122">Élément</span><span class="sxs-lookup"><span data-stu-id="a6e79-122">Element</span></span>|<span data-ttu-id="a6e79-123">Description</span><span class="sxs-lookup"><span data-stu-id="a6e79-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6e79-124">\<idn>, Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="a6e79-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="a6e79-125">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="a6e79-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="a6e79-126">\<iriParsing>, Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="a6e79-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="a6e79-127">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="a6e79-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="a6e79-128">\<schemeSettings>, Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="a6e79-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="a6e79-129">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a6e79-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6e79-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6e79-130">See also</span></span>

- [<span data-ttu-id="a6e79-131">Configuration des applications Internet</span><span class="sxs-lookup"><span data-stu-id="a6e79-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="a6e79-132">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a6e79-132">Configuration File Schema</span></span>](../index.md)
