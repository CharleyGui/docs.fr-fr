---
title: 'Comment : Appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112178"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a><span data-ttu-id="41b75-102">Comment : Appliquer un dessin à un modèle 3D</span><span class="sxs-lookup"><span data-stu-id="41b75-102">How to: Apply a Drawing to a 3D Model</span></span>

<span data-ttu-id="41b75-103">Cet exemple montre comment <xref:System.Windows.Media.DrawingBrush> utiliser <xref:System.Windows.Media.Media3D.Material> un comme appliqué à un modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="41b75-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>

<span data-ttu-id="41b75-104">Le code suivant <xref:System.Windows.Media.DrawingGroup> définit un comme <xref:System.Windows.Media.DrawingBrush>le contenu d’un .</span><span class="sxs-lookup"><span data-stu-id="41b75-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="41b75-105">Le <xref:System.Windows.Media.DrawingBrush> est fixé <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> comme <xref:System.Windows.Media.Media3D.DiffuseMaterial> la propriété de l’appliqué à un avion 3D.</span><span class="sxs-lookup"><span data-stu-id="41b75-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="41b75-106">Il est souvent souhaitable de définir des objets et des valeurs complexes comme le dessin ci-dessous comme des ressources qui peuvent être réutilisées et simplifier votre code.</span><span class="sxs-lookup"><span data-stu-id="41b75-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="41b75-107">Voir [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="41b75-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="41b75-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="41b75-108">Example</span></span>

<span data-ttu-id="41b75-109">Le code suivant affiche l’échantillon entier.</span><span class="sxs-lookup"><span data-stu-id="41b75-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="41b75-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41b75-110">See also</span></span>

- [<span data-ttu-id="41b75-111">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="41b75-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="41b75-112">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="41b75-112">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="41b75-113">Vue d'ensemble des objets Drawing</span><span class="sxs-lookup"><span data-stu-id="41b75-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="41b75-114">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="41b75-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
