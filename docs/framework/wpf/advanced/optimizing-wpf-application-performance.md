---
title: Optimisation des performances des applications WPF
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 4724e6264c0108924629055525e46d84e86a6e6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953416"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="2e27d-102">Optimisation des performances des applications WPF</span><span class="sxs-lookup"><span data-stu-id="2e27d-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="2e27d-103">Cette section est destinée à servir de référence [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour les développeurs d’applications qui cherchent des moyens d’améliorer les performances de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="2e27d-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="2e27d-104">Si vous êtes un développeur qui est nouveau dans l’infrastructure Microsoft .net et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez d’abord vous familiariser avec les deux plateformes.</span><span class="sxs-lookup"><span data-stu-id="2e27d-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="2e27d-105">Cette section part du principe que vous connaissez les deux et que les programmeurs ont déjà suffisamment de connaissances pour faire fonctionner leurs applications.</span><span class="sxs-lookup"><span data-stu-id="2e27d-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e27d-106">Les données de performances fournies dans cette section sont basées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur des applications qui s’exécutent sur un PC 2,8 GHz avec 512 de RAM et une carte graphique ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="2e27d-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e27d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2e27d-107">In This Section</span></span>  
 [<span data-ttu-id="2e27d-108">Planification des performances des applications</span><span class="sxs-lookup"><span data-stu-id="2e27d-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="2e27d-109">Tirer parti du matériel</span><span class="sxs-lookup"><span data-stu-id="2e27d-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="2e27d-110">Disposition et conception</span><span class="sxs-lookup"><span data-stu-id="2e27d-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="2e27d-111">Graphiques 2D et acquisition d'images</span><span class="sxs-lookup"><span data-stu-id="2e27d-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="2e27d-112">Comportement de l’objet</span><span class="sxs-lookup"><span data-stu-id="2e27d-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="2e27d-113">Ressources d'application</span><span class="sxs-lookup"><span data-stu-id="2e27d-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="2e27d-114">Text</span><span class="sxs-lookup"><span data-stu-id="2e27d-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="2e27d-115">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="2e27d-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="2e27d-116">Contrôles</span><span class="sxs-lookup"><span data-stu-id="2e27d-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="2e27d-117">Autres recommandations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="2e27d-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="2e27d-118">Temps de démarrage d’une application</span><span class="sxs-lookup"><span data-stu-id="2e27d-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e27d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e27d-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="2e27d-120">Couches de rendu graphiques</span><span class="sxs-lookup"><span data-stu-id="2e27d-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="2e27d-121">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="2e27d-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="2e27d-122">Disposition</span><span class="sxs-lookup"><span data-stu-id="2e27d-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="2e27d-123">Arborescences dans WPF</span><span class="sxs-lookup"><span data-stu-id="2e27d-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="2e27d-124">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="2e27d-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="2e27d-125">Utilisation d’objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="2e27d-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="2e27d-126">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="2e27d-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="2e27d-127">Vue d’ensemble des objets Freezable</span><span class="sxs-lookup"><span data-stu-id="2e27d-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="2e27d-128">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="2e27d-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="2e27d-129">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="2e27d-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="2e27d-130">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="2e27d-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="2e27d-131">Typographie dans WPF</span><span class="sxs-lookup"><span data-stu-id="2e27d-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="2e27d-132">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="2e27d-132">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="2e27d-133">Vue d’ensemble de la navigation</span><span class="sxs-lookup"><span data-stu-id="2e27d-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="2e27d-134">Conseils et astuces sur les animations</span><span class="sxs-lookup"><span data-stu-id="2e27d-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="2e27d-135">Procédure pas à pas : Mise en cache des données d’application dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="2e27d-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
