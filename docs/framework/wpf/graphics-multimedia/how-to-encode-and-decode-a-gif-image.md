---
title: 'Procédure : Encoder et décoder une image GIF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
ms.openlocfilehash: ec509a03d95e5f72af0b1f362e253799b07edc1f
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671690"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="8b507-102">Procédure : Encoder et décoder une image GIF</span><span class="sxs-lookup"><span data-stu-id="8b507-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="8b507-103">Les exemples suivants montrent comment décoder et encoder une image gif (Graphics Interchange Format) <xref:System.Windows.Media.Imaging.GifBitmapDecoder> à <xref:System.Windows.Media.Imaging.GifBitmapEncoder> l’aide des objets et spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8b507-103">The following examples show how to decode and encode a Graphics Interchange Format (GIF) image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b507-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="8b507-104">Example</span></span>  
 <span data-ttu-id="8b507-105">Cet exemple montre comment décoder une image GIF à l' <xref:System.Windows.Media.Imaging.GifBitmapDecoder> aide d' <xref:System.IO.FileStream>un à partir d’un.</span><span class="sxs-lookup"><span data-stu-id="8b507-105">This example demonstrates how to decode a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="8b507-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="8b507-106">Example</span></span>  
 <span data-ttu-id="8b507-107">Cet exemple montre comment encoder <xref:System.Windows.Media.Imaging.BitmapSource> un en image GIF à l' <xref:System.Windows.Media.Imaging.GifBitmapEncoder>aide d’un.</span><span class="sxs-lookup"><span data-stu-id="8b507-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8b507-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b507-108">See also</span></span>

- [<span data-ttu-id="8b507-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="8b507-109">Imaging Overview</span></span>](imaging-overview.md)
