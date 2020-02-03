---
title: Optimiser les performances de l’application
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: cc6ea051401199a87965565c920068fd55cb05d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743948"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="3de3a-102">Optimisation des performances des applications WPF</span><span class="sxs-lookup"><span data-stu-id="3de3a-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="3de3a-103">Cette section est destinée à servir de référence pour les développeurs d’applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] qui cherchent des moyens d’améliorer les performances de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="3de3a-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="3de3a-104">Si vous êtes un développeur qui est nouveau dans l’infrastructure Microsoft .NET et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez d’abord vous familiariser avec les deux plateformes.</span><span class="sxs-lookup"><span data-stu-id="3de3a-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="3de3a-105">Cette section part du principe que vous connaissez les deux et que les programmeurs ont déjà suffisamment de connaissances pour faire fonctionner leurs applications.</span><span class="sxs-lookup"><span data-stu-id="3de3a-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3de3a-106">Les données de performances fournies dans cette section sont basées sur des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s’exécutant sur un PC 2,8 GHz avec 512 de RAM et une carte graphique ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="3de3a-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3de3a-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3de3a-107">In This Section</span></span>  
 [<span data-ttu-id="3de3a-108">Planification des performances des applications</span><span class="sxs-lookup"><span data-stu-id="3de3a-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="3de3a-109">Tirer parti du matériel</span><span class="sxs-lookup"><span data-stu-id="3de3a-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="3de3a-110">Disposition et conception</span><span class="sxs-lookup"><span data-stu-id="3de3a-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="3de3a-111">Graphiques 2D et acquisition d'images</span><span class="sxs-lookup"><span data-stu-id="3de3a-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="3de3a-112">Comportement de l’objet</span><span class="sxs-lookup"><span data-stu-id="3de3a-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="3de3a-113">Ressources d'application</span><span class="sxs-lookup"><span data-stu-id="3de3a-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="3de3a-114">Text</span><span class="sxs-lookup"><span data-stu-id="3de3a-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="3de3a-115">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="3de3a-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="3de3a-116">Contrôles</span><span class="sxs-lookup"><span data-stu-id="3de3a-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="3de3a-117">Autres recommandations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="3de3a-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="3de3a-118">Temps de démarrage d’une application</span><span class="sxs-lookup"><span data-stu-id="3de3a-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="3de3a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3de3a-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="3de3a-120">Couches de rendu graphiques</span><span class="sxs-lookup"><span data-stu-id="3de3a-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="3de3a-121">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="3de3a-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="3de3a-122">Disposition</span><span class="sxs-lookup"><span data-stu-id="3de3a-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="3de3a-123">Arborescences dans WPF</span><span class="sxs-lookup"><span data-stu-id="3de3a-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="3de3a-124">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="3de3a-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="3de3a-125">Utilisation d’objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="3de3a-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="3de3a-126">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="3de3a-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="3de3a-127">Vue d’ensemble des objets Freezable</span><span class="sxs-lookup"><span data-stu-id="3de3a-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="3de3a-128">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="3de3a-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="3de3a-129">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="3de3a-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="3de3a-130">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="3de3a-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="3de3a-131">Typographie dans WPF</span><span class="sxs-lookup"><span data-stu-id="3de3a-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="3de3a-132">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="3de3a-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3de3a-133">Vue d’ensemble de la navigation</span><span class="sxs-lookup"><span data-stu-id="3de3a-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="3de3a-134">Conseils et astuces sur les animations</span><span class="sxs-lookup"><span data-stu-id="3de3a-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="3de3a-135">Procédure pas à pas : mise en cache de données d’application dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="3de3a-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
