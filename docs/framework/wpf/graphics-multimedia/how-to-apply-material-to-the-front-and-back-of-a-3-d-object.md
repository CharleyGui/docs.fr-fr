---
title: 'Comment : Appliquer du matériel à l’avant et au dos d’un objet 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112139"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a><span data-ttu-id="ed676-102">Comment : Appliquer du matériel à l’avant et au dos d’un objet 3D</span><span class="sxs-lookup"><span data-stu-id="ed676-102">How to: Apply Material to the Front and Back of a 3D Object</span></span>
<span data-ttu-id="ed676-103">L’exemple suivant montre <xref:System.Windows.Media.Media3D.Material> comment appliquer un à l’avant et à l’arrière d’un objet 3D et animer l’objet pour montrer les deux côtés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed676-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="ed676-104">La <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriété <xref:System.Windows.Media.Media3D.GeometryModel3D> d’un est <xref:System.Windows.Media.Brush> utilisée pour appliquer un rouge <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> sur <xref:System.Windows.Media.Media3D.GeometryModel3D> le côté avant <xref:System.Windows.Media.Brush> de l’objet et la propriété de l’est utilisé pour appliquer un bleu sur le côté arrière de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed676-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="ed676-105">Le code ci-dessous affiche l’application des matériaux à l’objet :</span><span class="sxs-lookup"><span data-stu-id="ed676-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="ed676-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed676-106">Example</span></span>  
 <span data-ttu-id="ed676-107">Le code suivant affiche l’échantillon entier.</span><span class="sxs-lookup"><span data-stu-id="ed676-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ed676-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed676-108">See also</span></span>

- [<span data-ttu-id="ed676-109">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="ed676-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="ed676-110">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="ed676-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="ed676-111">Animer les propriétés matérielles dans une scène 3D</span><span class="sxs-lookup"><span data-stu-id="ed676-111">Animate Material Properties in a 3D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="ed676-112">Appliquer le matériel Emissive sur un objet 3D</span><span class="sxs-lookup"><span data-stu-id="ed676-112">Apply Emissive Material to a 3D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
