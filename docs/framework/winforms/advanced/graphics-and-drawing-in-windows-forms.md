---
title: Graphiques et dessin
description: Découvrez les objets graphiques, stylet, pinceau et couleur, et comment effectuer des tâches telles que dessiner des formes, dessiner du texte ou afficher des images dans Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618400"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="5ee02-103">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ee02-103">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="5ee02-104">L’common language runtime utilise une implémentation avancée de l’Graphics Device Interface Windows (GDI) appelée GDI+.</span><span class="sxs-lookup"><span data-stu-id="5ee02-104">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="5ee02-105">Avec GDI+, vous pouvez créer des graphiques, dessiner du texte et manipuler des images graphiques en tant qu’objets.</span><span class="sxs-lookup"><span data-stu-id="5ee02-105">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="5ee02-106">GDI+ est conçu pour offrir des performances et une facilité d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5ee02-106">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="5ee02-107">Vous pouvez utiliser GDI+ pour restituer des images graphiques sur des Windows Forms et des contrôles.</span><span class="sxs-lookup"><span data-stu-id="5ee02-107">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="5ee02-108">Bien que vous ne puissiez pas utiliser GDI+ directement sur Web Forms, vous pouvez afficher des images graphiques via le contrôle serveur Web image.</span><span class="sxs-lookup"><span data-stu-id="5ee02-108">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="5ee02-109">Dans cette section, vous trouverez des rubriques qui présentent les notions de base de la programmation GDI+.</span><span class="sxs-lookup"><span data-stu-id="5ee02-109">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="5ee02-110">Bien qu’il ne s’agisse pas d’une référence exhaustive, cette section comprend des informations sur les objets <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, et <xref:System.Drawing.Color> et explique comment effectuer des tâches telles que dessiner des formes et du texte ou afficher des images.</span><span class="sxs-lookup"><span data-stu-id="5ee02-110">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="5ee02-111">Pour plus d’informations, consultez [référence GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="5ee02-111">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="5ee02-112">Si vous voulez vous lancer et commencer immédiatement, consultez [Bien démarrer avec la programmation graphique](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="5ee02-112">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="5ee02-113">Elle comporte des rubriques sur l’utilisation de code pour dessiner des lignes, des formes, du texte et d’autres éléments sur les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5ee02-113">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ee02-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ee02-114">In This Section</span></span>  
 [<span data-ttu-id="5ee02-115">Vue d’ensemble des graphismes</span><span class="sxs-lookup"><span data-stu-id="5ee02-115">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="5ee02-116">Fournit une introduction aux classes managées graphiques.</span><span class="sxs-lookup"><span data-stu-id="5ee02-116">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="5ee02-117">À propos du code managé GDI+</span><span class="sxs-lookup"><span data-stu-id="5ee02-117">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="5ee02-118">Fournit des informations sur les classes GDI+ managées.</span><span class="sxs-lookup"><span data-stu-id="5ee02-118">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="5ee02-119">Utilisation de classes graphiques managées</span><span class="sxs-lookup"><span data-stu-id="5ee02-119">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="5ee02-120">Montre comment effectuer diverses tâches à l’aide des classes managées GDI+.</span><span class="sxs-lookup"><span data-stu-id="5ee02-120">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ee02-121">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="5ee02-121">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="5ee02-122">Donne accès aux fonctionnalités graphiques de base de GDI+.</span><span class="sxs-lookup"><span data-stu-id="5ee02-122">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="5ee02-123">Fournit des fonctionnalités graphiques vectorielles et à deux dimensions avancées.</span><span class="sxs-lookup"><span data-stu-id="5ee02-123">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="5ee02-124">Fournit des fonctionnalités d’imagerie GDI+ avancées.</span><span class="sxs-lookup"><span data-stu-id="5ee02-124">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="5ee02-125">Fournit des fonctionnalités de typographie GDI+ avancées.</span><span class="sxs-lookup"><span data-stu-id="5ee02-125">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="5ee02-126">Les classes dans cet espace de noms peuvent être utilisées pour créer et utiliser des collections de polices.</span><span class="sxs-lookup"><span data-stu-id="5ee02-126">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="5ee02-127">Fournit des fonctionnalités d'impression.</span><span class="sxs-lookup"><span data-stu-id="5ee02-127">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ee02-128">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="5ee02-128">Related Sections</span></span>  
 [<span data-ttu-id="5ee02-129">Peinture et rendu personnalisés des contrôles</span><span class="sxs-lookup"><span data-stu-id="5ee02-129">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="5ee02-130">Explique comment fournir du code pour des contrôles de dessin.</span><span class="sxs-lookup"><span data-stu-id="5ee02-130">Details how to provide code for painting controls.</span></span>
