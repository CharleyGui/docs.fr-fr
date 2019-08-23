---
title: 'Procédure : Énumérer le contenu de dessin d’un visuel'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930067"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Procédure : Énumérer le contenu de dessin d’un visuel
L' <xref:System.Windows.Media.Drawing> objet fournit un modèle objet pour énumérer le contenu d’un <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> méthode pour récupérer la <xref:System.Windows.Media.DrawingGroup> valeur d’un <xref:System.Windows.Media.Visual> et l’énumérer.  
  
> [!NOTE]
> Lorsque vous énumérez le contenu du visuel, vous récupérez <xref:System.Windows.Media.Drawing> des objets, et non la représentation sous-jacente des données de rendu sous la forme d’une liste d’instructions de graphismes vectoriels. Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
