---
title: Optimiser les performances de l’application
description: Utilisez ces ressources pour améliorer les performances des applications Windows Presentation Foundation, telles que la planification des performances et la mise à profit du matériel.
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166325"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="a1746-103">Optimisation des performances des applications WPF</span><span class="sxs-lookup"><span data-stu-id="a1746-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="a1746-104">Cette section est destinée à servir de référence pour les [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] développeurs d’applications qui cherchent des moyens d’améliorer les performances de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="a1746-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="a1746-105">Si vous êtes un développeur qui est nouveau dans l’infrastructure Microsoft .NET et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , vous devez d’abord vous familiariser avec les deux plateformes.</span><span class="sxs-lookup"><span data-stu-id="a1746-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="a1746-106">Cette section part du principe que vous connaissez les deux et que les programmeurs ont déjà suffisamment de connaissances pour faire fonctionner leurs applications.</span><span class="sxs-lookup"><span data-stu-id="a1746-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1746-107">Les données de performances fournies dans cette section sont basées sur des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications qui s’exécutent sur un PC 2,8 GHz avec 512 de RAM et une carte graphique ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="a1746-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1746-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a1746-108">In This Section</span></span>  
 [<span data-ttu-id="a1746-109">Planification des performances des applications</span><span class="sxs-lookup"><span data-stu-id="a1746-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="a1746-110">Tirer parti du matériel</span><span class="sxs-lookup"><span data-stu-id="a1746-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="a1746-111">Disposition et conception</span><span class="sxs-lookup"><span data-stu-id="a1746-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="a1746-112">Graphisme 2D et acquisition d’images</span><span class="sxs-lookup"><span data-stu-id="a1746-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="a1746-113">Comportement de l’objet</span><span class="sxs-lookup"><span data-stu-id="a1746-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="a1746-114">Ressources d’application</span><span class="sxs-lookup"><span data-stu-id="a1746-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="a1746-115">Text</span><span class="sxs-lookup"><span data-stu-id="a1746-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="a1746-116">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="a1746-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="a1746-117">Contrôles</span><span class="sxs-lookup"><span data-stu-id="a1746-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="a1746-118">Autres recommandations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="a1746-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="a1746-119">Temps de démarrage d'une application</span><span class="sxs-lookup"><span data-stu-id="a1746-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="a1746-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1746-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="a1746-121">Couches de rendu graphiques</span><span class="sxs-lookup"><span data-stu-id="a1746-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="a1746-122">Vue d'ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="a1746-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="a1746-123">Disposition</span><span class="sxs-lookup"><span data-stu-id="a1746-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="a1746-124">Arborescences dans WPF</span><span class="sxs-lookup"><span data-stu-id="a1746-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="a1746-125">Vue d'ensemble des objets Drawing</span><span class="sxs-lookup"><span data-stu-id="a1746-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="a1746-126">Utilisation d'objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="a1746-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="a1746-127">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="a1746-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="a1746-128">Vue d'ensemble des objets Freezable</span><span class="sxs-lookup"><span data-stu-id="a1746-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="a1746-129">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="a1746-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="a1746-130">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="a1746-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a1746-131">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="a1746-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="a1746-132">Typographie dans WPF</span><span class="sxs-lookup"><span data-stu-id="a1746-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="a1746-133">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="a1746-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a1746-134">Vue d'ensemble de la navigation</span><span class="sxs-lookup"><span data-stu-id="a1746-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="a1746-135">Conseils et astuces sur les animations</span><span class="sxs-lookup"><span data-stu-id="a1746-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="a1746-136">Procédure pas à pas : mise en cache des données d’application dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="a1746-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
