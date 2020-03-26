---
title: 'Comment : Transformer l’échelle d’un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111983"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a><span data-ttu-id="20c26-102">Comment : Transformer l’échelle d’un modèle 3D</span><span class="sxs-lookup"><span data-stu-id="20c26-102">How to: Transform the Scale of a 3D Model</span></span>
<span data-ttu-id="20c26-103">Cet exemple montre comment mettre à l’échelle un objet 3D.</span><span class="sxs-lookup"><span data-stu-id="20c26-103">This example shows how to scale a 3D object.</span></span> <span data-ttu-id="20c26-104">Pour mettre à l’échelle <xref:System.Windows.Media.Media3D.ScaleTransform3D>un objet 3D, utilisez un .</span><span class="sxs-lookup"><span data-stu-id="20c26-104">To scale a 3D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="20c26-105">Les <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> , et les propriétés resize l’élément par le facteur que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="20c26-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="20c26-106">Par exemple, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> une valeur de 1,5 étend un objet à 150 pour cent de sa largeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="20c26-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="20c26-107">Une <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valeur de 0,5 réduit la hauteur d’un objet de 50 pour cent.</span><span class="sxs-lookup"><span data-stu-id="20c26-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="20c26-108">Le code ci-dessous montre l’utilisation d’un <xref:System.Windows.Media.Media3D.ScaleTransform3D> comme transformation pour un <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="20c26-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="20c26-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="20c26-109">Example</span></span>  
 <span data-ttu-id="20c26-110">Le code suivant affiche l’échantillon entier.</span><span class="sxs-lookup"><span data-stu-id="20c26-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="20c26-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20c26-111">See also</span></span>

- [<span data-ttu-id="20c26-112">Animation de traductions 3D</span><span class="sxs-lookup"><span data-stu-id="20c26-112">Animate 3D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="20c26-113">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="20c26-113">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="20c26-114">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="20c26-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
