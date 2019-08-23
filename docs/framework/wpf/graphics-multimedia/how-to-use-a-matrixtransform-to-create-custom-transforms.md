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
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Procédure : Utiliser la classe MatrixTransform pour créer des transformations personnalisées
Cet exemple montre comment utiliser un <xref:System.Windows.Media.MatrixTransform> pour traduire (déplacer) la position, l’étirement et l’inclinaison d’un. <xref:System.Windows.Controls.Button>  
  
> [!NOTE]
> Utilisez la <xref:System.Windows.Media.MatrixTransform> classe pour créer des transformations personnalisées qui ne sont pas <xref:System.Windows.Media.RotateTransform>fournies par <xref:System.Windows.Media.ScaleTransform>les classes <xref:System.Windows.Media.TranslateTransform> , <xref:System.Windows.Media.SkewTransform>, ou.  
  
## <a name="example"></a>Exemples  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Vue d’ensemble des transformations](transforms-overview.md)
- [Rubriques de guide pratique](transformations-how-to-topics.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
