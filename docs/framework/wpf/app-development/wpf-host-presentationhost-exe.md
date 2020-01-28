---
title: Hôte WPF (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743401"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="9caac-102">Hôte WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="9caac-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="9caac-103">L’hôte Windows Presentation Foundation (WPF) (PresentationHost. exe) est l’application qui permet aux applications WPF d’être hébergées dans des navigateurs compatibles (y compris Microsoft Internet Explorer 6 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="9caac-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="9caac-104">Par défaut, l’hôte Windows Presentation Foundation (WPF) est inscrit en tant que gestionnaire de Shell et de MIME pour le contenu WPF hébergé par le navigateur, ce qui comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9caac-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="9caac-105">les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) libre (non compilés) ;</span><span class="sxs-lookup"><span data-stu-id="9caac-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="9caac-106">Application du navigateur XAML (XBAP) (. XBAP).</span><span class="sxs-lookup"><span data-stu-id="9caac-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="9caac-107">Pour les fichiers de ces types, Windows Presentation Foundation hôte (WPF) :</span><span class="sxs-lookup"><span data-stu-id="9caac-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="9caac-108">Lance le gestionnaire HTML inscrit pour héberger le contenu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="9caac-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="9caac-109">Charge les versions appropriées des assemblys common language runtime (CLR) et Windows Presentation Foundation (WPF) requis.</span><span class="sxs-lookup"><span data-stu-id="9caac-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="9caac-110">vérifie la mise en place des niveaux d’autorisation appropriés pour la zone de déploiement.</span><span class="sxs-lookup"><span data-stu-id="9caac-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="9caac-111">Cette rubrique décrit les paramètres de ligne de commande qui peuvent être utilisés avec PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="9caac-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="9caac-112">Contrôle</span><span class="sxs-lookup"><span data-stu-id="9caac-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="9caac-113">Parameters</span><span class="sxs-lookup"><span data-stu-id="9caac-113">Parameters</span></span>  
  
|<span data-ttu-id="9caac-114">Paramètre</span><span class="sxs-lookup"><span data-stu-id="9caac-114">Parameter</span></span>|<span data-ttu-id="9caac-115">Description</span><span class="sxs-lookup"><span data-stu-id="9caac-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9caac-116">Nom de fichier</span><span class="sxs-lookup"><span data-stu-id="9caac-116">filename</span></span>|<span data-ttu-id="9caac-117">Chemin du fichier à activer.</span><span class="sxs-lookup"><span data-stu-id="9caac-117">The path of the file to be activated.</span></span> <span data-ttu-id="9caac-118">Peut également être un URI.</span><span class="sxs-lookup"><span data-stu-id="9caac-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="9caac-119">-debug</span><span class="sxs-lookup"><span data-stu-id="9caac-119">-debug</span></span>|<span data-ttu-id="9caac-120">Au moment d’activer une application, n’effectue pas sa validation ou son exécution à partir du magasin.</span><span class="sxs-lookup"><span data-stu-id="9caac-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="9caac-121">Fonctionne uniquement quand un fichier local est activé.</span><span class="sxs-lookup"><span data-stu-id="9caac-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="9caac-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="9caac-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="9caac-123">Utilisé avec une valeur d’URL pour indiquer à PresentationHost. exe qu’une application doit être déboguée comme si elle était déployée à partir de l’URL spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9caac-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="9caac-124">Cela permet de déterminer à la fois la zone de déploiement et le site d’origine.</span><span class="sxs-lookup"><span data-stu-id="9caac-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="9caac-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="9caac-125">-embedding</span></span>|<span data-ttu-id="9caac-126">Imposé par OLE.</span><span class="sxs-lookup"><span data-stu-id="9caac-126">Required by OLE.</span></span> <span data-ttu-id="9caac-127">Si le paramètre `-event` ou `-debug` est spécifié, il n’est pas nécessaire de spécifier le paramètre `-embedding`, car celui-ci est défini de façon interne.</span><span class="sxs-lookup"><span data-stu-id="9caac-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="9caac-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="9caac-128">-event \<eventname></span></span>|<span data-ttu-id="9caac-129">Ouvrez l’événement portant ce nom et signalez-le quand PresentationHost. exe est initialisé et prêt à héberger du contenu WPF.</span><span class="sxs-lookup"><span data-stu-id="9caac-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="9caac-130">PresentationHost.exe se termine si une erreur se produit à l’ouverture de l’événement, par exemple s’il n’a pas encore été créé.</span><span class="sxs-lookup"><span data-stu-id="9caac-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="9caac-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="9caac-131">-launchApplication \<url></span></span>|<span data-ttu-id="9caac-132">Lance une application ClickOnce autonome à partir de l’URL spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9caac-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="9caac-133">La stratégie de sécurité Internet Explorer et WinINet concernant les applications .NET sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="9caac-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="9caac-134">Scénarios</span><span class="sxs-lookup"><span data-stu-id="9caac-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="9caac-135">Gestionnaire d’interpréteur de commandes</span><span class="sxs-lookup"><span data-stu-id="9caac-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="9caac-136">Gestionnaire MIME</span><span class="sxs-lookup"><span data-stu-id="9caac-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="9caac-137">Débogage Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9caac-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="9caac-138">Débogage Visual Studio dans la zone</span><span class="sxs-lookup"><span data-stu-id="9caac-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="9caac-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9caac-139">See also</span></span>

- [<span data-ttu-id="9caac-140">Security</span><span class="sxs-lookup"><span data-stu-id="9caac-140">Security</span></span>](../security-wpf.md)
