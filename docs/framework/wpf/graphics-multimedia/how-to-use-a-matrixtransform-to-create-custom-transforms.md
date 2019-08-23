---
title: 'Procédure : Utiliser la classe MatrixTransform pour créer des transformations personnalisées'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913915"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="4a22d-102">Procédure : Utiliser la classe MatrixTransform pour créer des transformations personnalisées</span><span class="sxs-lookup"><span data-stu-id="4a22d-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="4a22d-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.MatrixTransform> pour traduire (déplacer) la position, l’étirement et l’inclinaison d’un. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="4a22d-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a22d-104">Utilisez la <xref:System.Windows.Media.MatrixTransform> classe pour créer des transformations personnalisées qui ne sont pas <xref:System.Windows.Media.RotateTransform>fournies par <xref:System.Windows.Media.ScaleTransform>les classes <xref:System.Windows.Media.TranslateTransform> , <xref:System.Windows.Media.SkewTransform>, ou.</span><span class="sxs-lookup"><span data-stu-id="4a22d-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a22d-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="4a22d-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="4a22d-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a22d-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="4a22d-107">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="4a22d-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="4a22d-108">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="4a22d-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="4a22d-109">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="4a22d-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
