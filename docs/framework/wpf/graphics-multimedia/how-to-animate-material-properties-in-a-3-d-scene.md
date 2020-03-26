---
title: 'Comment : Animer les propriétés matérielles dans une scène 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112191"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a><span data-ttu-id="d3ce1-102">Comment : Animer les propriétés matérielles dans une scène 3D</span><span class="sxs-lookup"><span data-stu-id="d3ce1-102">How to: Animate Material Properties in a 3D Scene</span></span>
<span data-ttu-id="d3ce1-103">Cet exemple montre comment animer <xref:System.Windows.Media.Brush.Opacity%2A> la <xref:System.Windows.Media.Media3D.Material> propriété de l’appliqué à un modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="d3ce1-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>  
  
 <span data-ttu-id="d3ce1-104">L’exemple de code <xref:System.Windows.Media.LinearGradientBrush> suivant <xref:System.Windows.Media.Media3D.Material> définit l’utilisé comme l’appliqué à l’objet 3D.</span><span class="sxs-lookup"><span data-stu-id="d3ce1-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="d3ce1-105">La <xref:System.Windows.Media.Brush.Opacity%2A> propriété <xref:System.Windows.Media.LinearGradientBrush> de ceci est animée utilisant l’exemple de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d3ce1-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="d3ce1-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3ce1-106">Example</span></span>  
 <span data-ttu-id="d3ce1-107">Le code suivant affiche l’échantillon entier.</span><span class="sxs-lookup"><span data-stu-id="d3ce1-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d3ce1-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3ce1-108">See also</span></span>

- [<span data-ttu-id="d3ce1-109">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="d3ce1-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d3ce1-110">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="d3ce1-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
