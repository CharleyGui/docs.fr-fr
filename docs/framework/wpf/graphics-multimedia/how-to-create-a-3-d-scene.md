---
title: 'Comment : Créer une scène 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112100"
---
# <a name="how-to-create-a-3d-scene"></a><span data-ttu-id="ee72f-102">Comment : Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="ee72f-102">How to: Create a 3D Scene</span></span>
<span data-ttu-id="ee72f-103">Cet exemple montre comment créer un objet 3D qui ressemble à une feuille de papier plate qui a été tourné.</span><span class="sxs-lookup"><span data-stu-id="ee72f-103">This example shows how to create a 3D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="ee72f-104">Un <xref:System.Windows.Controls.Viewport3D> avec les composants suivants sont utilisés pour créer cette scène 3D simple:</span><span class="sxs-lookup"><span data-stu-id="ee72f-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3D scene:</span></span>  
  
- <span data-ttu-id="ee72f-105">Un appareil photo <xref:System.Windows.Media.Media3D.PerspectiveCamera>est créé à l’aide d’un .</span><span class="sxs-lookup"><span data-stu-id="ee72f-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="ee72f-106">La caméra précise quelle partie de la scène 3D est visible.</span><span class="sxs-lookup"><span data-stu-id="ee72f-106">The camera specifies what part of the 3D scene is viewable.</span></span>  
  
- <span data-ttu-id="ee72f-107">Un maillage est créé pour spécifier la forme de <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> l’objet 3D (feuille de papier) en utilisant la propriété de <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="ee72f-107">A mesh is created to specify the shape of 3D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="ee72f-108">Un matériau est spécifié pour être affiché sur la surface de l’objet (gradient linéaire dans cet échantillon) en utilisant la <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriété de <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="ee72f-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="ee72f-109">Une lumière est créée pour <xref:System.Windows.Media.Media3D.DirectionalLight>briller sur l’objet à l’aide de .</span><span class="sxs-lookup"><span data-stu-id="ee72f-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee72f-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee72f-110">Example</span></span>  
 <span data-ttu-id="ee72f-111">Le code ci-dessous montre comment créer une scène 3D dans XAML.</span><span class="sxs-lookup"><span data-stu-id="ee72f-111">The code below shows how to create a 3D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="ee72f-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee72f-112">Example</span></span>  
 <span data-ttu-id="ee72f-113">Le code ci-dessous montre comment créer la même scène 3D dans le code de procédure.</span><span class="sxs-lookup"><span data-stu-id="ee72f-113">The code below shows how to create the same 3D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ee72f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee72f-114">See also</span></span>

- [<span data-ttu-id="ee72f-115">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="ee72f-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
