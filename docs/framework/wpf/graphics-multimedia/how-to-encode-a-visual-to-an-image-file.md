---
title: 'Procédure : Encoder un visuel dans un fichier image'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545294"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="2da97-102">Procédure : Encoder un visuel dans un fichier image</span><span class="sxs-lookup"><span data-stu-id="2da97-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="2da97-103">Cet exemple montre comment encoder <xref:System.Windows.Media.Visual> un objet dans un fichier image à <xref:System.Windows.Media.Imaging.RenderTargetBitmap> l’aide <xref:System.Windows.Media.Imaging.PngBitmapEncoder>d’un et d’un.</span><span class="sxs-lookup"><span data-stu-id="2da97-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2da97-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2da97-104">Example</span></span>  
 <span data-ttu-id="2da97-105">La <xref:System.Windows.Media.DrawingVisual> est créée à l' <xref:System.Windows.Media.Imaging.BitmapImage> aide <xref:System.Windows.Media.FormattedText> d’un et qui est <xref:System.Windows.Media.Imaging.RenderTargetBitmap>rendu à un.</span><span class="sxs-lookup"><span data-stu-id="2da97-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="2da97-106">La bitmap rendue est ensuite utilisée pour créer un <xref:System.Windows.Media.Imaging.BitmapFrame> qui est ajouté <xref:System.Windows.Media.Imaging.PngBitmapEncoder> au pour créer un nouveau fichier png (Portable Network Graphics).</span><span class="sxs-lookup"><span data-stu-id="2da97-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new Portable Network Graphics (PNG) file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="2da97-107">A été utilisé dans cet exemple, mais l’un des <xref:System.Windows.Media.Imaging.BitmapEncoder> objets dérivés a pu être utilisé pour créer le fichier image. <xref:System.Windows.Media.Imaging.PngBitmapEncoder></span><span class="sxs-lookup"><span data-stu-id="2da97-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da97-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2da97-108">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="2da97-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="2da97-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="2da97-110">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="2da97-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="2da97-111">Utilisation d’objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="2da97-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
