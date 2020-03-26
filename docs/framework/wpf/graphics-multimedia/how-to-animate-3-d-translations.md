---
title: 'Comment : Animer les traductions 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112256"
---
# <a name="how-to-animate-3d-translations"></a><span data-ttu-id="07f87-102">Comment : Animer les traductions 3D</span><span class="sxs-lookup"><span data-stu-id="07f87-102">How to: Animate 3D Translations</span></span>
<span data-ttu-id="07f87-103">Ce sujet montre comment animer une transformation de traduction définie sur un modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="07f87-103">This topic demonstrates how to animate a translation transformation set on a 3D model.</span></span>  
  
 <span data-ttu-id="07f87-104">Le code ci-dessous <xref:System.Windows.Media.Media3D.TranslateTransform3D> montre l’application d’un objet à la <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriété d’un <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="07f87-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="07f87-105">La <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriété <xref:System.Windows.Media.Media3D.TranslateTransform3D> de cet objet est animée à l’aide du code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="07f87-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="07f87-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="07f87-106">Example</span></span>  
 <span data-ttu-id="07f87-107">Le code suivant affiche l’échantillon entier.</span><span class="sxs-lookup"><span data-stu-id="07f87-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="07f87-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07f87-108">See also</span></span>

- [<span data-ttu-id="07f87-109">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="07f87-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="07f87-110">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="07f87-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="07f87-111">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="07f87-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="07f87-112">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="07f87-112">Transforms Overview</span></span>](transforms-overview.md)
