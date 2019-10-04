---
title: 'Procédure : Encoder et décoder une image TIFF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
ms.openlocfilehash: 173a30e785b16a3617b82b771c463083356d6e6e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835295"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="8ee2d-102">Procédure : Encoder et décoder une image TIFF</span><span class="sxs-lookup"><span data-stu-id="8ee2d-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="8ee2d-103">Les exemples suivants montrent comment décoder et encoder une image TIFF (Tagged Image File Format) à l’aide des objets <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> et <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8ee2d-103">The following examples show how to decode and encode a Tagged Image File Format (TIFF) image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee2d-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ee2d-104">Example</span></span>  
 <span data-ttu-id="8ee2d-105">Cet exemple montre comment décoder une image TIFF à l’aide d’un <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> à partir d’un <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="8ee2d-105">This example demonstrates how to decode a TIFF image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="8ee2d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ee2d-106">Example</span></span>  
 <span data-ttu-id="8ee2d-107">Cet exemple montre comment encoder un <xref:System.Windows.Media.Imaging.BitmapSource> dans une image TIFF à l’aide d’un <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="8ee2d-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a TIFF image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8ee2d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ee2d-108">See also</span></span>

- [<span data-ttu-id="8ee2d-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="8ee2d-109">Imaging Overview</span></span>](imaging-overview.md)
