---
title: 'Comment : appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459370"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="06d2b-102">Comment : appliquer un dessin à un modèle 3D</span><span class="sxs-lookup"><span data-stu-id="06d2b-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="06d2b-103">Cet exemple montre comment utiliser une <xref:System.Windows.Media.DrawingBrush> comme <xref:System.Windows.Media.Media3D.Material> appliquée à un modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="06d2b-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="06d2b-104">Le code suivant définit une <xref:System.Windows.Media.DrawingGroup> comme contenu d’un <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="06d2b-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="06d2b-105">La <xref:System.Windows.Media.DrawingBrush> est définie comme <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriété de la <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliquée à un plan 3D.</span><span class="sxs-lookup"><span data-stu-id="06d2b-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="06d2b-106">Il est souvent souhaitable de définir des objets et des valeurs complexes comme le dessin ci-dessous en tant que ressources qui peuvent être réutilisées et simplifier votre code.</span><span class="sxs-lookup"><span data-stu-id="06d2b-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="06d2b-107">Pour plus d’informations, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .</span><span class="sxs-lookup"><span data-stu-id="06d2b-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="06d2b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="06d2b-108">Example</span></span>

<span data-ttu-id="06d2b-109">Le code suivant illustre l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="06d2b-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="06d2b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06d2b-110">See also</span></span>

- [<span data-ttu-id="06d2b-111">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="06d2b-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="06d2b-112">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="06d2b-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="06d2b-113">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="06d2b-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="06d2b-114">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="06d2b-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
