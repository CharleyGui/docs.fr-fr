---
title: 'Comment : Appliquer le matériel d’émissive à un objet 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112152"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a><span data-ttu-id="23dd4-102">Comment : Appliquer le matériel d’émissive à un objet 3D</span><span class="sxs-lookup"><span data-stu-id="23dd4-102">How to: Apply Emissive Material to a 3D Object</span></span>
<span data-ttu-id="23dd4-103">L’exemple suivant montre <xref:System.Windows.Media.Media3D.EmissiveMaterial> comment utiliser pour ajouter de la couleur à un matériau existant égal à la couleur du pinceau de l’EmissiveMaterial.</span><span class="sxs-lookup"><span data-stu-id="23dd4-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="23dd4-104">Le code <xref:System.Windows.Media.Media3D.DiffuseMaterial> ci-dessous affiche et <xref:System.Windows.Media.Media3D.EmissiveMaterial> appliqué en combinaison pour ajouter du bleu à l’apparence du DiffuseMaterial.</span><span class="sxs-lookup"><span data-stu-id="23dd4-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="23dd4-105">Dans le code de procédure :</span><span class="sxs-lookup"><span data-stu-id="23dd4-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="23dd4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="23dd4-106">Example</span></span>  
 <span data-ttu-id="23dd4-107">Le code suivant affiche l’échantillon entier dans XAML.</span><span class="sxs-lookup"><span data-stu-id="23dd4-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="23dd4-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="23dd4-108">Example</span></span>  
 <span data-ttu-id="23dd4-109">Voici l’échantillon entier du code de procédure.</span><span class="sxs-lookup"><span data-stu-id="23dd4-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="23dd4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23dd4-110">See also</span></span>

- [<span data-ttu-id="23dd4-111">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="23dd4-111">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="23dd4-112">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="23dd4-112">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="23dd4-113">Animer les propriétés matérielles dans une scène 3D</span><span class="sxs-lookup"><span data-stu-id="23dd4-113">Animate Material Properties in a 3D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="23dd4-114">Appliquer du matériel à l’avant et au dos d’un objet 3D</span><span class="sxs-lookup"><span data-stu-id="23dd4-114">Apply Material to the Front and Back of a 3D Object</span></span>](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
