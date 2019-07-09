---
title: 'Procédure : Appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662813"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="d00a7-102">Procédure : Appliquer un dessin à un modèle 3D</span><span class="sxs-lookup"><span data-stu-id="d00a7-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="d00a7-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.DrawingBrush> comme le <xref:System.Windows.Media.Media3D.Material> appliqué à un modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="d00a7-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="d00a7-104">Le code suivant définit un <xref:System.Windows.Media.DrawingGroup> comme contenu d’un <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="d00a7-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="d00a7-105">Le <xref:System.Windows.Media.DrawingBrush> est défini comme le <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriété de la <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliqué à un plan 3D.</span><span class="sxs-lookup"><span data-stu-id="d00a7-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>  
  
 <span data-ttu-id="d00a7-106">**Remarque :** Il est souvent souhaitable de définir des valeurs telles que le dessin ci-dessous et les objets complexes en tant que ressources qui peuvent être réutilisées et simplifient votre code.</span><span class="sxs-lookup"><span data-stu-id="d00a7-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="d00a7-107">Consultez [XAML ressources](../advanced/xaml-resources.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="d00a7-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="d00a7-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d00a7-108">Example</span></span>  
 <span data-ttu-id="d00a7-109">Le code suivant montre l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="d00a7-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d00a7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d00a7-110">See also</span></span>

- [<span data-ttu-id="d00a7-111">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="d00a7-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="d00a7-112">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="d00a7-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d00a7-113">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="d00a7-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="d00a7-114">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="d00a7-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
