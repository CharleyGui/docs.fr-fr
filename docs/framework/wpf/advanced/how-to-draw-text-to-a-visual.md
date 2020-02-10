---
title: 'Comment : ajouter du texte à un Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094551"
---
# <a name="how-to-draw-text-to-a-visual"></a>Comment : ajouter du texte à un Visual
L’exemple suivant montre comment dessiner du texte sur un <xref:System.Windows.Media.DrawingVisual> à l’aide d’un objet <xref:System.Windows.Media.DrawingContext>. Un contexte de dessin est retourné en appelant la méthode <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> d’un objet <xref:System.Windows.Media.DrawingVisual>. Vous pouvez dessiner des graphiques et du texte dans un contexte de dessin.  
  
 Pour dessiner du texte dans le contexte de dessin, utilisez la méthode <xref:System.Windows.Media.DrawingContext.DrawText%2A> d’un objet <xref:System.Windows.Media.DrawingContext>. Lorsque vous avez terminé de dessiner du contenu dans le contexte de dessin, appelez la méthode <xref:System.Windows.Media.DrawingContext.Close%2A> pour fermer le contexte de dessin et conserver le contenu.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) (Test de positionnement à l’aide d’exemples de DrawingVisuals).
