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
# <a name="how-to-encode-and-decode-a-gif-image"></a>Procédure : Encoder et décoder une image GIF
Les exemples suivants montrent comment décoder et encoder une image gif (Graphics Interchange Format) <xref:System.Windows.Media.Imaging.GifBitmapDecoder> à <xref:System.Windows.Media.Imaging.GifBitmapEncoder> l’aide des objets et spécifiques.  
  
## <a name="example"></a>Exemples  
 Cet exemple montre comment décoder une image GIF à l' <xref:System.Windows.Media.Imaging.GifBitmapDecoder> aide d' <xref:System.IO.FileStream>un à partir d’un.  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Exemples  
 Cet exemple montre comment encoder <xref:System.Windows.Media.Imaging.BitmapSource> un en image GIF à l' <xref:System.Windows.Media.Imaging.GifBitmapEncoder>aide d’un.  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la création d’images](imaging-overview.md)
