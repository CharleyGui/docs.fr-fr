---
title: 'Procédure : Appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855884"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="adef4-102">Procédure : Appliquer un dessin à un modèle 3D</span><span class="sxs-lookup"><span data-stu-id="adef4-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="adef4-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> comme appliqué à un modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="adef4-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="adef4-104">Le code suivant définit un <xref:System.Windows.Media.DrawingGroup> comme le contenu d’un <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="adef4-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="adef4-105">Le <xref:System.Windows.Media.DrawingBrush> est défini <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> en tant que propriété du <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliqué à un plan 3D.</span><span class="sxs-lookup"><span data-stu-id="adef4-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="adef4-106">Il est souvent souhaitable de définir des objets et des valeurs complexes comme le dessin ci-dessous en tant que ressources qui peuvent être réutilisées et simplifier votre code.</span><span class="sxs-lookup"><span data-stu-id="adef4-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="adef4-107">Pour plus d’informations, consultez [ressources XAML](../advanced/xaml-resources.md) .</span><span class="sxs-lookup"><span data-stu-id="adef4-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="adef4-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="adef4-108">Example</span></span>

<span data-ttu-id="adef4-109">Le code suivant illustre l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="adef4-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="adef4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adef4-110">See also</span></span>

- [<span data-ttu-id="adef4-111">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="adef4-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="adef4-112">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="adef4-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="adef4-113">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="adef4-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="adef4-114">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="adef4-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
