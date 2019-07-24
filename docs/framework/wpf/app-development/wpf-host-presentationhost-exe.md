---
title: Hôte WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 16618042324387bfc15f4685f4759378c50a80b7
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401721"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="26c1e-102">Hôte WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="26c1e-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="26c1e-103">L’hôte Windows Presentation Foundation (WPF) (PresentationHost. exe) est l’application qui [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux applications d’être hébergées dans des navigateurs compatibles (y compris [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="26c1e-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="26c1e-104">Par défaut, l’hôte Windows Presentation Foundation (WPF) est inscrit en tant que [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Shell et gestionnaire pour le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] contenu hébergé par le navigateur, ce qui comprend les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="26c1e-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="26c1e-105">les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) libre (non compilés) ;</span><span class="sxs-lookup"><span data-stu-id="26c1e-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="26c1e-106">l’application [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).</span><span class="sxs-lookup"><span data-stu-id="26c1e-106">[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).</span></span>  
  
 <span data-ttu-id="26c1e-107">Pour les fichiers de ces types, Windows Presentation Foundation hôte (WPF):</span><span class="sxs-lookup"><span data-stu-id="26c1e-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="26c1e-108">Lance le gestionnaire [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] inscrit pour héberger le contenu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="26c1e-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="26c1e-109">Charge les versions appropriées des assemblys common language runtime (CLR) et Windows Presentation Foundation (WPF) requis.</span><span class="sxs-lookup"><span data-stu-id="26c1e-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="26c1e-110">vérifie la mise en place des niveaux d’autorisation appropriés pour la zone de déploiement.</span><span class="sxs-lookup"><span data-stu-id="26c1e-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="26c1e-111">Cette rubrique décrit les paramètres de ligne de commande qui peuvent être utilisés avec PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="26c1e-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="26c1e-112">Utilisation</span><span class="sxs-lookup"><span data-stu-id="26c1e-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="26c1e-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26c1e-113">Parameters</span></span>  
  
|<span data-ttu-id="26c1e-114">Paramètre</span><span class="sxs-lookup"><span data-stu-id="26c1e-114">Parameter</span></span>|<span data-ttu-id="26c1e-115">Description</span><span class="sxs-lookup"><span data-stu-id="26c1e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26c1e-116">filename</span><span class="sxs-lookup"><span data-stu-id="26c1e-116">filename</span></span>|<span data-ttu-id="26c1e-117">Chemin du fichier à activer.</span><span class="sxs-lookup"><span data-stu-id="26c1e-117">The path of the file to be activated.</span></span> <span data-ttu-id="26c1e-118">Il peut également s’agir d’un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26c1e-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="26c1e-119">-debug</span><span class="sxs-lookup"><span data-stu-id="26c1e-119">-debug</span></span>|<span data-ttu-id="26c1e-120">Au moment d’activer une application, n’effectue pas sa validation ou son exécution à partir du magasin.</span><span class="sxs-lookup"><span data-stu-id="26c1e-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="26c1e-121">Fonctionne uniquement quand un fichier local est activé.</span><span class="sxs-lookup"><span data-stu-id="26c1e-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="26c1e-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="26c1e-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="26c1e-123">Utilisé avec une valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour indiquer à PresentationHost.exe qu’une application doit être déboguée comme si elle était déployée à partir de la valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26c1e-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="26c1e-124">Cela permet de déterminer à la fois la zone de déploiement et le site d’origine.</span><span class="sxs-lookup"><span data-stu-id="26c1e-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="26c1e-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="26c1e-125">-embedding</span></span>|<span data-ttu-id="26c1e-126">Imposé par OLE.</span><span class="sxs-lookup"><span data-stu-id="26c1e-126">Required by OLE.</span></span> <span data-ttu-id="26c1e-127">Si le paramètre `-event` ou `-debug` est spécifié, il n’est pas nécessaire de spécifier le paramètre `-embedding`, car celui-ci est défini de façon interne.</span><span class="sxs-lookup"><span data-stu-id="26c1e-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="26c1e-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="26c1e-128">-event \<eventname></span></span>|<span data-ttu-id="26c1e-129">Ouvrez l’événement ayant ce nom, puis signalez-le quand PresentationHost.exe est initialisé et prêt à héberger le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26c1e-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="26c1e-130">PresentationHost.exe se termine si une erreur se produit à l’ouverture de l’événement, par exemple s’il n’a pas encore été créé.</span><span class="sxs-lookup"><span data-stu-id="26c1e-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="26c1e-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="26c1e-131">-launchApplication \<url></span></span>|<span data-ttu-id="26c1e-132">Lance une application ClickOnce autonome à partir de l’URL spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26c1e-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="26c1e-133">Les stratégies de sécurité [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] et WinINet relatives aux applications .NET sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="26c1e-133">[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="26c1e-134">Scénarios</span><span class="sxs-lookup"><span data-stu-id="26c1e-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="26c1e-135">Gestionnaire d’interpréteur de commandes</span><span class="sxs-lookup"><span data-stu-id="26c1e-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="26c1e-136">Gestionnaire MIME</span><span class="sxs-lookup"><span data-stu-id="26c1e-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="26c1e-137">Débogage Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26c1e-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="26c1e-138">Débogage Visual Studio dans la zone</span><span class="sxs-lookup"><span data-stu-id="26c1e-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="26c1e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26c1e-139">See also</span></span>

- [<span data-ttu-id="26c1e-140">Sécurité</span><span class="sxs-lookup"><span data-stu-id="26c1e-140">Security</span></span>](../security-wpf.md)
