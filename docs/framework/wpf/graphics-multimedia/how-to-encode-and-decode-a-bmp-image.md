---
title: 'Procédure : Encoder et décoder une image BMP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
ms.openlocfilehash: 7d3520a1b1913fe68fedb0ea9d76cc138ed661c4
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331731"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a>Procédure : Encoder et décoder une image BMP
Les exemples suivants montrent comment décoder et encoder une image bitmap (BMP) à <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> l' <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> aide des objets et spécifiques.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment décoder une image BMP à l' <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> aide d' <xref:System.Uri>un à partir d’un.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment encoder <xref:System.Windows.Media.Imaging.BitmapSource> un en image BMP à l' <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>aide d’un.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la création d’images](imaging-overview.md)
