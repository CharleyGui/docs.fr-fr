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
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Procédure : Encoder un visuel dans un fichier image
Cet exemple montre comment encoder <xref:System.Windows.Media.Visual> un objet dans un fichier image à <xref:System.Windows.Media.Imaging.RenderTargetBitmap> l’aide <xref:System.Windows.Media.Imaging.PngBitmapEncoder>d’un et d’un.  
  
## <a name="example"></a>Exemple  
 La <xref:System.Windows.Media.DrawingVisual> est créée à l' <xref:System.Windows.Media.Imaging.BitmapImage> aide <xref:System.Windows.Media.FormattedText> d’un et qui est <xref:System.Windows.Media.Imaging.RenderTargetBitmap>rendu à un. La bitmap rendue est ensuite utilisée pour créer un <xref:System.Windows.Media.Imaging.BitmapFrame> qui est ajouté <xref:System.Windows.Media.Imaging.PngBitmapEncoder> au pour créer un nouveau fichier png (Portable Network Graphics).  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 A été utilisé dans cet exemple, mais l’un des <xref:System.Windows.Media.Imaging.BitmapEncoder> objets dérivés a pu être utilisé pour créer le fichier image. <xref:System.Windows.Media.Imaging.PngBitmapEncoder>  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.DrawingContext>
- [Vue d’ensemble de la création d’images](imaging-overview.md)
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
- [Utilisation d’objets DrawingVisual](using-drawingvisual-objects.md)
